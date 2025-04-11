# DALL-E tarafından Üretilen Görüntünün GPT-4V ile Analizi

Şimdi GPT-4V'ye DALL-E tarafından üretilen görüntüyü analiz etmesini isteyeceğiz: Şekil 16.21: DALL-E tarafından üretilen bir köpeğin aşırı CV DAT'ı. DAT, görüntü oldukça divergent olduğu için korkutucu görünmektedir. Bununla birlikte, herhangi bir ek talimat veya ipucu olmadan standart bir istek yapıyoruz:

```python
from openai import OpenAI
client = OpenAI()
response = client.chat.completions.create(
  model="gpt-4-vision-preview",
  messages=[
    {
      "role": "user",
      "content": [
        {"type": "text", "text": "What's in this image?"},
        {
          "type": "image_url",
          "image_url": {
            "url": "https://raw.githubusercontent.com/Denis2054/AI_Educational/master/D4.png",
          },
        },
      ],
    }
  ],
  max_tokens=300,
)
```

## Kod Açıklaması

1. `from openai import OpenAI`: OpenAI kütüphanesinden `OpenAI` sınıfını içe aktarır.
2. `client = OpenAI()`: OpenAI sınıfının bir örneğini oluşturur.
3. `response = client.chat.completions.create(...)`: `client` nesnesinin `chat.completions.create` metodunu çağırarak bir sohbet tamamlama isteği gönderir.
   - `model="gpt-4-vision-preview"`: Kullanılacak modelin GPT-4V önizleme sürümü olduğunu belirtir.
   - `messages=[...]`: İsteğin içeriğini tanımlar. Burada bir kullanıcı mesajı vardır.
     - `"role": "user"`: Mesajın kullanıcı tarafından gönderildiğini belirtir.
     - `"content": [...]`: Mesajın içeriğini tanımlar. Burada hem metin hem de bir görüntü URL'si vardır.
       - `{"type": "text", "text": "What's in this image?"}`: Kullanıcının metin mesajını tanımlar.
       - `{"type": "image_url", "image_url": {"url": "..."}}`: Görüntü URL'sini tanımlar.
   - `max_tokens=300`: Yanıtın maksimum token sayısını 300 olarak sınırlar.

## Yanıtın İşlenmesi

Daha sonra metni biçimlendiriyoruz:
```python
import textwrap
choice = response.choices[0]
response_content = choice.message.content  # İçerik özelliğine erişim
# Metni bir paragrafa biçimlendirmek için textwrap kullanma
formatted_response = textwrap.fill(response_content, width=80)
# Biçimlendirilmiş yanıtı yazdırma
print(formatted_response)
```

### Kod Açıklaması

1. `import textwrap`: Metni biçimlendirmek için `textwrap` modülünü içe aktarır.
2. `choice = response.choices[0]`: Yanıttan ilk seçimi alır.
3. `response_content = choice.message.content`: Seçilen yanıttan içerik metnini alır.
4. `formatted_response = textwrap.fill(response_content, width=80)`: `textwrap.fill` metodunu kullanarak metni 80 karakter genişliğinde bir paragrafa biçimlendirir.
5. `print(formatted_response)`: Biçimlendirilmiş yanıtı yazdırır.

## Sonuç

Çıktı yaratıcıdır ve görüntünün divergensini kavrar. Ancak divergens köpeği tanımaz:
"This is a digitally created abstract image that features a variety of colors and shapes. It includes numerous swirling elements and circular patterns that somewhat resemble brush strokes with a dynamic and fluid feel. The colors are vivid and diverse, ranging from blues and purples to oranges, yellows, and reds, all set against a black background to enhance their vibrancy. These patterns and colors are arranged in a way that suggests the form of a stylized creature, perhaps a bird or another kind of animal, with an eye-like shape toward the right side. The overall effect is ornate and evokes a sense of movement. It's a piece that could be seen as an example of modern digital art that plays with color, form, and the idea of motion."

Metin köpeği tanımıyor, ancak bunu yapması gerekiyor mu? Görev divergens ve yaratıcılık hakkındadır. DALL-E tarafından üretilen görüntü ve GPT-4V tarafından oluşturulan metin, çoğu insanı geride bırakan inanılmaz yaratıcılık yetenekleri sergiler. "Küçük C" yapay zeka yaratıcılığının yeni bir çağına giriyoruz!

Birkaç vizyon modeli keşfettik ve DAT deneyleri gerçekleştirdik. Özetlemek ve bir sonraki maceramıza başlamak için şimdi özet bölümüne geçelim!

---

