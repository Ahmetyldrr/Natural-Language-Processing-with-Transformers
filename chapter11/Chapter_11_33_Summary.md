# Bu Bölümün Çevirisi

Bu bölüm, bizi hızlı tasarım dan hızlı mühendisliğine götürdü. Yaratıcı hızlı ifadeler icat etmek, son kullanıcılara yardımcı olacaktır. Bir modelin uygulama şeklini özelleştirmek, modelin sınırları aşılamayacak kadar zor hale geldiğinde gerekli olur. Bir modeli daha iyi hale getirmek, günlük gelen olaylara cevap vermesi gereken bir sistem için soru-cevap sorununu çözmeyebilir. Bir modeli her gün daha iyi hale getiremeyiz. Bu gibi durumlarda, embedding tabanlı bir arama sistemi gibi alternatifler bulmalıyız. Embedding tabanlı arama, RAG'ı uygulamak için birçok olasılıktan biridir.

## İlk Adım: Metin Embedding'lerinin Temellerini Gözden Geçirmek

İlk adımımız, Doğal Dil İşleme Kiti ve Gensim ile metin embedding'lerinin temellerini gözden geçirmekti. Réne Descartes'ın bir metnini tokenize ettik ve sonra tokenleri ön işleme tabi tuttular. Daha sonra tokenleri Gensim'in Word2Vec modülü ile embeddingledik. Son olarak, Gensim'in vektör uzayını TensorFlow Projector ile keşfettik.

## İkinci Adım: Embedding Tabanlı Arama ile Soru-Cevap Sistemi Uygulamak

İkinci adımımız, embedding tabanlı bir arama ile bir soru-cevap sistemi uygulamak oldu. GPT-3.5-turbo örneğini çalıştırarak başladık, ancak Eylül 2021 kesim tarihli veri kümesi nedeniyle 2022 Olimpiyatları hakkında soruları cevaplayamadı. Daha sonra sisteme bir bilgi tabanı ekledik ve OpenAI API'sine gönderilen istekteki mesajda bilgi ekledik. Daha sonra, arama işlevlerini uygulamak için gömülü bir veri kümesi kullandık.

## Üçüncü Adım: Amazon Fine Food Reviews Veri Kümesinde Embedding Modeli Çalıştırmak

Üçüncü ve son adımımız, Kaggle'dan indirdiğimiz Amazon Fine Food Reviews veri kümesinde bir embedding modeli çalıştırmak oldu. Daha sonra, duygu analizi için bir kümeleme algoritması kullanarak bir sor-sorgula sistemi uyguladık. Artık süreci anlıyorsunuz. Veri kümelerini kendi veri kümelerinizle ve modelleri kendi seçtiğiniz modellerle değiştirebilirsiniz. Yenilikçi yöntemlerle etkili bir soru-cevap sistemi mühendisliği yaptık.

Bu bölümde Python kodları kullanılmamıştır. Ancak, eğer kodlar kullanılsaydı, satır satır açıklamalar aşağıdaki gibi olurdu:

Örneğin, tokenization işlemi için kullanılan Python kodları:
```python
import nltk
from nltk.tokenize import word_tokenize

text = "Réne Descartes'ın bir metni"
tokens = word_tokenize(text)
print(tokens)
```
*   `import nltk`: Doğal Dil İşleme Kiti (NLTK) kütüphanesini içe aktarır.
*   `from nltk.tokenize import word_tokenize`: NLTK'nın `tokenize` modülünden `word_tokenize` fonksiyonunu içe aktarır.
*   `text = "Réne Descartes'ın bir metni"`: Tokenize edilecek metni tanımlar.
*   `tokens = word_tokenize(text)`: Metni tokenize eder ve tokenleri `tokens` değişkenine atar.
*   `print(tokens)`: Tokenleri yazdırır.

Gensim'in Word2Vec modülü ile embedding işlemi için kullanılan Python kodları:
```python
from gensim.models import Word2Vec

# Tokenize edilmiş metinleri içeren bir liste oluştur
sentences = [["Bu", "bir", "örnek", "metin"], ["Bu", "başka", "bir", "örnek"]]

# Word2Vec modelini oluştur
model = Word2Vec(sentences, vector_size=100, window=5, min_count=1)

# Bir kelimenin vektörünü al
vector = model.wv["örnek"]
print(vector)
```
*   `from gensim.models import Word2Vec`: Gensim'in `Word2Vec` modelini içe aktarır.
*   `sentences = [["Bu", "bir", "örnek", "metin"], ["Bu", "başka", "bir", "örnek"]]`: Tokenize edilmiş metinleri içeren bir liste oluşturur.
*   `model = Word2Vec(sentences, vector_size=100, window=5, min_count=1)`: Word2Vec modelini oluşturur.
*   `vector = model.wv["örnek"]`: "örnek" kelimesinin vektörünü alır.
*   `print(vector)`: Vektörü yazdırır.

---

