# Çapraz Platform Model Zincirleme Deneyimi

Çapraz platform, model zincirleme deneyimimiz, Midjourney çıktısını basit bir istemle Runway Gen-2'ye göndererek devam ediyor: "Bu gemiyi denizde yüzdürün." Sonuçları indirelim: 
```bash
!curl -L https://raw.githubusercontent.com/Denis2054/Transformers_3rd_Edition/master/Chapter19/ship_in_galaxy.mp4 --output "ship_in_galaxy.mp4"
```
Gen-2, Midjourney görüntüsünü işleyebileceği bir temsile dönüştürür. Ortaya çıkan video oldukça umut verici. 
Görselleştirelim:

```python
from moviepy.editor import * 
# ship_in_galaxy.mp4 dosyasını yükleyelim ve 00:00:00 - 00:00:07 alt klibini seçelim
clip = VideoFileClip("ship_in_galaxy.mp4").subclip(0, 7)
# Klibi 5 kez döngüye alalım
clip = clip.loop(5)
# Klibi ipython'da 900 genişliğinde gösterelim
clip.ipython_display(width=900)
```
Bu kodu chapter notebook'unda çalıştırabilirsiniz: 
# Şekil 19.16: Gemi AI tarafından oluşturulan video

Bu bölümde, çapraz modellemeyi vizyon Generative AI'ya uyguladık. Örneğin, pazarlama potansiyeli bizi otomatik reklam kampanyalarına oldukça ileri götürebilir. Bu bölümü özetleyip bir sonraki keşfe geçme zamanı. 

**Satır Satır Python Kodu Açıklaması**

1. `from moviepy.editor import *` : moviepy kütüphanesinin editor modülünden tüm fonksiyonları import eder.
2. `clip = VideoFileClip("ship_in_galaxy.mp4").subclip(0, 7)` : 
   - `VideoFileClip("ship_in_galaxy.mp4")` : "ship_in_galaxy.mp4" dosyasını yükler.
   - `.subclip(0, 7)` : Yüklenen videodan 0. saniyeden 7. saniyeye kadar olan kısmı seçer.
3. `clip = clip.loop(5)` : Seçilen klibi 5 kez döngüye alır.
4. `clip.ipython_display(width=900)` : Klibi ipython ortamında 900 genişliğinde gösterir.

---

