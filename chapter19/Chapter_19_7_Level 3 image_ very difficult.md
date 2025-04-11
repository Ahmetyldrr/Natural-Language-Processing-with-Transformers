# İngilizce Paragrafın Türkçe Çevirisi

Sisli bir gecede bir arabayı indirin: 
```bash
!curl -L https://raw.githubusercontent.com/Denis2054/Transformers_3rd_Edition/master/Chapter18/car_in_fog.png --output "car_in_fog.png"
```
Bir görme modelinin karşı karşıya olduğu zorlukları doğrulamak için görüntüyü gösterin:
```python
image_path = "car_in_fog.png"
image = Image.open(image_path)
image
```
Çıktı, bu görüntünün bir insanı bile şaşırtabileceğini gösteriyor:
# Şekil 19.3: Gece tanımlanması zor bir araç
Keşif, HuggingGPT ile başlayacak.

# Python Kodlarının Açıklaması

1. `image_path = "car_in_fog.png"`
   - Bu satır, `image_path` adlı bir değişkene `"car_in_fog.png"` değerini atar. Bu değer, daha önce indirilen görüntünün dosya yoludur.

2. `image = Image.open(image_path)`
   - Bu satır, `Image` sınıfının `open` metodunu kullanarak `image_path` değişkeninde saklanan dosya yolundaki görüntüyü açar ve `image` değişkenine atar.
   - `Image` sınıfı, muhtemelen Python Imaging Library (PIL) veya onun bir fork'u olan Pillow'dan gelmektedir.

3. `image`
   - Bu satır, Jupyter Notebook gibi interaktif bir ortamda kullanıldığında, `image` değişkeninde saklanan görüntüyü gösterir. 
   - Standart Python scriptinde bu şekilde kullanılmaz; bunun yerine `image.show()` gibi bir metod kullanılabilir.

# Not
- `!curl` komutu, Jupyter Notebook içinde kullanılan bir komuttur ve harici komutları çalıştırmak için kullanılır. Bu komut, belirtilen URL'deki dosyayı indirir ve `"car_in_fog.png"` olarak kaydeder.
- Kodların çalışması için gerekli kütüphanelerin (`PIL` veya `Pillow`) yüklü olması gerekir.

---

