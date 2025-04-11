# Bölüm: Dikkat Kafalarının Çıktı Skorlarının Analizi

Bu bölümde, 3. Bölüm'de, "Emergent vs Downstream Tasks: The Unseen Depths of Transformers" başlığı altında başlatılan dikkat kafalarının çıktı skorlarını analiz etmek için etkileşimli bir arayüz uygulayacağız. Program ilk olarak Hugging Face kütüphanesini kurar:

# Hugging Face Transformers Kütüphanesini Kurma
```python
!pip install transformers
```
BertTokenizer ve BertModel'i kullanacağız:
```python
from transformers import BertTokenizer, BertModel
```
Şimdi, etkileşimli formu ekliyoruz ve bir cümle giriyoruz:
```python
%%capture 
input_text = "The output shows the attention values" #@param {type:"string"}
print(input_text)
```
Çıktı, girdiğimiz string değeridir. Hücreleri çalıştırdıktan sonra, bu forma geri dönüp keşfetmek istediğiniz herhangi bir diziyi girebilirsiniz.

Kod şimdi tokenizer ve modeli tanımlıyor ve girdi metnini tokenleştirerek başlıyor:
```python
# BERT Modeli ve Tokenizer'ı Yükleme
model_name = 'bert-base-uncased'
tokenizer = BertTokenizer.from_pretrained(model_name)
model = BertModel.from_pretrained(model_name, output_attentions=True)

# Girdi Metnini Tokenleştirme
tokens = tokenizer.tokenize(input_text)
input_ids = tokenizer.convert_tokens_to_ids(tokens)
```
Şimdi dikkat çıktılarına erişiyoruz:
```python
# Dikkat Matrisini Alma
inputs = tokenizer.encode_plus(input_text, return_tensors='pt')
input_ids = inputs['input_ids']
attention_mask = inputs['attention_mask']
outputs = model(input_ids, attention_mask=attention_mask)
attentions = outputs.attentions
```
Artık dikkat kafalarının çıktısını akış olarak alabiliriz.

### Kod Açıklamaları

1. `!pip install transformers`: Hugging Face transformers kütüphanesini kurar.
2. `from transformers import BertTokenizer, BertModel`: BertTokenizer ve BertModel sınıflarını transformers kütüphanesinden import eder.
3. `%%capture`: Jupyter Notebook'ta hücrelerin çıktısını yakalamak için kullanılır.
4. `input_text = "The output shows the attention values" #@param {type:"string"}`: Kullanıcıdan string tipi bir girdi alır.
5. `print(input_text)`: Kullanıcının girdiği metni yazdırır.
6. `model_name = 'bert-base-uncased'`: Kullanılacak BERT modelinin adını belirler.
7. `tokenizer = BertTokenizer.from_pretrained(model_name)`: Belirtilen model adına göre bir BertTokenizer örneği oluşturur.
8. `model = BertModel.from_pretrained(model_name, output_attentions=True)`: Belirtilen model adına göre bir BertModel örneği oluşturur ve dikkat çıktılarını döndürmesini sağlar.
9. `tokens = tokenizer.tokenize(input_text)`: Girdi metnini tokenleştirir.
10. `input_ids = tokenizer.convert_tokens_to_ids(tokens)`: Tokenleştirilen metni input_ids formatına çevirir.
11. `inputs = tokenizer.encode_plus(input_text, return_tensors='pt')`: Girdi metnini encode eder ve PyTorch tensorları olarak döndürür.
12. `outputs = model(input_ids, attention_mask=attention_mask)`: Modeli çalıştırır ve çıktılar ile dikkat maskesini alır.
13. `attentions = outputs.attentions`: Modelin dikkat çıktılarını alır.

---

