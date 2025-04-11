# Stable Diffusion'ın Keras Uygulamasını Keşfetmek

Kararlı Diffüzyon'un minimalist Keras uygulamasını çalıştıran yetenekli minimalist kodu gördük. Şimdi sonucun sihrini izleyelim. GitHub deposunun chapter dizininde Stable Diffusion_Keras.ipynb dosyasını açın. Öncelikle TensorFlow'un yüklü olduğundan emin oluyoruz: 
# TensorFlow'u İçe Aktarma
```python
try:
    import tensorflow as tf
    print(tf.__version__)
except:
    !pip install tensorflow
    import tensorflow as tf
    print(tf.__version__)
```
Bu kod bloğu, TensorFlow'un yüklü olup olmadığını kontrol eder. Eğer yüklü değilse, `!pip install tensorflow` komutunu kullanarak TensorFlow'u yükler.

Daha sonra Keras bilgisayar görüşü kütüphanesini ve geliştirilmiş bir API arka ucu olan `keras_core`'u yüklüyoruz:
```bash
!pip install keras_cv --upgrade --quiet
!pip install keras_core --upgrade --quiet
```
Bu komutlar, Keras_cv ve keras_core'u günceller ve yükler.

Yaklaşımın basitliği etkileyicidir. Şimdi ihtiyacımız olan modülleri içe aktarıyoruz:
```python
import time
import keras_cv
from tensorflow import keras
import matplotlib.pyplot as plt
```
Bu satırlar, gerekli kütüphaneleri içe aktarır.

Keras modelimizi seçiyoruz:
```python
model = keras_cv.models.StableDiffusion(img_width=512, img_height=512)
```
Bu kod, 512x512 görüntü boyutu ile Stable Diffusion modelini oluşturur.

Model, önceki bölümlerde gördüğümüz gibi çalışır. Model, metin kodlayıcısını çalıştırır, ardından 64x64 latent görüntü yamasını diffüzyon modeli ile kademeli olarak "gürültüyü temizler". Son olarak, "gürültüsü temizlenmiş" 64x64 yamasını daha yüksek çözünürlüklü (bazen "süper çözünürlük" olarak da adlandırılır) 512x512 görüntüye dönüştürür.

Artık bir istem ile görüntüler oluşturabilir ve görüntüleri çizebiliriz:
```python
images = model.text_to_image("photograph of an astronaut on Mars with a sunset", batch_size=3)

def plot_images(images):
    plt.figure(figsize=(20, 20))
    for i in range(len(images)):
        ax = plt.subplot(1, len(images), i + 1)
        plt.imshow(images[i])
        plt.axis("off")

plot_images(images)
```
Bu kod, "Mars'ta gün batımı ile astronotun fotoğrafı" istemi ile 3 görüntü oluşturur ve bunları çizer.

Çıktı, bu kompakt kod için şaşırtıcıdır: 
# Şekil 17.3: Stable Diffusion Tarafından Oluşturulan Astronot Görüntüsü

Keras ekibinin hayal ettiği daha karmaşık eğlenceli istemi deneyebiliriz:
```python
images = model.text_to_image(
    "cute magical flying dog, fantasy art, "
    "golden color, high quality, highly detailed, elegant, sharp focus, "
    "concept art, character concepts, digital painting, mystery, adventure",
    batch_size=3,
)
plot_images(images)
```
Bu kod, "sevimli sihirli uçan köpek, fantastik sanat, altın rengi, yüksek kalite, son derece detaylı, zarif, keskin odak, kavramsal sanat, karakter kavramları, dijital resim, gizem, macera" istemi ile 3 görüntü oluşturur ve bunları çizer.

Çıktı mükemmeldir: 
# Şekil 17.4: Stable Diffusion Tarafından Oluşturulan Uçan Köpek Görüntüsü

Stable Diffusion'ın Keras uygulaması, sadece övgü alabilecek fantastik bir eğitici ve üretken bir yaklaşımı temsil eder. Şimdi Stability AI'ın Diffüzyon API'si ile deneylerimizi genişleteceğiz.

---

