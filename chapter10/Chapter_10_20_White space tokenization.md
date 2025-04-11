# White Space Tokenization

Boşluk tokenization, boşluk olmayan karakterleri token olarak işler:

```python
# nltk.tokenize modülünden WhitespaceTokenizer'ı içe aktar
from nltk.tokenize import WhitespaceTokenizer

# WhitespaceTokenizer örneği oluştur
tokenizer = WhitespaceTokenizer()

# Tokenize edilecek metni tanımla
text = "Tokenize this sequence of words using white space. There aren't many words."

# Metni tokenize et
tokens = tokenizer.tokenize(text)

# Sonuçları yazdır
print("White Space Tokenization:")
print(tokens)
print()
```

WhitespaceTokenizer, kelimeleri boşluk olmayan karakterleri token olarak kullanarak ayırmıştır:

# White Space Tokenization:
`['Tokenize', 'this', 'sequence', 'of', 'words', 'using', 'white', 'space.', 'There', "aren't", 'many', 'words.']`

Dikkat edin ki, TreebankWordTokenizer'ın aksine, WhitespaceTokenizer "aren't" kısaltmasını işlemedi çünkü içinde boşluk karakteri yok.

---

