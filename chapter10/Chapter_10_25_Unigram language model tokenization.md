# Unigram Dil Modeli Tokenleştirme
Unigram dil modeli tokenleştirme Google tarafından geliştirilmiştir. Alt kelime birimleri kullanarak eğitim alır. Nadir kullanılan birimleri düşürür. Unigram dil modeli tokenleştirme deterministik değildir. Bu nedenle, aynı girdi için her zaman aynı tokenleri üretmez. Tersine, BPE deterministiktir ve bir girdi için aynı çıktı tokenlerini üretecektir.

## Örnek Uygulama
Aşağıdaki örnekte, küçük bir eğitim oturumunu bir cümle örneğinde çalıştırıyoruz ve ardından bir cümleyi tokenleştiriyoruz.

### Gerekli Modüllerin İçe Aktarılması
İlk olarak, gerekli modülleri içe aktarıyoruz:
```python
from tokenizers import Tokenizer
from tokenizers.models import Unigram
from tokenizers.trainers import UnigramTrainer
from tokenizers.pre_tokenizers import Whitespace
```
*   `tokenizers` kütüphanesinden `Tokenizer` sınıfını içe aktarıyoruz. Bu sınıf, tokenleştirme işlemlerini gerçekleştirmek için kullanılır.
*   `tokenizers.models` modülünden `Unigram` sınıfını içe aktarıyoruz. Bu sınıf, Unigram dil modeli tokenleştirme işlemlerini gerçekleştirmek için kullanılır.
*   `tokenizers.trainers` modülünden `UnigramTrainer` sınıfını içe aktarıyoruz. Bu sınıf, Unigram dil modeli tokenleştirme modelini eğitmek için kullanılır.
*   `tokenizers.pre_tokenizers` modülünden `Whitespace` sınıfını içe aktarıyoruz. Bu sınıf, boşluk karakterlerine göre ön tokenleştirme işlemlerini gerçekleştirmek için kullanılır.

### Örnek Korpus Tanımlama
Ardından, örnek bir korpus tanımlıyoruz:
```python
# Örnek bir korpus tanımla
corpus = [
    "Subword tokenizers break text sequences into subwords.",
    "This sentence is another part of the corpus.",
    "Tokenization is the process of breaking text down into smaller units.",
    "These smaller units can be words, subwords, or even individual characters.",
    "Transformer models often use subword tokenization."
]
```
*   `corpus` adlı bir liste tanımlıyoruz ve bu liste içerisinde örnek cümlelerimizi saklıyoruz.

### Tokenizer Eğitimi
Boşluk karakterlerine göre ön tokenleştirme yapan bir Unigram tokenizer modeli eğitiyoruz:
```python
# Unigram tokenizer modeli oluştur
tokenizer = Tokenizer(Unigram([]))

# Ön tokenleştirici ekle
tokenizer.pre_tokenizer = Whitespace()

# Tokenizer modelini eğit
trainer = UnigramTrainer(vocab_size=5000)  # İstenen kelime haznesi boyutunu ayarlayın
tokenizer.train_from_iterator(corpus, trainer)
```
*   `Tokenizer` sınıfından bir örnek oluşturuyoruz ve Unigram dil modeli tokenleştirme işlemlerini gerçekleştirmek için `Unigram` sınıfını kullanıyoruz.
*   `pre_tokenizer` özelliğini `Whitespace` sınıfına ayarlayarak boşluk karakterlerine göre ön tokenleştirme işlemlerini gerçekleştiriyoruz.
*   `UnigramTrainer` sınıfından bir örnek oluşturuyoruz ve `vocab_size` parametresini 5000 olarak ayarlayarak kelime haznesi boyutunu belirliyoruz.
*   `train_from_iterator` metodu ile `corpus` listesindeki cümleleri kullanarak tokenizer modelini eğitiyoruz.

### Cümle Tokenleştirme
Son olarak, hedef cümleyi tokenleştiriyoruz:
```python
# Orijinal cümleyi tokenleştir
output = tokenizer.encode("Subword tokenizers break text sequences into subwords.")
print(output.tokens)
```
*   `encode` metodu ile hedef cümleyi tokenleştiriyoruz.
*   `tokens` özelliği ile tokenleştirilmiş cümleyi alıyoruz ve yazdırıyoruz.

Çıktı:
```python
['S', 'ubword', 'tokeniz', 'er', 's', 'break', 'te', 'x', 't', 'se', 'q', 'u', 'ence', 's', 'in', 'to', 'subword', 's', '.']
```
Görüldüğü gibi, çıktı kelimeler veya cümleler değil, alt kelimelerdir.

---

