# Model Dosyalarını Kaydetme

Aşağıdaki kod, modelin dosyalarını kaydedecektir:
```python
# Modelinizi ve tokenizer'ı kaydetmek için bir dizin belirtin
save_directory = "/content/model"

# Eğer modeliniz DataParallel ile sarılmışsa, orijinal modele .module kullanarak erişin ve sonra kaydedin
if isinstance(model, torch.nn.DataParallel):
    model.module.save_pretrained(save_directory)
else:
    model.save_pretrained(save_directory)

# Tokenizer'ı kaydedin
tokenizer.save_pretrained(save_directory)
```
`/content/model` dizininde kaydedilen dosyalar şunlardır:
- `tokenizer_config.json`: Tokenizer'a özgü yapılandırma ayrıntıları.
- `special_tokens_map.json`: Özel tokenler için eşlemeler.
- `vocab.txt`: Tokenizer'ın tanıyabileceği tokenlerin sözlüğü.
- `added_tokens.json`: Tokenizer'ın ilk oluşturulmasından sonra eklenen tokenler.

PyTorch'da çoklu-GPU eğitimi için bir model DataParallel ile sarıldığında, orijinal model DataParallel nesnesinin bir özelliği haline gelir.

Colab ortamındaki dosyaların oturum sona erdiğinde silineceğini unutmayın. Kaydedilen model büyük olabilir. Bu durumda, bir çözüm Google Drive'ı bağlamaktır:
```python
from google.colab import drive
drive.mount('/content/drive')
```
Daha sonra `/content/model` dizinindeki dosyaları Google Drive'a kaydedin. Dosyalar başka bir oturumda yüklenebilir, aşağıdaki kod parçasında gösterildiği gibi:
```python
from transformers import BertTokenizer, BertForSequenceClassification

# Model ve tokenizer'ın kaydedildiği dizin
load_directory = "/content/model/"
```
Sonraki adım, eğitilmiş modelle etkileşimde bulunmak için bir arayüz oluşturmaktır.

**Kod Açıklamaları:**

1. `save_directory = "/content/model"`: Model ve tokenizer'ı kaydetmek için bir dizin belirler.
2. `if isinstance(model, torch.nn.DataParallel):`: Modelin DataParallel ile sarılıp sarılmadığını kontrol eder.
3. `model.module.save_pretrained(save_directory)`: Model DataParallel ile sarılmışsa, orijinal modele `.module` kullanarak erişir ve kaydeder.
4. `model.save_pretrained(save_directory)`: Model DataParallel ile sarılmamışsa, modeli doğrudan kaydeder.
5. `tokenizer.save_pretrained(save_directory)`: Tokenizer'ı kaydeder.
6. `from google.colab import drive`: Google Colab'da Google Drive'ı kullanmak için gerekli kütüphaneyi içe aktarır.
7. `drive.mount('/content/drive')`: Google Drive'ı Colab'a bağlar.
8. `from transformers import BertTokenizer, BertForSequenceClassification`: BertTokenizer ve BertForSequenceClassification'ı içe aktarır.

---

