# İngilizce Paragrafın Türkçe Çevirisi

İşler yolunda gittiği sürece, hiç kimse önceden eğitilmiş tokenleştiriciler hakkında düşünmez. Gerçek hayatta olduğu gibi. Aracın motorunu düşünmeden yıllarca kullanabiliriz. Sonra bir gün, arabamız arıza yapar ve durumu açıklamak için nedenleri bulmaya çalışırız. Önceden eğitilmiş tokenleştiricilerde de aynı şey olur. Bazen sonuçlar beklediğimiz gibi olmaz. Örneğin, bazı kelime çiftleri, Bağımsızlık Bildirgesi metni bağlamında birbirine uymaz, Şekil 10.2'de görüldüğü gibi: 

Şekil 10.2: Tokenleştiricilerin yanlış hesapladığı ve Kalite Kontrol (QC) sırasında tespit edilen kelime çiftleri

Şekil 10.2'de gösterilen örnekler Amerikan Bağımsızlık Bildirgesi, Haklar Bildirgesi ve İngiliz Magna Carta'dan alınmıştır: kek ve bölümler birbirine uymaz, ancak bir tokenleştirici bunların yüksek bir kosinüs benzerlik değerine sahip olduğunu hesaplar. Özgürlük, örneğin, ifade özgürlüğüne atıfta bulunur. Telif hakkı, ücretsiz e-kitabın editörü tarafından yazılan nota atıfta bulunur. ödemek ve fatura günlük İngilizcede birbirine uyar. Çok anlamlılık, bir kelimenin birkaç anlamı olabilmesidir. Örneğin, Fatura ödenecek bir miktarı ifade eder, aynı zamanda Haklar Bildirgesi'ne de atıfta bulunur. Sonuç kabul edilebilir, ancak tamamen şans eseri olabilir. Devam etmeden önce, bazı noktaları açıklığa kavuşturmak için bir an duralım. QC, kalite kontrolü ifade eder. Her stratejik kurumsal projede, QC zorunludur. Çıktının kalitesi kritik bir projenin hayatta kalmasını belirleyecektir. Proje stratejik değilse, bazen hatalar kabul edilebilir. Stratejik bir projede, birkaç hata bile risk yönetimi denetiminin müdahalesine neden olabilir ve projenin devam ettirilip ettirilmeyeceğine veya terk edilip edilmeyeceğine karar verilebilir. Kalite kontrol ve risk yönetimi perspektiflerinden bakıldığında, alakasız veri kümelerini (yani çok fazla işe yaramaz kelime veya kritik kelimelerin eksikliği) tokenleştirmek, embedding algoritmalarını karıştırır ve "zayıf sonuçlar" üretir. Bu nedenle, bu bölümde "tokenleştirme" kelimesini gevşek bir şekilde kullanıyorum, birinin diğerine olan etkisi nedeniyle bazı embeddingleri dahil ediyorum. Stratejik bir AI projesinde, "zayıf sonuçlar" dramatik bir sonuca sahip tek bir hata olabilir (özellikle tıbbi alanda, uçak veya roket montajı veya diğer kritik alanlarda). 

Chapter 2'de oluşturduğumuz positional_encoding.ipynb tabanlı Open Tokenizers.ipynb dosyasını açın. Sonuçlar, Word2Vec algoritmalarının stokastik doğası nedeniyle bir çalışmadan diğerine değişebilir. Ön koşulların kurulu ve içe aktarıldığından emin olun: 
```python
!pip install gensim
import nltk
nltk.download('punkt')
import math
import numpy as np
from nltk.tokenize import sent_tokenize, word_tokenize
import gensim
from gensim.models import Word2Vec
import numpy as np
from sklearn.metrics.pairwise import cosine_similarity
import matplotlib.pyplot as plt
import warnings
warnings.filterwarnings(action='ignore')
```
Şimdi örnek veri setimizi yükleyelim: 
#1. Colab dosya yöneticisini kullanarak text.txt dosyasını yükleyin
#2. GitHub'dan dosyayı indirin 
```bash
!curl -L https://raw.githubusercontent.com/Denis2054/Transformers-for-NLP-and-Computer-Vision-3rd-Edition/master/Chapter10/text.txt --output "text.txt"
```
text.txt veri setimiz Amerikan Bağımsızlık Bildirgesi, Haklar Bildirgesi, Magna Carta, Immanuel Kant'ın eserleri ve diğer metinleri içerir. Şimdi text.txt dosyasını tokenleştireceğiz ve bir Word2Vec modelini eğiteceğiz: 
```python
#'text.txt' dosyasını oku
sample = open("text.txt", "r")
s = sample.read() 
# escape karakterlerini işle
f = s.replace("\n", " ")
data = [] 
# Cümle ayrıştırma
for i in sent_tokenize(f):
    temp = [] 
    # Cümleyi kelimelere ayır
    for j in word_tokenize(i):
        temp.append(j.lower())
    data.append(temp)

# Skip Gram modelini oluştur
model2 = gensim.models.Word2Vec(data, min_count=1, size=512, window=5, sg=1)
print(model2)
```
`window=5` ilginç bir parametredir. Giriş cümlesinde mevcut kelime ile tahmin edilen kelime arasındaki mesafeyi sınırlar. `sg=1` atlama-gram eğitim algoritmasının kullanıldığı anlamına gelir. Çıktı, kelime haznesinin boyutunun 10816, embeddinglerin boyutluluğunun 512 ve öğrenme oranının alpha=0.025 olarak ayarlandığını gösterir: 
```
Word2Vec<vocab=3291, vector_size=512, alpha=0.025>
```
Artık bir kelime temsil modeli ve embeddinglere sahibiz ve `similarity(word1,word2)` adında bir kosinüs benzerlik fonksiyonu oluşturabiliriz. Fonksiyona `word1` ve `word2` göndereceğiz ve bunlar arasındaki kosinüs benzerlik değerini döndürecektir. Değer ne kadar yüksek olursa, benzerlik o kadar yüksek olur. Fonksiyon önce bilinmeyen kelimeleri, `[unk]`, tespit edecek ve bir mesaj gösterecektir: 
```python
def similarity(word1, word2):
    cosine = False  # varsayılan değer
    try:
        a = model2[word1]
        cosine = True
    except KeyError: 
        # KeyError istisnası ortaya çıkar
        print(word1, ":[unk] key not found in dictionary") 
        # False ima edilir
    try:
        b = model2[word2] 
        # a=True ima edilir
    except KeyError: 
        # KeyError istisnası ortaya çıkar
        cosine = False 
        # hem a hem de b doğru olmalı
        print(word2, ":[unk] key not found in dictionary")

    # Kosinüs benzerliği sadece cosine==True ise hesaplanır
    if (cosine == True):
        b = model2[word2] 
        # kosinüs benzerliğini hesapla
        dot = np.dot(a, b)
        norma = np.linalg.norm(a)
        normb = np.linalg.norm(b)
        cos = dot / (norma * normb)
        aa = a.reshape(1, 512)
        ba = b.reshape(1, 512) 
        # print("Word1",aa) 
        # print("Word2",ba)
        cos_lib = cosine_similarity(aa, ba) 
        # print(cos_lib,"word similarity")
    if (cosine == False): cos_lib = 0; 
    return cos_lib
```
Fonksiyon `cos_lib` değerini, hesaplanan kosinüs benzerlik değerini döndürecektir. Şimdi altı vakadan geçeceğiz. Veri setimizi `text.txt` olarak adlandıracağız. Durum 0 ile başlayalım. 

## Kod Açıklaması

1. `!pip install gensim` : gensim kütüphanesini kurar.
2. `import nltk` : nltk kütüphanesini içe aktarır.
3. `nltk.download('punkt')` : nltk'nin punkt paketini indirir.
4. `sent_tokenize(f)` : metni cümlelere ayırır.
5. `word_tokenize(i)` : cümleyi kelimelere ayırır.
6. `gensim.models.Word2Vec(data, min_count=1, size=512, window=5, sg=1)` : Word2Vec modelini oluşturur.
7. `similarity(word1, word2)` : iki kelime arasındaki kosinüs benzerliğini hesaplar.

## Notlar

* Kod, Colab ortamında çalıştırılmak üzere tasarlanmıştır.
* `text.txt` dosyası, Amerikan Bağımsızlık Bildirgesi, Haklar Bildirgesi, Magna Carta, Immanuel Kant'ın eserleri ve diğer metinleri içerir.
* Word2Vec modeli, Skip Gram algoritması kullanılarak eğitilmiştir.

---

