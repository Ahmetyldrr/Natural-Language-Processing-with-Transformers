# Metin Gömmeye Giriş

Bu bölümde, metin gömmeye ilişkin temel kavramları ele alacağız: bir kitabı tokenleştirme, tokenleri gömme ve oluşturduğumuz vektör uzayını keşfetme. GitHub deposunun chapter dizinindeki Embedding_with_NLKT_Gensim.ipynb dosyasını açın. Öncelikle ihtiyacımız olan kütüphaneleri kuracağız.

İngilizce paragrafın birebir Türkçe çevirisi yukarıdaki gibidir.

Python kodları bulunmamaktadır, sadece bir metin çevirisi yapılmıştır.

Eğer bir python kodu olsaydı, satır satır açıklamaları `#` ile başlayan başlıklarla ve uygun markdown formatında açıklanacaktı. 

Örneğin, eğer aşağıdaki gibi bir python kodu olsaydı:

```python
import nltk
from gensim.models import Word2Vec

# Kitap tokenleştirme
def tokenize_book(book_text):
    tokens = nltk.word_tokenize(book_text)
    return tokens

# Tokenleri gömme
def embed_tokens(tokens):
    model = Word2Vec([tokens], vector_size=100, min_count=1)
    return model

# Vektör uzayını keşfetme
def explore_vector_space(model):
    vector = model.wv['kelime']
    print(vector)
```

Açıklamaları şu şekilde olacaktı:

# Kitap Tokenleştirme
Kitap tokenleştirme işlemi `nltk` kütüphanesinin `word_tokenize` fonksiyonu ile yapılır.
```python
def tokenize_book(book_text):
    # book_text'i tokenlere ayır
    tokens = nltk.word_tokenize(book_text)
    return tokens
```

# Tokenleri Gömme
Tokenleri gömme işlemi `gensim` kütüphanesinin `Word2Vec` sınıfı ile yapılır.
```python
def embed_tokens(tokens):
    # Tokenleri gömme modeli oluştur
    model = Word2Vec([tokens], vector_size=100, min_count=1)
    return model
```

# Vektör Uzayını Keşfetme
Vektör uzayını keşfetme işlemi, oluşturulan modelin `wv` attribute'u ile yapılır.
```python
def explore_vector_space(model):
    # 'kelime' tokeninin vektörünü yazdır
    vector = model.wv['kelime']
    print(vector)
```

---

