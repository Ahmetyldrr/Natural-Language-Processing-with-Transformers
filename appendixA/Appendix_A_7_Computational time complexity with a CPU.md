# CPU Nedir?
Bir CPU, genel amaçlı bir yazılım işlemcisidir. Matris çarpımlarına özel olarak tasarlanmamıştır. Karmaşık işlemleri gerçekleştirebilir, ancak yalnızca belirli bir verimlilik derecesine kadar. Notebook'un ilk hücresini çalıştırmadan önce, Çalışma Zamanı menüsüne giderek, Çalışma zamanı türünü değiştir'i seçerek ve Donanım hızlandırıcı parametresinin Yok olarak ayarlandığından ve Çalışma zamanı şekli (RAM) Standart olarak ayarlandığından emin olarak bir CPU kullandığımızı doğrulamalıyız: 

Şekil A.2: Çalışma zamanı türünü seçme

Bu durumda, bir donanım hızlandırıcı, belirli hesaplama görevlerini (örneğin matris çarpımı) genel amaçlı bir CPU'dan daha verimli bir şekilde gerçekleştiren bir GPU veya TPU'dur, ki bu bir donanım hızlandırıcı değildir. Bu, Donanım hızlandırıcı'nın Yok olarak ayarlanmasını açıklar. 

Notebook, az önce incelediğimiz zaman karmaşıklıkları içeren bir şekil ile başlar: 

Şekil A.3: Attention is All You Need, Vaswani ve ark. (2017), sayfa 6

Notebook'un amacı, kendi kendine dikkat ve tekrarlayan katmanların gerçek algoritmalarını değil, katman başına karmaşıklığı temsil etmektir. Kendi kendine dikkat hesaplama zamanı karmaşıklığı, matris çarpımları ile çalışacaktır. Tekrarlayan hesaplama zamanı, sıralı yaklaşımını simüle eden bir döngü kullanacaktır. 

Tekrarlayan bir model, değerleri hesaplamak için matrisleri kullanır; ancak, genel hesaplama karmaşıklığı n ve d'nin bir sırasıdır. Hesaplamaların, kendi kendine dikkat katmanları ve tekrarlayan katmanların içindeki gerçek algoritmaları yansıtmadığını belirtmek önemlidir. Ayrıca, donanım, veri, hiperparametreler, eğitim zamanı ve diğer parametreler gibi birçok faktör performansı etkileyecektir. Bu notebook'un amacı, genel hesaplama zamanı karmaşıklığını göstermektir. Bu durumda, simülasyonlar yeterlidir.

İlk olarak, değerlendirmelerin çerçevesini tanımlarız: 
```python
# Katman başına karmaşıklığın hesaplama zamanları
# Kendi kendine dikkat ve tekrarlayan katmanlar arasındaki hesaplama zamanını karşılaştırma:
# kendi kendine dikkat = O(n^2 * d)
# ve
# tekrarlayan = O(n * d^2)
```
Daha sonra numpy ve time'ı içe aktarırız: 
```python
import numpy as np
import time
```
Dizi uzunluğunu (bir dizideki kelime sayısı) ve boyutları (kelimenin özelliklerini temsil eden sayısal vektör) tanımlarız: 
```python
# dizi uzunluğunu ve temsil boyutluluğunu tanımla
n = 512
d = 512
```
n = d olduğunu fark edeceksiniz, bu da O(n^2 * d) = O(n * d^2) = 512*512*512 = 134,217,728 işlem anlamına gelir. Bu durumda, hem dikkat hem de tekrarlayan katmanlar, hesaplama karmaşıklığı zamanı açısından aynı sayıda işlem gerçekleştirmek zorundadır.

Giriş dizisini rastgele değerlerle boyutlar (d) için tanımlarız: 
```python
# girişleri tanımla
input_seq = np.random.rand(n, d)
```
İlk olarak, başlangıç zamanı ile bir matris çarpımı ile kendi kendine dikkat katmanının zaman karmaşıklığını simüle edeceğiz: 
```python
# kendi kendine dikkat katmanının simülasyonu O(n^2*d)
start_time = time.time()
for i in range(n):
    for j in range(n):
        _ = np.dot(input_seq[i], input_seq[j])
```
Matris çarpımı tamamlandığında, geçen süreyi hesaplarız ve yazdırırız: 
```python
at = time.time() - start_time
print(f"Kendi kendine dikkat hesaplama zamanı: {time.time() - start_time} saniye")
```
Zaman görüntülenir: 
Kendi kendine dikkat hesaplama zamanı: 0.7938594818115234 saniye

Şimdi, başlangıç ve bitiş zamanı ile bir matris çarpımı olmadan tekrarlayan katman fonksiyonunun zaman karmaşıklığını simüle edeceğiz: 
```python
# tekrarlayan katman simülasyonu O(n*d^2)
start_time = time.time()
hidden_state = np.zeros(d)
for i in range(n):
    for j in range(d):
        for k in range(d):
            hidden_state[j] += input_seq[i, j] * hidden_state[k]
rt = time.time() - start_time
print(f"Tekrarlayan katman hesaplama zamanı: {time.time() - start_time} saniye")
```
Çıktı, geçen süreyi gösterir: 
Tekrarlayan katman hesaplama zamanı: 109.65185356140137 saniye

Şimdi, dikkat katmanının hesaplama zamanı karmaşıklığı ve tekrarlayan katman hesaplama zamanı karmaşıklığının yüzdesini hesaplarız. Performans yüzdelerini ölçebiliriz. Bu yaklaşım, dikkat katmanlarının gücünü genel olarak gösterir. 

Daha sonra sonucu görüntüleriz: 
```python
# Toplamı hesapla
total = at + rt
# at'nin yüzdesini hesapla
percentage_at = round((at / total) * 100, 2)
# Sonucu yazdır
print(f"Dikkat hesaplama zamanı yüzdesi, 'dikkat' ve 'tekrarlayan' toplamında {percentage_at}%")
```
Çıktı, dikkat katmanının hesaplama zamanı karmaşıklığının daha verimli olduğunu gösterir: 
Dikkat hesaplama zamanı yüzdesi, 'dikkat' ve 'tekrarlayan' toplamında 0.72%

Dikkat katmanının hesaplama zamanı karmaşıklığı, bu yapılandırmada CPU'da tekrarlayan katmandan daha iyi performans gösterir. Şimdi GPU'lara geçelim.

---

