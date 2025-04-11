# Örnek 2: DALL-E ile Oluşturulan Görüntünün GPT-4V ile Analizi

Örnek 2, bu bölümün "DALL-E ile ChatGPT Plus kullanarak görüntü oluşturma" alt bölümünde DALL-E tarafından üretilen görüntüdür: Şekil 16.20: DALL-E tarafından üretilen gelişmiş CV DAT köpeği. GPT-4V, şekildeki köpeği tanıyabilir mi? Standart görüntü için herhangi bir ek talimat olmadan aşağıdaki gibi bir istek yapıyoruz:

```python
from openai import OpenAI
client = OpenAI()
response = client.chat.completions.create(
  model="gpt-4-vision-preview",
  messages=[
    {"role": "user", "content": [
        {"type": "text", "text": "What's in this image?"},
        {"type": "image_url", "image_url": {"url": "https://raw.githubusercontent.com/Denis2054/AI_Educational/master/dog.png"}},
      ],
    }
  ],
  max_tokens=300,
)
```

## Kod Açıklaması

1. `from openai import OpenAI`: OpenAI kütüphanesinden `OpenAI` sınıfını içe aktarır. Bu, OpenAI API'sine bağlanmak için kullanılır.
2. `client = OpenAI()`: `OpenAI` sınıfının bir örneğini oluşturur. Bu, OpenAI API'sine bağlanmak için kullanılan istemci nesnesidir.
3. `response = client.chat.completions.create(...)`: `client` nesnesini kullanarak `chat.completions.create` metodunu çağırır. Bu, GPT-4V modeline bir istek gönderir ve bir yanıt alır.
   - `model="gpt-4-vision-preview"`: Kullanılacak GPT modelini belirtir. Burada "gpt-4-vision-preview" modeli kullanılıyor.
   - `messages=[...]`: GPT modeline gönderilen iletileri tanımlar. Burada bir kullanıcı iletisi (`"role": "user"`) ve bu iletinin içeriği (`"content"`).
     - `"type": "text", "text": "What's in this image?"`: Metin türünde bir içerik tanımlar. Bu, GPT modeline "Bu görüntüde ne var?" sorusunu sorar.
     - `"type": "image_url", "image_url": {"url": "..."}`: Görüntü türünde bir içerik tanımlar. Burada görüntü URL'si belirtilir.
   - `max_tokens=300`: Yanıt için maksimum token sayısını belirtir.

## Yanıtın İşlenmesi

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

1. `import textwrap`: `textwrap` modülünü içe aktarır. Bu, metni belirli bir genişliğe göre biçimlendirmek için kullanılır.
2. `choice = response.choices[0]`: Yanıttan ilk seçimi (`choices` listesindeki ilk öğe) alır.
3. `response_content = choice.message.content`: Seçilen yanıttan içerik metnini alır.
4. `formatted_response = textwrap.fill(response_content, width=80)`: `textwrap.fill` metodunu kullanarak içerik metnini 80 karakter genişliğinde bir paragrafa biçimlendirir.
5. `print(formatted_response)`: Biçimlendirilmiş yanıtı yazdırır.

## Sonuç

Çıktı, GPT-4V'nin yalnızca köpeği tanımadığını, aynı zamanda görüntünün oldukça yaratıcı bir tanımını yaptığını gösterir:

Bu görüntü, bir köpeğin son derece stilize edilmiş ve renkli bir dijital illüstrasyonunu içerir. Sanat eseri, bir köpeğin soyut bir temsilini oluşturmak için bir araya gelen çeşitli dönen şekiller ve desenlerden oluşur. Arka plan, köpek için kullanılan canlı ve çeşitli renk paletinin kontrast oluşturduğu, yıldızlı bir gece gökyüzünü andıran benekli noktalara sahiptir. Dönen desenler, görüntüye dinamik ve hayalperest bir his verir, bir hareket ve enerji hissi sağlar. Metin hem doğru hem de güzeldir.

Daha sonra, Şekil 16.20'de gösterilen görüntü notebook'ta görüntülenir. Şimdi, GPT-4V'yi farklı semantik çağrışımların sınırlarına kadar zorlayalım.

---

