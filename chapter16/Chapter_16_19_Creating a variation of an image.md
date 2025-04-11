# DALL-E 2 ile Görüntü Varyasyonları Oluşturma

DALL-E 2'nin ne kadar yaratıcı olabileceğini görelim ve `c_image.png` olarak oluşturulup kaydedilen görüntü için bir varyasyon oluşturmasını isteyelim. Ocak 2024 itibariyle, OpenAI DALL-E 2'nin varyasyonlar oluşturmak için kullanılmasını öneriyor. Model şüphesiz gelişecek ve siz de onunla birlikte gelişeceksiniz! Aşağıdaki örnek Varyasyon hücresine bir örnektir.

# Varyasyon Oluşturma Kodu

DALL-E 2'ye bir görüntü seçip, orijinaline benzer ama daha yaratıcı bir varyasyon oluşturmasını istemek için aşağıdaki kodu kullanıyoruz:
```python
from openai import OpenAI
client = OpenAI()
response = client.images.create_variation(
  model="dall-e-2",  # Ocak 2024 itibariyle, varyasyonlar için dalle-e-2
  image=open("c_image.png", "rb"),  # Görüntü dosyasını açma
  n=2,  # Oluşturulacak varyasyon sayısı
  size="1024x1024"  # Oluşturulacak görüntünün boyutu
)
image_url = response.data[0].url  # Oluşturulan varyasyonun URL'si
```
### Kod Açıklaması

1. `from openai import OpenAI`: OpenAI kütüphanesinden `OpenAI` sınıfını içe aktarıyoruz.
2. `client = OpenAI()`: OpenAI istemcisini oluşturuyoruz.
3. `response = client.images.create_variation(...)`: DALL-E 2'ye bir varyasyon oluşturmasını istemek için `create_variation` metodunu çağırıyoruz.
   - `model="dall-e-2"`: Kullanılacak modeli belirtiyoruz.
   - `image=open("c_image.png", "rb")`: Varyasyon oluşturulacak görüntü dosyasını açıyoruz.
   - `n=2`: Oluşturulacak varyasyon sayısını belirtiyoruz.
   - `size="1024x1024"`: Oluşturulacak görüntünün boyutunu belirtiyoruz.
4. `image_url = response.data[0].url`: Oluşturulan varyasyonun URL'sini alıyoruz.

# Varyasyonun Gösterilmesi

Oluşturulan varyasyonu göstermek için aşağıdaki kodu kullanıyoruz:
```python
url = image_url
image = Image.open(requests.get(url, stream=True).raw)
v_image = Image.open(requests.get(url, stream=True).raw)
v_image
```
### Kod Açıklaması

1. `url = image_url`: Oluşturulan varyasyonun URL'sini `url` değişkenine atıyoruz.
2. `image = Image.open(requests.get(url, stream=True).raw)`: URL'deki görüntüyü indirip açıyoruz.
3. `v_image = Image.open(requests.get(url, stream=True).raw)`: Aynı URL'deki görüntüyü tekrar indirip açıyoruz.
4. `v_image`: Açılan görüntüyü gösteriyoruz.

Çıktı, ilginç bir varyasyon olabilir: 
# Şekil 16.13: Önceki görüntünün bir varyasyonu

Artık DALL-E 2 API'si ile görüntü varyasyonları oluşturup oluşturmayı biliyorsunuz. Bir AI görüntü sanatçısı olma yolundasınız! OpenAI, ana akım çevrimiçi DALL-E arayüzü ile bir adım daha ileri gitmiştir.

---

