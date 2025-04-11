# İngilizce Paragrafın Türkçe Çevirisi

İlk resim, seviye 1, kolay resimdir: !curl -L https://raw.githubusercontent.com/Denis2054/Transformers_3rd_Edition/master/Chapter16/generate_an_image_of_a_car_in_space.jpg --output "generate_an_image_of_a_car_in_space.jpg" 
Bunu, bölümün geri kalanında aklımızda tutmak için görüntüleyelim: 
```python
from PIL import Image # PIL kütüphanesinden Image modülünü içe aktar

# Resminizin pathini tanımlayın
image_path = "/content/generate_an_image_of_a_car_in_space.jpg" 

# Resmi açın
image = Image.open(image_path)
image 
```
Çıktı, siyah bir arka plan üzerinde beyaz bir arabayı gösteriyor, ki bu herhangi bir iyi eğitilmiş bilgisayarlı görü modelinin tespit etmesi gereken bir şeydir: 
## Şekil 19.1: Uzayda bir araba 
Şimdi zor resmi indirelim.

# Python Kodlarının Satır Satır Açıklaması

1. `from PIL import Image` : 
   - Bu satır, Python Imaging Library (PIL) kütüphanesinden `Image` modülünü içe aktarır. 
   - `Image` modülü, resim dosyalarını açmak, manipüle etmek ve kaydetmek için kullanılır.

2. `image_path = "/content/generate_an_image_of_a_car_in_space.jpg"` : 
   - Bu satır, `/content/generate_an_image_of_a_car_in_space.jpg` yolunu `image_path` değişkenine atar. 
   - `image_path`, açılması istenen resmin dosya yolunu tutar.

3. `image = Image.open(image_path)` : 
   - Bu satır, `image_path` değişkeninde tutulan dosya yolunu kullanarak resmi açar. 
   - `Image.open()` fonksiyonu, belirtilen yoldaki resmi açar ve bir `Image` nesnesi olarak döndürür.

4. `image` : 
   - Bu satır, açılan resmi gösterir. 
   - Jupyter Notebook gibi interaktif ortamlarda, son satırdaki ifade otomatik olarak görüntülenir. Bu nedenle, `image` değişkeni son satırda olduğu için resmi görüntüler.

---

