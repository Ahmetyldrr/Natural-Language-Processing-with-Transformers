# Eğitilmiş Tokenizer Dosyalarını Yükleme

Önceden eğitilmiş tokenizer dosyalarını yükleyebilirdik. Ancak, kendi tokenizer'ımızı eğittik ve şimdi dosyaları yüklemeye hazırız:

```python
from tokenizers.implementations import ByteLevelBPETokenizer
from tokenizers.processors import BertProcessing
tokenizer = ByteLevelBPETokenizer(
    "./KantaiBERT/vocab.json",
    "./KantaiBERT/merges.txt",
)
```

*   Yukarıdaki kodda `ByteLevelBPETokenizer` sınıfı kullanılarak bir tokenizer nesnesi oluşturulur.
*   `vocab.json` ve `merges.txt` dosyaları tokenizer'ı eğitmek için kullanılır.

## Tokenizer'ı Kullanma

Tokenizer bir diziyi kodlayabilir:

```python
tokenizer.encode("The Critique of Pure Reason.").tokens
```

*   `encode` methodu bir diziyi tokenlara ayırır.
*   `tokens` attribute'u tokenları bir liste olarak döndürür.

"The Critique of Pure Reason" dizisi aşağıdaki tokenlara ayrılır:

`['The', 'ĠCritique', 'Ġof', 'ĠPure', 'ĠReason', '.']`

Bu dizideki token sayısını da görebiliriz:

```python
tokenizer.encode("The Critique of Pure Reason.")
```

*   `encode` methodu bir `Encoding` nesnesi döndürür.
*   `num_tokens` attribute'u token sayısını gösterir.

Çıktı, dizide altı token olduğunu gösterir:

`Encoding(num_tokens=6, attributes=[ids, type_ids, tokens, offsets, attention_mask, special_tokens_mask, overflowing])`

## Tokenizer'ı BERT Modeline Uydurma

Tokenizer şimdi tokenları bu not defterinde kullanılan BERT modeli varyantına uyacak şekilde işler.

```python
tokenizer._tokenizer.post_processor = BertProcessing(
    ("</s>", tokenizer.token_to_id("</s>")),
    ("<s>", tokenizer.token_to_id("<s>")),
)
```

*   `post_processor` attribute'u tokenlara işleme sonrası işlemler uygulamak için kullanılır.
*   `BertProcessing` sınıfı BERT modeli için özel tokenlar ekler.

```python
tokenizer.enable_truncation(max_length=512)
```

*   `enable_truncation` methodu dizileri belirli bir uzunluğa kadar kısaltmak için kullanılır.

## İşlem Sonrası Diziyi Kodlama

```python
tokenizer.encode("The Critique of Pure Reason.")
```

*   `encode` methodu işlem sonrası diziyi kodlar.

Çıktı, şimdi sekiz token olduğunu gösterir:

`Encoding(num_tokens=8, attributes=[ids, type_ids, tokens, offsets, attention_mask, special_tokens_mask, overflowing])`

Eklenen tokenları görmek için:

```python
tokenizer.encode("The Critique of Pure Reason.").tokens
```

*   `tokens` attribute'u tokenları bir liste olarak döndürür.

Çıktı, başlangıç ve bitiş tokenlarının eklendiğini gösterir:

`['<s>', 'The', 'ĠCritique', 'Ġof', 'ĠPure', 'ĠReason', '.', '</s>']`

## Eğitim Verisini Hazırlama

Eğitim modeli için veri artık eğitilmeye hazırdır.

## Sistem Bilgilerini Kontrol Etme

Şimdi not defterini çalıştırdığımız makinenin sistem bilgilerini kontrol edeceğiz.

---

