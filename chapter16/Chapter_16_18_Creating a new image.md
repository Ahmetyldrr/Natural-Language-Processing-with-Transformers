# Notebook'un İlk Hücreleri ve DALL-E 3 API'si ile Görüntü Oluşturma

İlk hücre, notebook'un amacını belirler. Bunu tüm senaryolar için kullanabilirsiniz. Bu örnekte, ay yakınındaki bir restoranda sohbet robotuyla konuşan bir kişinin yeni bir görüntüsünü oluşturacağız ve görüntüyü bir dosyaya kaydedeceğiz: 
#prompt sequence= "Ay yakınındaki bir uzay gemisinde restoranda sohbet robotu kullanan bir kişinin görüntüsünü oluşturma." 
sequence, DALL-E 3'ü bir görüntü oluşturması için yönlendiren metin komutudur.

## OpenAI Kurulumu ve API Anahtarı

OpenAI kurulum, içe aktarma ve API anahtarı hücrelerini notebook'ta çalıştırın.

## DALL-E 3 API'sini Çalıştırma

Şimdi, Generation hücresine gidin ve DALL-E 3 API'sini çalıştırın:
```python
from openai import OpenAI
client = OpenAI()
response = client.images.generate(
  model="dall-e-3",
  prompt=sequence,
  size="1024x1024",
  quality="standard",
  n=1,
)
image_url = response.data[0].url
```
İstek, `client.images.generate` ile başlar. 
- `prompt`, bu notebook'un ilk hücrelerinde belirtilen belgelerde tanımladığımız `sequence`'dir.
- `model`, kullanılan DALL-E modelini belirtir (`dall-e-3`).
- `size`, oluşturulacak görüntünün boyutunu belirtir (`1024x1024`).
- `quality`, görüntünün kalitesini belirtir (`standard`).
- `n`, oluşturulacak görüntü sayısını belirtir (`1`).

## Oluşturulan Görüntüyü Görüntüleme ve Kaydetme

Görüntü oluşturulur, kaydedilir ve görüntülenir:
```python
# görüntüyü görüntüleme
url = image_url
image = Image.open(requests.get(url, stream=True).raw)
image.save("c_image.png", "PNG")
c_image = Image.open(requests.get(url, stream=True).raw)
c_image
```
- `url`, oluşturulan görüntünün URL'sini içerir.
- `Image.open` ve `requests.get`, görüntüyü URL'den alır ve açar.
- `image.save`, görüntüyü "c_image.png" olarak PNG formatında kaydeder.

Çıktı, oluşturulan görüntüyü görüntüler: 
Şekil 16.12: DALL-E 3 API tarafından oluşturulan görüntü

Aynı `sequence` için API'yi her çalıştırdığınızda, aynı görüntünün farklı bir sürümünü elde edebilirsiniz. Şimdi, bir görüntünün varyasyonunu oluşturalım.

---

