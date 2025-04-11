# Metni Tokenleştirme

Metni tokenleştirme, işleyeceğimiz bilginin en alt seviyesine geri dönmemizi sağlar. Embedding'e yol açan sürecin aşağıdan yukarıya doğru tam olarak anlaşılması esastır. Bölüm 6'da, RoBERTa aracılığıyla Sıfırdan bir Transformer Eğitimi'nde, 3. Adım: Bir tokenizer eğitimi bölümünde, kelimeleri temel biçimleri, önekleri ve sonekleri ne olursa olsun minimal bileşenlere ayıran bir bayt düzeyinde tokenleştirici eğittik. Bu bölümde, bir kelime tokenleştirici kullanacağız. Bayt düzeyinde bir tokenleştirici, bireysel bayt düzeyinde çalışırken, NLTK'den word_tokenize işlevi metni bireysel kelimelere ayırır. Her iki yaklaşım da farklı amaçlara hizmet eder ve farklı dilsel ayrıntı düzeylerinde çalışır.

İlk olarak, bir kelime tokenleştirici içe aktaracağız, hazırladığımız kitabı tokenleştireceğiz ve tokenleri sayacağız:

```python
from nltk.tokenize import word_tokenize
tokens = word_tokenize(descartes_book)
print(len(tokens))
```

Bu kodun çıktısı, sözlükteki ilk token sayısını gösterir: 23605. Şimdi, anlamlı tokenleri çıkarmak için tokenleri ön işleme tabi tutacağız.

# Kodun Açıklaması

1. `from nltk.tokenize import word_tokenize`: Bu satır, NLTK kütüphanesinin tokenize modülünden word_tokenize işlevini içe aktarır. Bu işlev, metni bireysel kelimelere ayırmak için kullanılır.

2. `tokens = word_tokenize(descartes_book)`: Bu satır, `descartes_book` değişkeninde depolanan metni word_tokenize işlevi kullanarak tokenleştirir ve sonuçları `tokens` değişkenine atar.

3. `print(len(tokens))`: Bu satır, `tokens` listesinin uzunluğunu, yani token sayısını yazdırır.

Bu kod, Descartes'ın kitabını kelimelere ayırarak tokenleştirir ve elde edilen token sayısını gösterir.

---

