# Treebank Tokenizer
Treebank Tokenizer, Pennsylvania Üniversitesi'nin diğer anotasyonların yanı sıra POS, sözdizimsel yapılar ve anlamsal roller içeren korpuslarına dayanmaktadır:

# Treebank Tokenization
```python
tokenizer = TreebankWordTokenizer()
```
Yukarıdaki kod satırı, `TreebankWordTokenizer` sınıfından bir tokenizer nesnesi oluşturur.

```python
text = "There aren't that many tokenizers."
```
Bu satır, tokenize edilecek metni tanımlar.

```python
tokens = tokenizer.tokenize(text)
```
Bu satır, `tokenizer` nesnesini kullanarak `text` değişkenindeki metni tokenize eder ve sonucu `tokens` değişkenine atar.

```python
print("Treebank Tokenization:")
```
Bu satır, "Treebank Tokenization:" başlığını yazdırır.

```python
print(tokens)
```
Bu satır, tokenize edilmiş metni (yani `tokens` listesini) yazdırır.

```python
print()
```
Bu satır, boş bir satır yazdırarak çıktının daha okunabilir olmasını sağlar.

TreebankWordTokenizer(), bir diziyi kelimelere ayırırken kontraksiyonlar gibi gelişmiş konuları dikkate alır:

# Treebank Tokenization:
`['There', 'are', "n't", 'that', 'many', 'tokenizers', '.']`

Çıktı olarak aşağıdaki sonuç elde edilir:
```
Treebank Tokenization:
['There', 'are', "n't", 'that', 'many', 'tokenizers', '.']
```

---

