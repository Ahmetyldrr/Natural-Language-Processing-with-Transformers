# Gece Görüntüsündeki Araba Daha Gelişmiş Bilgisayarlı Görü Modelleri Gerektiriyor

Gece görüntüsündeki araba daha gelişmiş bilgisayarlı görü modelleri gerektiriyor: 
```bash
curl -L https://raw.githubusercontent.com/Denis2054/Transformers_3rd_Edition/master/Chapter18/car_in_night.jpg --output "car_in_night.jpg"
```
Eğer görüntüyü gösterirsек, zorluğu görebiliriz: 
```python
from PIL import Image 
# Görüntünün yolunu tanımla
image_path = "/content/car_in_night.jpg" 
# Görüntüyü aç
image = Image.open(image_path)
image
```
Çıktı, kafa karıştırıcı nesneler içerir (sokak lambaları, parlak yüzeyler ve koyu renkli arabalar): 
## Şekil 19.2: Geceleyin Bir Araba 
 Seviye 3, çok zor görüntü, oldukça zorlu bir challenge olarak kalır.

---

