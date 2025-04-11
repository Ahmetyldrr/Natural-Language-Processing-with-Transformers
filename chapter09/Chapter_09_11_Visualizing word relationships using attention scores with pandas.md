# Çıktıların Akışı
Çıktıların akışı, dikkat başlık çıktıları hakkında değerli bilgiler sağlar. Ancak, kelime x kelime matrisindeki ilişkileri görüntülemek, modeli yorumlamayı çok daha erişilebilir hale getirecektir. Program ilk olarak verileri bir DataFrame'de yüklemek için pandas'ı içe aktararak başlar. Ardından, açılır menüler ve filtreler gibi etkileşimli bir arayüz oluşturmak için ipywidgets'ı içe aktarır:

# Pandas'ta Çıktıların Gösterilmesi
```python
import pandas as pd
import ipywidgets as widgets
```
Program şimdi her katman ve her başlık dikkat matrisi için bir DataFrame oluşturabilir:
# Her Katman ve Başlık Dikkat Matrisi için DataFrame Oluşturma
```python
df_layers_heads = []
for layer, attention in enumerate(attentions):
    for head, head_attention in enumerate(attention[0]):
        attention_matrix = head_attention[:len(tokens), :len(tokens)].detach().numpy()  # tensörü gradyanlardan ayır ve numpy'e çevir
        df_attention = pd.DataFrame(attention_matrix, index=tokens, columns=tokens)
        df_layers_heads.append((layer, head, df_attention))
```
Program, görüntüleme seçeneklerini ayarlar:
# DataFrame Görüntüleme Seçeneklerini Ayarlama
```python
pd.set_option('display.max_columns', None)
pd.set_option('display.expand_frame_repr', False)
pd.set_option('max_colwidth', None)
```
Dikkat matrisini görüntülemek için bir fonksiyona ihtiyacımız var:
# Dikkat Matrisini Görüntüleme Fonksiyonu
```python
def display_attention(selected_layer, selected_head):
    _, _, df_to_display = next(df for df in df_layers_heads if df[0] == selected_layer and df[1] == selected_head)
    display(df_to_display)
```
Katmanlar ve başlık için etkileşimli widget'lar oluşturmaya devam ediyoruz:
# Katman ve Başlık için Etkileşimli Widget'lar Oluşturma
```python
layer_widget = widgets.IntSlider(min=0, max=len(attentions)-1, step=1, description='Layer:')
head_widget = widgets.IntSlider(min=0, max=len(attentions[0][0])-1, step=1, description='Head:')
```
Etkileşimli arayüzümüz görüntülenmeye hazır:
# Etkileşimli Arayüzü Kullanma
```python
widgets.interact(display_attention, selected_layer=layer_widget, selected_head=head_widget)
```
Çıktı, her başlıkta (0'dan 11'e kadar) kelimeler arasındaki ilişkilerin değerlerini, katmanlar (0'dan 12'ye kadar) boyunca ilerledikçe görüntüleyen yorumlanabilir bir arayüzdür:
Şekil 9.7: Farklı Katmanlar ve Başlıklar için Çıktı

Artık bir katman ve bir başlık seçerek dikkat başlıklarının çıktılarını analiz edebilirsiniz. Örneğin, "attention" ve "values" kelimeleri arasındaki ilişkiye bakalım, katman 0'da başlık 0 için. "values" kaynak kelimesi ile "attention" hedef kelimesi arasındaki ilişki, "values" için en yüksek değildir. Dikkatlice bakarsanız, "the" kelimesinin "values" kelimesini "attention"dan daha fazla çektiğini göreceksiniz:
Şekil 9.8: Katman 0 ve Başlık 0 için Çıktı

Şimdi, "values" ve "attention" kelimeleri arasındaki ilişkiye bakalım, katman 9'da başlık 9 için:
Şekil 9.9: Katman 9 ve Başlık 9 için Çıktı

"values" kaynak kelimesi ile "attention" hedef kelimesi arasındaki ilişki, "values" ve "the" arasındaki ilişkiden daha yüksektir. Model öğreniyor! Gösterimler, modelin yeterince eğitilip eğitilmediğini ve mimarinin verimli olup olmadığını gösterebilir. Her durumda, yorumlama, bir modeli değerlendirmek ve yorumlamak için size yardımcı olacak tam olarak budur. Modelin mimarisinin yalnızca bir kısmını diğer alt katmanları uygulamadan önce inceledik. Bu bölümden ayrılmadan önce, BERT model dikkat başlığı keşiflerimize exBERT, başka bir kaynak, ekleyeceğiz.

---

