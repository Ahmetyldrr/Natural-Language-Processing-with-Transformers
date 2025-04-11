# Eğitilmiş Tokenizer'ı Yükleme

Şimdi eğitilmiş tokenizer'ımızı yüklemeye hazırız, bu tokenizer RobertaTokenizer.from_pretrained() içinde önceden eğitilmiş tokenizer'ımızdır: 
```python
from transformers import RobertaTokenizer
tokenizer = RobertaTokenizer.from_pretrained("./KantaiBERT", max_length=512)
```
Şimdi eğitilmiş tokenizer'ımızı yüklediğimize göre, sıfırdan bir RoBERTa modeli başlatacağız.

Satır satır açıklama:

1. `from transformers import RobertaTokenizer`: Bu satır, `transformers` kütüphanesinden `RobertaTokenizer` sınıfını içe aktarır. `RobertaTokenizer`, RoBERTa modelinin metinleri tokenlara ayırmak için kullandığı bir tokenleştiricidir.
2. `tokenizer = RobertaTokenizer.from_pretrained("./KantaiBERT", max_length=512)`: Bu satır, `./KantaiBERT` dizininde önceden eğitilmiş `RobertaTokenizer` modelini yükler ve `tokenizer` değişkenine atar. 
   - `./KantaiBERT`: Yüklenmek istenen önceden eğitilmiş modelin dizinidir.
   - `max_length=512`: Tokenleştirme sırasında metinlerin maksimum uzunluğunu belirler. Bu örnekte, maksimum uzunluk 512 olarak ayarlanmıştır. 

Bu kod, önceden eğitilmiş bir RoBERTa tokenizer'ını yüklemek için kullanılır. Yüklenen tokenizer daha sonra metinleri işlerken kullanılabilir.

---

