# Modelin Tanımını Görselleştirme

Modelin tanımını özelliklerine erişerek görselleştirebiliriz. Bu bölümde şunlara odaklanacağız: 
- `wv`: Kelime vektörlerini içeren nesne.
- `vector_size`: Kelime vektörlerinin boyut sayısı.
- `train_count`: `train()` fonksiyonunun çağrılma sayısı.
- `total_train_time`: Toplam kümülatif eğitim süresi (saniye cinsinden).
- `epochs`: Eğitim epoch sayısı.
- `sg`: Eğitim algoritması: 1 için skip-gram; 0 için CBOW

Keşfetmeyi seçtiğimiz özellikleri görüntüleyen bir widget oluşturabiliriz:

```python
from IPython.display import display
import ipywidgets as widgets

# Modeli yükle
model = Word2Vec.load("descartes_word2vec.model")

# Model özelliği için widget
attr_widget = widgets.Dropdown(
    options=['wv', 'vector_size', 'train_count', 'total_train_time', 'epochs'],
    value='wv',
    description='Özellik:',
)
display(attr_widget)

# Satır sayısı için widget
num_lines_widget = widgets.IntSlider(
    min=0, 
    max=100, 
    step=1, 
    value=10, 
    description='Satırlar:'
)
display(num_lines_widget)

# Verileri görüntülemek için buton
display_button = widgets.Button(description='Görüntüle')
display(display_button)

# Verileri görüntüleme fonksiyonu
def display_data(button):
    attr = attr_widget.value
    num_lines = num_lines_widget.value
    
    if attr == 'wv':
        # Kelimeleri listele
        words = list(model.wv.index_to_key)
        
        # İlk num_lines kelimeyi yazdır
        for word in words[:num_lines]:
            print(word, model.wv[word])
    else:
        # Modelin özelliğini yazdır
        print(getattr(model, attr))

# Fonksiyonu butona bağla
display_button.on_click(display_data)
```

Özellikler bir açılır listede görüntülenir. Birini seçip görüntüleyebilirsiniz. Örneğin, bir kelimeyi temsil eden boyutların vektör boyutunu elde edebiliriz:

# Vektör Boyutunu Seçme

Tokenlerin (bu durumda kelimelerin) 300 boyutlu bir vektörle temsil edildiğini görüyoruz. Bu vektörleri `wv` üzerine tıklayarak görüntüleyebilirsiniz. Bu durumda, görüntülemek istediğiniz satır sayısını seçin. Yalnızca bir kelimeyi görüntülemek için 1 olarak ayarlayabilirsiniz:

# Görüntülemek İstediğiniz Kelime Sayısını Seçme

Bir kelimenin sayısal temsilini aşağıdaki alıntıda gösterildiği gibi göreceksiniz:
```
[-1.7703770e-04  8.0561076e-05  1.7074384e-03  3.0068988e-03
 -3.1028548e-03 -2.3738446e-03  2.1451029e-03  2.9889001e-03
 -1.6721861e-03 -1.2577033e-03  2.4635433e-03 -5.1635387e-04
 -1.5168249e-03  2.1891161e-03 -1.6221605e-03 -6.0506846e-04
  9.5858454e-04  3.3036861e-04 -2.7588590e-03 -3.1527190e-03
```

Modelin diğer özelliklerini açılır listede keşfedebilir ve gerekirse daha fazlasını ekleyebilirsiniz. Daha fazla bilgi için Genism'in Word2Vec belgelerine bakın: https://radimrehurek.com/gensim/models/word2vec.html .

Modelin bazı özelliklerinin içeriğini görüntüledik. Şimdi bir kelimeye ve vektörüne doğrudan erişeceğiz.

### Python Kodlarının Açıklaması

1. `from IPython.display import display` : IPython'ın display fonksiyonunu içe aktarır. Bu fonksiyon, Jupyter Notebook'ta widget'ları görüntülemek için kullanılır.

2. `import ipywidgets as widgets` : ipywidgets kütüphanesini içe aktarır ve `widgets` takma adını verir. Bu kütüphane, Jupyter Notebook'ta etkileşimli widget'lar oluşturmak için kullanılır.

3. `model = Word2Vec.load("descartes_word2vec.model")` : `Word2Vec` modelini "descartes_word2vec.model" dosyasından yükler.

4. `attr_widget = widgets.Dropdown(...)` : Bir açılır liste widget'ı oluşturur. Seçenekler modelin özellikleri (`'wv'`, `'vector_size'`, `'train_count'`, `'total_train_time'`, `'epochs'`).

5. `num_lines_widget = widgets.IntSlider(...)` : Bir sayısal kaydırma çubuğu widget'ı oluşturur. Bu, görüntülemek istediğiniz satır sayısını seçmek için kullanılır.

6. `display_button = widgets.Button(description='Görüntüle')` : Bir buton widget'ı oluşturur. Bu butona tıklandığında, `display_data` fonksiyonu çağrılır.

7. `def display_data(button):` : `display_data` fonksiyonunu tanımlar. Bu fonksiyon, butona tıklandığında çağrılır.

   - `attr = attr_widget.value` : Seçilen özelliği alır.
   - `num_lines = num_lines_widget.value` : Seçilen satır sayısını alır.
   - `if attr == 'wv':` : Eğer seçilen özellik `wv` ise, kelimeleri ve vektörlerini listeler.
   - `else:` : Diğer durumlarda, modelin seçilen özelliğini yazdırır.

8. `display_button.on_click(display_data)` : `display_data` fonksiyonunu butona bağlar. Butona tıklandığında bu fonksiyon çağrılır.

---

