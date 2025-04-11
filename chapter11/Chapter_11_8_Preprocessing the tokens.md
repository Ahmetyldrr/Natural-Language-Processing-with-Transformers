# Bu Bölümün Amacı
Bu bölümün amacı, tokenleri üç yöntemle ön işlemden geçirmektir: 

1. ## Tokenleri Küçük Harfe Çevirme
Tokenleri küçük harfe çevirmek, kelime hazinesindeki token sayısını azaltacaktır. Örneğin, "Talking" ve "talking" bu stratejide yinelenenlerdir. "Talking"i "talking"e çevirmek yinelenenleri ortadan kaldırır.

2. ## Lemmatization (Köklendirme)
Lemmatization, kelimeleri anlamsal anlamlarını korumak için temel lemma (temel form)larına indirgeyecektir. Örneğin, "running" "run" olacaktır. Bu yaklaşımda, "ing" soneki bu bölümdeki kelime hazinesinin bir parçası olmayacaktır. Bu örnekte, bir kök bulma yöntemi uygulamadık. Kök bulma, kural tabanlıdır ve önekleri ve sonekeleri kaldırır. Elde edilen kök geçerli bir kelime olmayabilir. Örneğin, "happiness" "ness" kaldırıldığında "happi" üretebilir. Bu durumda, tüm ana kelimelerin anlamsal anlamını korumak istiyoruz.

3. ## Stop Words (Durdurma Kelimeleri)
Stop words, "ve" ve "the" gibi filtrelenecek ortak kelimelerdir. Stop words'leri filtreleme seçimi her projeye bağlıdır.

Bu üç işlevi uygulamak için, önce WordNet'i ve İngilizce stopwords listesini içeren stopwords'leri indiriyoruz:
```python
nltk.download('wordnet')
nltk.download('stopwords')
```
WordNet, lemmatization için uygulanabilen bir İngilizce kelime hazinesidir. Şimdi stopwords, WordNetLemmatizer ve tokenleri işlemek için string modülünü içe aktarıyoruz:
```python
from nltk.corpus import stopwords
from nltk.stem import WordNetLemmatizer
import string
```
Program şimdi ihtiyacımız olan ön işleme işlevlerini uyguluyor:
```python
stop_words = set(stopwords.words('english'))
lemmatizer = WordNetLemmatizer()
tokens = [lemmatizer.lemmatize(token.lower()) for token in tokens if token.lower() not in stop_words and token not in string.punctuation]
```
Bu kod satırında:
- `stop_words` değişkenine İngilizce stopwords'ler atanıyor.
- `lemmatizer` değişkenine WordNetLemmatizer nesnesi atanıyor.
- `tokens` listesi, aşağıdaki işlemleri içeren bir liste kavraması kullanılarak güncelleniyor:
  - Her token küçük harfe çevriliyor (`token.lower()`).
  - Küçük harfe çevrilmiş token, stop words'ler listesinde yoksa ve noktalama işaretleri listesinde yoksa (`string.punctuation`), işleme devam ediyor.
  - Lemmatizer kullanılarak token köklendiriliyor (`lemmatizer.lemmatize(...)`).

Program, tokenleri küçük harfe çevirdi, lemmatization görevlerini gerçekleştirdi ve stop words'leri filtreledi.

Şimdi işlenmiş kelime hazinemizdeki token sayısını bulalım:
```python
print(len(tokens))
```
Token sayısı 23.605 ham tokenden 9.781 anlamlı tokene düşürüldü: 9781

Elde edilen tokenler kelimelerdir çünkü bir kelime tokenizer kullandık, kelimeleri minimal alt parçalara ayıran bir bayt düzeyinde tokenizer değil.

Tokenization işlemi, görevlerimiz için anlamlı olmayan bilgileri filtreledi. Ancak, yinelenenler kelime hazinesinde kalabilir. Elde edilen benzersiz tokenleri bulabilir, sayabilir ve görüntüleyebiliriz:
```python
unique_tokens = set(tokens)
print(len(unique_tokens))
```
Önce sayalım:
```python
print(unique_tokens)
```
Çıktı, yinelenenleri filtreler ve anlamlı tokenlerin benzersiz bir kümesini üretir: 3843

Program şimdi işlenmiş tokenlerin kelime hazinesini görüntüler:
```python
print(unique_tokens)
```
Kelime hazinesindeki kelimelerin listesi aşağıdaki alıntıda gösterildiği gibi görüntülenir:
```python
{'ofpoetry.i', 'hamper', 'warmerimmediately', 'convinced', 'agreeably', 'affair', 'thebody', 'trust', 'dependent',…}
```
Token işleme işlevi kabul edilebilir bir çıktı üretti, ancak bazı yanlışlıklar kaldı. Kelime hazinesini %100 mükemmel olana kadar ön işlemeye devam edebiliriz, ancak bu bölümdeki örnek için yeterli bilgiye sahibiz.

Gensim ve Word2Vec ile kelime hazinesini gömmek için `unique_tokens` kelime hazinesini kullanacağız:
```python
tokens = unique_tokens
# print(len(tokens))
```
Artık kelime hazinesini Gensim ve Word2Vec ile gömebiliriz.

---

