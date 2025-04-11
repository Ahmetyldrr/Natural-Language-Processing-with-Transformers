# OpenAI İnce Ayar Dokümantasyonu Çevirisi

OpenAI ince ayar dokümantasyonu: https://platform.openai.com/docs/guides/fine-tuning

Aşağıdaki metin OpenAI ince ayar dokümantasyonunun birebir Türkçe çevirisidir.

İlgili İngilizce paragraf bulunmamaktadır, lütfen paragrafı sağlar mısınız?

(Eğer ilgili paragrafı sağlarsanız, onu birebir Türkçeye çeviririm ve Python kodları varsa satır satır açıklama yaparım.) 

Örnek bir paragraf ekleyerek devam edelim:

İngilizce Paragraf:
"Fine-tuning is a process that allows you to customize a pre-trained model to fit your specific needs. It involves adjusting the model's parameters to better suit your dataset."

Türkçe Çevirisi:
"İnce ayar, önceden eğitilmiş bir modeli özel ihtiyaçlarınıza uyacak şekilde özelleştirmenizi sağlayan bir süreçtir. Modelin parametrelerini veri setinize daha uygun hale getirmek için ayarlamayı içerir."

# Python Kodları Açıklaması

Eğer bir Python kodu örneği olsaydı, örneğin:
```python
import openai

# OpenAI API anahtarını ayarla
openai.api_key = "API-ANAHTARINIZ"

# İnce ayar için model seçimi
model = "davinci"

# İnce ayar işlemi
response = openai.FineTune.create(
    training_file="dosya_id",
    model=model,
    n_epochs=4
)

print(response)
```
Yukarıdaki kod örneği için satır satır açıklama:
1. `import openai`: OpenAI kütüphanesini içe aktarır.
2. `openai.api_key = "API-ANAHTARINIZ"`: OpenAI API anahtarını ayarlar. Burada `"API-ANAHTARINIZ"` yerine gerçek API anahtarınız yazılmalıdır.
3. `model = "davinci"`: İnce ayar için kullanılacak modeli seçer. Burada `"davinci"` modeli seçilmiştir.
4. `response = openai.FineTune.create(...)`: İnce ayar işlemini başlatır. 
   - `training_file="dosya_id"`: Eğitim verisinin bulunduğu dosyanın ID'sini belirtir.
   - `model=model`: Kullanılacak modeli belirtir.
   - `n_epochs=4`: Eğitim epoch sayısını 4 olarak ayarlar.
5. `print(response)`: İnce ayar işleminin sonucunu yazdırır.

Lütfen çevirmek istediğiniz paragrafı veya kodları bana verin.

---

