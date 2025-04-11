# OpenAI'ın Güçlü Transformer Motorları

OpenAI, dünyadaki en güçlü transformer motorlarından bazılarına sahiptir. Bir GPT-4 modeli yüzlerce görevi yerine getirebilir. GPT-3, eğitilmediği birçok görevi yapabilir. Bu bölüm, Getting_Started_GPT_4_API.ipynb'de API'yi kullanacaktır. GPT-3'ü kullanmak için OpenAI'ın web sitesine, https://openai.com/ adresine gidin ve kaydolun. Başlamak için OpenAI tarafından sağlanan örnekleri çalıştırabiliriz. Bir kez daha asistanlara güveniyoruz.

Python kodları bulunmamaktadır, sadece bir paragraf çevirisi yapılmıştır.

Eğer bir python kodu olsaydı, örneğin:
```python
# GPT-4 API'sini kullanmak için örnek kod
import openai

# OpenAI API anahtarını tanımlayın
openai.api_key = "API_ANAHTARINIZ"

# GPT-4 modelini kullanarak bir metin oluşturun
response = openai.Completion.create(
    engine="gpt-4",
    prompt="Merhaba, dünya!",
    max_tokens=1024
)

# Oluşturulan metni yazdırın
print(response.choices[0].text)
```
Yukarıdaki kod için satır satır açıklama:
1. `# GPT-4 API'sini kullanmak için örnek kod` : Kodun amacını açıklayan bir yorum satırı.
2. `import openai` : OpenAI kütüphanesini içe aktarır.
3. `openai.api_key = "API_ANAHTARINIZ"` : OpenAI API anahtarını tanımlayın. "API_ANAHTARINIZ" yerine gerçek API anahtarınızı yazmalısınız.
4. `response = openai.Completion.create(...)` : GPT-4 modelini kullanarak bir metin oluşturur.
   - `engine="gpt-4"` : Kullanılacak modeli belirtir (GPT-4).
   - `prompt="Merhaba, dünya!"` : Oluşturulacak metnin başlangıç noktası.
   - `max_tokens=1024` : Oluşturulacak metnin maksimum uzunluğu.
5. `print(response.choices[0].text)` : Oluşturulan metni yazdırır.

---

