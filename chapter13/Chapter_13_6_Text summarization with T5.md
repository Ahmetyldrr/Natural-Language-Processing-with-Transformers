# Doğal Dil İşleme (NLP) Özetleme Görevleri

NLP özetleme görevleri, bir metnin özlü kısımlarını çıkarır. Bu bölüm, bu bölümde kullanacağımız Hugging Face kaynaklarını tanıtarak başlayacaktır. Ardından, bir T5-large transformer modelini başlatacağız. Son olarak, T5'i herhangi bir belgeyi, hukuki ve kurumsal belgeler dahil, özetlemek için nasıl kullanacağımızı göreceğiz. Hugging Face'in çerçevesini tanıtarak başlayalım.

İşte birebir çeviri. Python kodları bulunmamaktadır.

Eğer bir kod örneği olsaydı, satır satır açıklama şu şekilde yapılırdı:

Örneğin aşağıdaki python kodu için:

```python
from transformers import T5Tokenizer, T5ForConditionalGeneration

# T5 modeli ve tokenizer'ı yükleme
model = T5ForConditionalGeneration.from_pretrained('t5-large')
tokenizer = T5Tokenizer.from_pretrained('t5-large')

# Giriş metnini tanımlama
input_text = "NLP summarizing tasks extract succinct parts of a text."

# Metni tokenleştirme
input_ids = tokenizer.encode("summarize: " + input_text, return_tensors="pt")

# Özetleme işlemi
output = model.generate(input_ids)

# Çıktıyı çözme
summary = tokenizer.decode(output[0], skip_special_tokens=True)

print(summary)
```

# Kod Açıklaması

1. **Gerekli Kütüphanelerin Yüklenmesi**
   ```python
from transformers import T5Tokenizer, T5ForConditionalGeneration
```
   Bu satır, `transformers` kütüphanesinden `T5Tokenizer` ve `T5ForConditionalGeneration` sınıflarını içe aktarır. `T5Tokenizer`, metni tokenlara ayırmak için kullanılırken, `T5ForConditionalGeneration` sınıfı, T5 modelini koşullu metin oluşturma görevi için yükler.

2. **T5 Modeli ve Tokenizer'ı Yükleme**
   ```python
model = T5ForConditionalGeneration.from_pretrained('t5-large')
tokenizer = T5Tokenizer.from_pretrained('t5-large')
```
   Bu satırlar, önceden eğitilmiş 't5-large' modelini ve buna karşılık gelen tokenizer'ı yükler.

3. **Giriş Metnini Tanımlama**
   ```python
input_text = "NLP summarizing tasks extract succinct parts of a text."
```
   Bu satır, özetlenecek giriş metnini tanımlar.

4. **Metni Tokenleştirme**
   ```python
input_ids = tokenizer.encode("summarize: " + input_text, return_tensors="pt")
```
   Bu satır, giriş metnini "summarize: " öneki ile birlikte tokenleştirir ve `input_ids` değişkenine atar. `return_tensors="pt"` parametresi, çıktının PyTorch tensor formatında olmasını sağlar.

5. **Özetleme İşlemi**
   ```python
output = model.generate(input_ids)
```
   Bu satır, T5 modelini kullanarak özetleme işlemini gerçekleştirir.

6. **Çıktıyı Çözme**
   ```python
summary = tokenizer.decode(output[0], skip_special_tokens=True)
```
   Bu satır, model tarafından oluşturulan `output` tensor'unu metne çevirir ve özel tokenları atlar.

7. **Özetin Yazdırılması**
   ```python
print(summary)
```
   Bu satır, oluşturulan özeti yazdırır.

---

