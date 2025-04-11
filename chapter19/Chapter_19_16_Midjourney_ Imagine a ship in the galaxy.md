# Midjourney Tarafından Üretilen Bir Görüntünün İndirilmesi ve Kullanılması

Midjourney tarafından üretilen ve galakside bir gemi prompt'u kullanılarak oluşturulan bir görüntüyü indirelim: 
```bash
!curl -L https://raw.githubusercontent.com/Denis2054/Transformers_3rd_Edition/master/Chapter19/ship_in_galaxy.jpg --output "ship_in_galaxy.jpg"
```
Şimdi görüntüyü gösterebiliriz:
```python
from PIL import Image 
# Görüntünün yolunu tanımlayın
image_path = "/content/ship_in_galaxy.jpg" 
# Görüntüyü açın
image = Image.open(image_path)
image
```
Çıktı oldukça güzel ve yararlıdır, Şekil 19.25'te gösterildiği gibi. Klasik yazılım kullanarak böyle bir görüntüyü üretmek zaman ve kaynak gerektirecektir. Örneğin, bu görüntünün bir pazarlama kampanyası için nasıl kullanılabileceğini hayal edebiliriz: 
# Şekil 19.15: Galakste Yelken Açan Bir Geminin AI Üretimi Görüntüsü
Bu çıktıyı başka bir sistemin girdisine bağlayabilir miyiz? Hadi öğrenelim ve Gen-2'ye bu görüntüyle bir video yapmasını soralım.

**Kod Açıklaması**

1. `!curl -L https://raw.githubusercontent.com/Denis2054/Transformers_3rd_Edition/master/Chapter19/ship_in_galaxy.jpg --output "ship_in_galaxy.jpg"`
   - Bu komut, belirtilen URL'deki görüntüyü "ship_in_galaxy.jpg" olarak kaydeder.
   - `!curl`: curl komutunu çalıştırmak için kullanılan bir jupyter notebook komutudur.
   - `-L` seçeneği, curl'un yönlendirmeleri takip etmesini sağlar.
   - `--output "ship_in_galaxy.jpg"` seçeneği, indirilen veriyi "ship_in_galaxy.jpg" dosyasına kaydeder.

2. `from PIL import Image`
   - Bu satır, Python Imaging Library (PIL) modülünden Image sınıfını içe aktarır.

3. `image_path = "/content/ship_in_galaxy.jpg"`
   - Bu satır, görüntünün dosya yolunu `image_path` değişkenine atar.

4. `image = Image.open(image_path)`
   - Bu satır, `image_path` değişkeninde belirtilen görüntüyü açar ve `image` değişkenine atar.

5. `image`
   - Bu satır, görüntüyü gösterir. Jupyter Notebook gibi bazı ortamlarda, bu komut görüntüyü doğrudan gösterebilir.

---

