# GPT-4V Kullanarak Görüntü Analizi

Bu not defterinde, OpenAI tarafından Ocak 2024'te önerilen `gpt-4-vision-preview` modelini kullanacağız. Tabii ki, modeller ve model isimleri gelişmeye devam edecek. Sürekli olarak dikkatli olmamız gerekiyor!

Kodun çalışmasını sağlamak için OpenAI'ın örnek kodunda bulunan Wikipedia'dan bir görüntüyü kullanacağız. Ayrıca, isteğin OpenAI'ın Ocak 2024 güncellemelerine uygun standart sohbet tamamlama formatında olduğuna dikkat edin:

```python
from openai import OpenAI
client = OpenAI()
response = client.chat.completions.create(
  model="gpt-4-vision-preview",
  messages=[
    {"role": "user", "content": [
        {"type": "text", "text": "What's in this image?"},
        {"type": "image_url", "image_url": {"url": "https://upload.wikimedia.org/wikipedia/commons/thumb/d/dd/Gfp-wisconsin-madison-the-nature-boardwalk.jpg/2560px-Gfp-wisconsin-madison-the-nature-boardwalk.jpg"}},
      ],
    }
  ],
  max_tokens=300,
)
```

## Yanıtı Biçimlendirme

Yanıt ham bir çıktıdır. Onu güzel bir şekilde biçimlendirelim ve görüntüleyelim:

```python
import textwrap
choice = response.choices[0]
response_content = choice.message.content  # İçerik özelliğine erişim
# Metni bir paragrafa biçimlendirmek için textwrap kullanın
formatted_response = textwrap.fill(response_content, width=80)
# Biçimlendirilmiş yanıtı yazdırma
print(formatted_response)
```

## Çıktı

Çıktı şimdi güzel bir şekilde biçimlendirilmiştir:

The image shows a beautiful natural landscape. A wooden boardwalk pathway
meanders through tall, lush green grass, which suggests that this might be a
wetland or marsh area where the boardwalk provides a walkway to prevent
disturbance to the ecosystem and to keep visitors' feet dry. The scene is
bathed in bright, natural light, indicating it is a sunny day with a few
scattered clouds in the sky. The skies are a vibrant blue, adding a sense of
tranquility to the landscape. Beyond the grass, there appear to be bushes or
shrubbery and a line of trees in the distance, which could signify the edge of
the wetland or the beginning of a forested area. Overall, the image conveys a
peaceful outdoor setting that is inviting for a walk or contemplation in nature.

## Doğruluk Kontrolü

Açıklama oldukça şiirsel. Ancak doğru mu? Görüntüyü görüntüleyerek öğrenelim:

```python
from IPython.display import Image, display
# Görüntünün URL'si
image_url = "https://upload.wikimedia.org/wikipedia/commons/thumb/d/dd/Gfp-wisconsin-madison-the-nature-boardwalk.jpg/2560px-Gfp-wisconsin-madison-the-nature-boardwalk.jpg"
# Görüntüyü görüntüleme
display(Image(url=image_url))
```

## Sonuç

Çıktı, GPT-4V tarafından alınan ve analiz edilen görüntünün bir özetini gösterir (Şekil 16.22). Bu, GPT-4V için kolay bir görevdi. Şimdi, farklı anlamsal ilişkilendirme alanına girelim.

---

