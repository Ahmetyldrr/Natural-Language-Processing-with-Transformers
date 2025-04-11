# Prototip İçin Veri Ön İşleme

Bir prototip için, tweetleri ön işlemden geçirebiliriz. Veri setinin ham formatı, bir dil modelini önceden eğitmek için gerek olmayan gürültü içerir. Bunu, DataFrame'in ilk birkaç satırını yükleyerek ve yazdırarak görebiliriz:

```python
import pandas as pd 
# Veri setini yükle
df = pd.read_csv('/content/twcs/twcs.csv') 
# Veriyi anlamak için ilk birkaç satırı kontrol et
print(df.head())
```

Çıktı, bu prototip için tweetlerin kelimeleri arasındaki ilişkiyi anlamak için modele gerek olmayan bilgiler içerir:
```
   tweet_id   author_id  inbound                      created_at  \
0         1  sprintcare    False  Tue Oct 31 22:10:47 +0000 2017   
1         2      115712     True  Tue Oct 31 22:11:45 +0000 2017   
2         3      115712     True  Tue Oct 31 22:08:27 +0000 2017   
3         4  sprintcare    False  Tue Oct 31 21:54:49 +0000 2017   
4         5      115712     True  Tue Oct 31 21:49:35 +0000 2017   
                                                text response_tweet_id  \
0  @115712 I understand. I would like to assist y...                 2   
1      @sprintcare and how do you propose we do that               NaN   
2  @sprintcare I have sent several private messag...                 1   
3  @115712 Please send us a Private Message so th...                 3   
4                                 @sprintcare I did.                 4
```

Bu alakasız bilgilerin üstesinden gelmenin en etkili yolu, alfabe ve bazı noktalama işaretleri gibi ihtiyacımız olan karakterleri içeren kelimeleri çıkarmaktır. Bu hücreye kadar olan hücreleri çalıştırın ve inceleyin:

```python
import re 
def filter_tweet(tweet):
    # Sadece a'dan z'ye karakterleri, boşlukları ve kesme işaretlerini tut, sonra küçük harfe dönüştür
    return re.sub(r'[^a-z\s\']', '', tweet.lower())
filtered_tweets = [filter_tweet(tweet) for tweet in tweets]
```

Prototipi önceden eğitmek için yeterli bilgiyi çıkardık. Filtrelemeyi daha da ileri götüreceğiz ve sadece en az 30 kelime içeren tweetleri tutacağız:
```python
f = 30 
filtered_tweets = [tweet for tweet in filtered_tweets if len(tweet.split()) > f] 
# Sadece f kelimeden fazla olan tweetleri tut
```

Bu şekilde, modelin yeterli içerik içeren cümlelerdeki uzun vadeli bağımlılıkları öğrenmesini sağlayacağız. Çıktıda, uzun kelime dizileri içerir:
```
ags which only contain certain items such as unwrapped food raw meat and fish where there is a food safety risk prescription medicines uncovered blades seeds bulbs amp s
 hi you can change your microsoft account email through the steps here httpstcodkehohboyy
```

Veri hakkında bilgi kaydetmek ve görüntülemek için aşağıdaki hücreleri çalıştırın. 

**Kod Açıklamaları**

1. `import pandas as pd`: Pandas kütüphanesini pd takma adı ile içe aktarır.
2. `df = pd.read_csv('/content/twcs/twcs.csv')`: `/content/twcs/twcs.csv` dosyasını okuyarak bir DataFrame oluşturur ve `df` değişkenine atar.
3. `print(df.head())`: DataFrame'in ilk birkaç satırını yazdırır.
4. `import re`: re (regular expression) kütüphanesini içe aktarır.
5. `def filter_tweet(tweet)`: Bir tweeti filtrelemek için bir fonksiyon tanımlar.
6. `return re.sub(r'[^a-z\s\']', '', tweet.lower())`: Tweeti küçük harfe dönüştürür ve sadece a'dan z'ye karakterleri, boşlukları ve kesme işaretlerini tutar.
7. `filtered_tweets = [filter_tweet(tweet) for tweet in tweets]`: Tweetleri filtreler ve `filtered_tweets` listesine atar.
8. `f = 30`: Bir eşik değeri tanımlar.
9. `filtered_tweets = [tweet for tweet in filtered_tweets if len(tweet.split()) > f]`: Filtrelenmiş tweetleri, kelime sayısına göre filtreler ve `filtered_tweets` listesine atar.

---

