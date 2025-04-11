# Kelime Noktalama İşaretli Tokenization

Kelime noktalama işaretli tokenization, dizileri boşluklara ve noktalama işaretlerine göre kelimelere ayırır:

```python
# Word Punctuation Tokenization tokenizer 
tokenizer = WordPunctTokenizer()
```

Metin = "Bir ödül kazandılar! Çok sevinçliydiler."
```python
text = "They won a prize! They were overjoyed."
tokens = tokenizer.tokenize(text)
```

1. `tokenizer.tokenize(text)` : Bu satır, `text` değişkenindeki metni `WordPunctTokenizer` kullanarak tokenize eder. Yani metni kelimelere ve noktalama işaretlerine ayırır.

2. `tokens` değişkeni, tokenize edilmiş kelimeleri ve noktalama işaretlerini bir liste olarak saklar.

```python
print("Word Punctuation Tokenization:")
print(tokens)
print()
```

1. `print("Word Punctuation Tokenization:")` : Bu satır, ekrana "Word Punctuation Tokenization:" yazdırır.
2. `print(tokens)` : Bu satır, tokenize edilmiş kelimeleri ve noktalama işaretlerini ekrana yazdırır.
3. `print()` : Bu satır, boş bir satır yazdırarak çıktının daha okunabilir olmasını sağlar.

`WordPunctTokenizer` çıktısı, ayırıcılara sahip kelimeler üretir:

# Word Punctuation Tokenization Çıktısı
`['They', 'won', 'a', 'prize', '!', 'They', 'were', 'overjoyed', '.']`

Tam çeviri:
 
Kelime noktalama işaretli tokenization, dizileri boşluklara ve noktalama işaretlerine göre kelimelere ayırır: 
# Kelime Noktalama İşaretli Tokenization tokenizer 
tokenizer = WordPunctTokenizer() 
metin = "Bir ödül kazandılar! Çok sevinçliydiler." 
tokenler = tokenizer.tokenize(metin) 
print ( "Kelime Noktalama İşaretli Tokenization:" ) 
print (tokenler) 
print () 
`WordPunctTokenizer` çıktısı, ayırıcılara sahip kelimeler üretir: 
# Kelime Noktalama İşaretli Tokenization 
`['Bir', 'ödül', 'kazandılar', '!', 'Çok', 'sevinçliydiler', '.']` 

Python kodu açıklaması:
```python
from nltk.tokenize import WordPunctTokenizer

# Word Punctuation Tokenization 
tokenizer = WordPunctTokenizer()

text = "They won a prize! They were overjoyed."
tokens = tokenizer.tokenize(text)

print("Word Punctuation Tokenization:")
print(tokens)
print()

# Çıktı:
# Word Punctuation Tokenization:
# ['They', 'won', 'a', 'prize', '!', 'They', 'were', 'overjoyed', '.']
# 

# Türkçe karşılığı
print("Kelime Noktalama İşaretli Tokenization:")
print(tokenizer.tokenize("Bir ödül kazandılar! Çok sevinçliydiler."))
print()

# Çıktı:
# Kelime Noktalama İşaretli Tokenization:
# ['Bir', 'ödül', 'kazandılar', '!', 'Çok', 'sevinçliydiler', '.']
```

---

