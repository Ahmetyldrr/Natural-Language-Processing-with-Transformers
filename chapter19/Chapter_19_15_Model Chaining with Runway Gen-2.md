# Bölüm Çevirisi

Bu bölümde, bir Midjourney görüntüsünün çıktısını Gen-2 görüntüden videoya hizmetinin girdisine bağlayacağız. İlk olarak, modele Mars'ta bir rover'ı süren bir astronotun videosunu oluşturmasını isteyen bir istem tarafından üretilen örnek bir Gen-2 videosunu indirelim: 
```bash
!curl -L https://raw.githubusercontent.com/Denis2054/Transformers_3rd_Edition/master/Chapter19/Gen-2_Mars.mp4 --output "Gen-2_Mars.mp4"
```
Şimdi bunu bölüm not defterinde görüntüleyebiliriz:

## Python Kodları ve Açıklamaları

### Adım 1: Gerekli Kütüphaneyi İçe Aktarma
```python
from moviepy.editor import *
```
Bu satır, `moviepy.editor` modülünü içe aktarır. `moviepy`, videoları düzenlemek için kullanılan bir Python kütüphanesidir.

### Adım 2: Video Dosyasını Yükleme ve Alt Klibi Seçme
```python
clip = VideoFileClip("Gen-2_Mars.mp4").subclip(00, 7)
```
Bu satır, `"Gen-2_Mars.mp4"` adlı video dosyasını yükler ve videonun ilk 7 saniyesini (`00:00:00` - `00:00:07`) `clip` değişkenine atar.

### Adım 3: Videoyu Döngüye Alma
```python
clip = clip.loop(5)
```
Bu satır, `clip` değişkenindeki videoyu 5 kez döngüye alır, yani video 5 kez arka arkaya oynatılır.

### Adım 4: Videoyu Görüntüleme
```python
clip.ipython_display(width=900)
```
Bu satır, `clip` değişkenindeki videoyu Jupyter Notebook içinde `900` piksel genişliğinde görüntüler.

## Sonuç

Not defterinde görüntüleyebileceğiniz video oldukça umut verici. 
## Şekil 19.14: Mars'ta Bir Astronot Hakkında AI Üretimi Bir Videonun Ekran Görüntüsü
Şimdi, Midjourney'i Gen-2'ye bağlayalım.

---

