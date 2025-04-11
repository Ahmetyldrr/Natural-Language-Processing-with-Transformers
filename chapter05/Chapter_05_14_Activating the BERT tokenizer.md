# Bu Bölümde Yapılacaklar
Bu bölümde, önceden eğitilmiş bir BERT tokenizer'ı başlatacağız. Bu, tokenizer'ı sıfırdan eğitmek için harcanacak zamanı kazandıracaktır.

## Tokenizer'ı Başlatma ve İlk Cümleyi Tokenleştirme
Program, küçük harf duyarlılığı olmayan (uncased) bir tokenizer seçer, etkinleştirir ve ilk tokenleştirilmiş cümleyi görüntüler:

```python
tokenizer = BertTokenizer.from_pretrained('bert-base-uncased', do_lower_case=True)
tokenized_texts = [tokenizer.tokenize(sent) for sent in sentences]
print("Tokenize the first sentence:")
print(tokenized_texts[0])
```

- `BertTokenizer.from_pretrained('bert-base-uncased', do_lower_case=True)`: 
  - Önceden eğitilmiş 'bert-base-uncased' modelini kullanarak bir BERT tokenizer'ı oluşturur.
  - `do_lower_case=True` parametresi, tüm giriş metninin küçük harfe dönüştürülmesini sağlar.

- `tokenized_texts = [tokenizer.tokenize(sent) for sent in sentences]`:
  - Listedeki her bir cümleyi (`sentences`) tokenleştirir.
  - `tokenizer.tokenize(sent)`: Belirtilen cümleyi (`sent`) tokenlere ayırır.

- `print("Tokenize the first sentence:")` ve `print(tokenized_texts[0])`:
  - İlk tokenleştirilmiş cümleyi ve başlığını yazdırır.

## Çıktı ve Açıklaması
Çıktı, sınıflandırma token'ı ve dizi segmentasyon token'ını içerir:
```
Tokenize the first sentence:
['[CLS]', 'our', 'friends', 'wo', 'n', "'", 't', 'buy', 'this', 'analysis', ',', 'let', 'alone', 'the', 'next', 'one', 'we', 'propose', '.', '[SEP]']
```

- `'[CLS]'`: Sınıflandırma token'ı. Cümlenin başında yer alır ve sınıflandırma görevleri için kullanılır.
- `'[SEP]'`: Dizi segmentasyon token'ı. Cümlenin sonunu belirtir ve birden fazla cümleyi ayırmak için kullanılır.

## İşlemin Devamı
Program şimdi verileri işleyecektir.

---

