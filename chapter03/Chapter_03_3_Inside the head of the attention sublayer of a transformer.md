# Bu Bölümün Amacı
Bu bölüm, mimarinin matematiğini anlamak ile modelin kelime parçaları (kelimeler veya kelimelerin parçaları) üreterek kelime dizilerine nasıl dönüştürdüğü arasındaki boşluğu doldurmayı amaçlamaktadır. Bu bölümde, görüntülenen skorlar, softmax'tan sonra dikkat başlıklarının çıktısıdır, ancak olasılıklar değer vektörlerinin (V) ağırlıklı toplamını oluşturmadan önce. 9. Bölüm'de, "Siyah Kutuyu Yorumlanabilir Araçlarla Parçalama" başlıklı bölümde, sayıları kelimelere nasıl dönüştürdüğünü göstermek için bu bölümde kullanılan BertViz_Interactive.ipynb dahil olmak üzere kod seviyesine ineceğiz. Herhangi bir kodu çalıştırmaya gerek yoktur, ancak matematiksel olasılıklardan kelimelere nasıl geçildiğini kavramak gerekir. Buradaki ana odak, anlamsız sayılardan organize dile yapılan kuantum sıçramasını anlamaktır. Bir transformer modelinin daha fazla dil dizisini öğrenmesiyle anlamın nasıl ortaya çıktığını göreceğiz.

## Transformer Modelinin İç Çalışmaları
Şimdi, transformer'ın iç işleyişini görmek için aşağıdaki cümleyi inceleyelim: "Transformers possess surprising emerging features." Bu dizi, bir transformer modelinin alt katmanlarından geçer ve 2. Bölüm'de açıklanan dikkat başlıklarına ulaşır. Burada, dikkat başlıklarının matematiksel hesaplamalarına girmeksizin elde edilen çıktılara bakacağız. Koda da bakmayacağız; bu, 9. Bölüm'e kadar bekleyebilir. Orijinal Transformer'ın nasıl tasarlandığını ve nasıl yıkıcı çıktılara yol açtığını anlamaya odaklanacağız, tıpkı orijinal tasarımcıların yaptığı gibi. Sayılar ve kelimeler arasındaki boşluğu doldurduğumuzda, kitap boyunca not defterlerini çalıştırmak için gereken anlayışa sahip olacağız.

### Dikkat Başlıklarının Çıktılarına Odaklanma
İlk olarak, katman 1 ve dikkat başlığı 1'e bakalım: 
```python
selected_layer = 1
selected_head = 1
```
Transformer analiz aracı, başlığın ne düşündüğünü görüntüler:
#### Şekil 3.1: Katman 1'de dikkat başlığı 1 için kelime çiftlerinin olasılık tablosu
Şekil 3.1'in her satırı cümledeki bir kelimeyi içerir. Her sütun da cümledeki her kelimeyi içerir. Kesişim, iki kelimenin ilgili olma olasılığını temsil eder. Görebileceğiniz gibi, öğrenme veya eğitim dediğimiz şey, bir kelimenin belirli bir bağlamda (dizi) başka bir kelimeyle ilgili olma olasılığıdır.

Bu deney için, "transformers" ve "possess" kelimeleri arasındaki ilişkiye odaklanacağız:
- "transformers": Dikkat başlığı "aklı" tam kapasite çalışıyor. Her kelimenin diğer kelimelerle olan ilişkisini inceliyor. "transformers-transformers" çifti için yüksek bir skor buluyor (0.79). Bu skor çok ilginç değil çünkü bir kelime açıkça kendisiyle ilgili.
- "possess": "transformers" ve "possess" arasındaki skor (0.038). Bu da henüz çok ilginç değil.

Şimdi, katman 1'de başka bir başlığa bakalım:
```python
selected_layer = 1
selected_head = 6
```
Çıktılar aşağıdaki gibidir:
#### Şekil 3.2: Katman 1'de dikkat başlığı 6 için kelime çiftlerinin olasılık tablosu
Başlık 6 farklı ilişkiler kurar.
- "transformers": "transformers-transformers" çifti için yüksek bir skor bulur, ancak başlık 1'den daha düşük (0.70).
- "possess": "transformers" ve "possess" arasındaki skor, başlık 1'den daha yüksek (0.12).

Şimdi, katman 6, başlık 1'e geçelim:
```python
selected_layer = 6
selected_head = 1
```
Çıktılar aşağıdaki gibidir:
#### Şekil 3.3: Katman 6'da dikkat başlığı 1 için kelime çiftlerinin olasılık tablosu
Başlık 1 "ışığı görmeye" başlıyor:
- "transformers": "transformers-transformers" çifti için katman 1'den daha düşük bir skor bulur (0.03). Kendisinden başka kelimelerle ilişkilendirmesi gerektiğini öğreniyor.
- "possess": "transformers" ve "possess" arasındaki skor, katman 1'den daha yüksek (0.188). "surprising" kelimesinin yüksek skoru 0.53'tür.

Son olarak, katman 6, başlık 6'ya bakalım:
```python
selected_layer = 6
selected_head = 6
```
Çıktı aşağıdaki gibidir:
#### Şekil 3.4: Katman 6'da dikkat başlığı 6 için kelime çiftlerinin olasılık tablosu
Başlık 6 kendi görüşlerine sahip:
- "transformers": "transformers-transformers" çifti için başlık 1'den daha düşük bir skor bulur (0.098).
- "possess": "transformers" ve "possess" arasındaki skor, başlık 1'den daha yüksek (0.20). "surprising" kelimesinin yüksek skoru (0.004), "possess"ten daha düşük ve başlık 1'den daha düşük.

Eğitim henüz bitmedi, ancak bazı öngörüler edinebiliriz: Katman 6, başlık 6'da, model giderek "possess" kelimesini seçmesi gerektiğini bulur. Bir isim + fiil iyi bir seçimdir. Eğitim henüz bitmedi, ancak iyi bir başlangıçtır.

Eğer eğitim maskeli bir kelime üzerinde olsaydı ve transformer modelinin bu cümlede eksik kelimeyi bulması gerekseydi: "Transformers _______ surprising emerging features." Model, ortaya çıkan bir örüntü buldu ve "possess" fiilini seçmeyi öğrendi. Model, birçok makine öğrenimi algoritması gibi ortaya çıkandır.

Eğer katman 6 ve başlık 6'ya "transformer" kelimesi için bakarsak:
#### Şekil 3.5: Katman 6'da dikkat başlığı 6 için "transformers" kelimesinin olasılık tablosu
Bunları sıraladığımızda, "transformers" kelimesini incelediğimiz için "transformers" kelimesini atlarsak, "transformers possess emerging features (surprising)" olduğunu görürüz. Bu iyi bir ilerlemedir çünkü eğitim sürecinin tam ortasındayız. Eğer amaç "possess" kelimesini bulmak olsaydı, çok daha fazla bilginin ortaya çıktığını söyleyebilirdik. Model milyarlarca parametre ile milyonlarca ilişki öğrenirken hayal edin!

Artık bir transformer'ın, kelimeleri veya kelime parçalarını temsil eden sayılardan anlaşılır dizilere nasıl gittiğini görebiliriz. ChatGPT ile ortaya çıkmayı eylem halinde görelim.

---

