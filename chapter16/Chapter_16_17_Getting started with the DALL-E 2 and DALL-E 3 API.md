# DALL-E API ile Görüntü Oluşturma ve Değiştirme

DALL-E'nin metinden görüntüye işlevselliği kısa sürede dramatik bir şekilde gelişti. Dönüştürücüler (Transformers) çok modlu ve çeşitli görevleri yerine getirebilir (ses, görüntü ve diğer sinyaller). Bu bölüm DALL-E 2 ve DALL-E 3'ü uygulamaktadır. API, bir görüntünün varyasyonlarını oluşturmamıza ve üretmemize olanak tanır. Getting_Started_DALL_E_API.ipynb dosyasını açın. Projeniz için uygun gördüğünüz şekilde DALL-E 2 ve DALL-E 3 API'sini uygulayabilirsiniz. Program önce Pillow'u (bir Python görüntü işleme kütüphanesi) ve OpenAI API kütüphanesini kurar, bu sizin API anahtarınızı gerektirecektir.

## Kodun Açıklaması

Aşağıdaki python kodları Getting_Started_DALL_E_API.ipynb dosyasının içeriğini temsil etmektedir.

```python
# Pillow ve OpenAI API kütüphanelerini kurmak için
!pip install Pillow openai
```

Bu satır, gerekli kütüphaneleri kurar. `!pip install` komutu Jupyter Notebook içinde kütüphane kurmak için kullanılır.

```python
# OpenAI API kütüphanesini import etmek için
import openai
```

OpenAI API kütüphanesini kullanarak API anahtarınızı yapılandırabilir ve DALL-E ile etkileşime geçebilirsiniz.

```python
# API anahtarınızı yapılandırmak için
openai.api_key = "API_ANAHTARINIZ"
```

Burada `"API_ANAHTARINIZ"` kısmını kendi OpenAI API anahtarınız ile değiştirmelisiniz.

```python
# DALL-E 2 ile görüntü oluşturmak için
response = openai.Image.create(
  prompt="Oluşturulacak görüntünün metin açıklaması",
  n=1,
  size="1024x1024"
)
```

Bu kod, DALL-E 2 kullanarak belirtilen metin açıklaması temelinde bir görüntü oluşturur.

```python
# Oluşturulan görüntüyü göstermek için
from PIL import Image
import requests
from io import BytesIO

image_url = response['data'][0]['url']
response = requests.get(image_url)
img = Image.open(BytesIO(response.content))
img.show()
```

Bu bölüm, oluşturulan görüntüyü gösterir.

## İki Ana Başlık

Bu bölüm iki ana başlığa ayrılmıştır:
1. **Yeni bir görüntü oluşturma**
2. **Bir görüntünün varyasyonunu oluşturma**

İlk olarak, bir görüntü oluşturalım.

Getting_Started_DALL_E_API.ipynb dosyasını hücre hücre çalıştırarak sağlanan işlevselliği kavrayabilir veya bir senaryo için tüm not defterini çalıştırabilirsiniz.

---

