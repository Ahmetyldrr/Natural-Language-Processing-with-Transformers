# İnsanlığın Ulaşım Serüveni ve GPT-4 ile Haber Beslemesi Okumak

İnsanlık, ayakla yürümekten atlara binmeye, atlardan trenlere, trenlerden arabalara ve uçaklara geçti. Yakında, insanlık uzaydaki uzay araçlarıyla seyahat edecek. 21. yüzyılda, çok az insan New York'tan Los Angeles'a at sırtında gitmek ister. Bazıları araba kullanmayı veya tren almayı tercih edecektir. Çoğu insan uçacaktır. Bir kez GPT-4 copilot'un sağladığı hıza alıştığımızda, geri dönüş olmayacak!

Bu görev için basit bir cümlelik bir komut işi yapar: Denis Rothman "Google Colab'da bir haber beslemesi okuyan bir Python programı yazmak istiyorum. Bunu nasıl yaparım?" GPT-4: "Google Colab'da bir haber beslemesi okuyan bir Python programı yazmak için... GPT-4'ün talimatlarının geri kalanını not defterinde okuyun ve kodu çalıştırın:

```python
# feedparser kütüphanesini yüklemek için pip komutu
!pip install feedparser

# feedparser kütüphanesini içe aktarma
import feedparser

# Haber beslemesi URL'sini tanımlama
news_feed_url = "http://feeds.bbci.co.uk/news/rss.xml"

# Haber beslemesini ayrıştırma
feed = feedparser.parse(news_feed_url)

# Haber beslemesindeki her bir girdi için
for entry in feed.entries:
    # Girdinin başlığını yazdırma
    print(entry.title)
    # Girdinin bağlantısını yazdırma
    print(entry.link)
    # Boş bir satır yazdırma
    print()
```

Çıktı, haber başlıkları ve danışılacak web siteleri sağlar:

NHS 5% pay offer may end bitter dispute in England
https://www.bbc.co.uk/news/health-64977269?at_medium=RSS&at_campaign=KARANGA
.../...

---

