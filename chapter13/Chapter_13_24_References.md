# Kaynakça Çevirisi

Aşağıdaki metin, verilen ingilizce paragrafın birebir türkçeye çevirisi yapılmış halidir.

Ashish Vaswani, Noam Shazeer, Niki Parmar, Jakob Uszkoreit, Llion Jones, Aidan N. Gomez, Lukasz Kaiser, ve Illia Polosukhin , 2017, Dikkat Her Şeydir : https://arxiv.org/abs/1706.03762 
Peter Shaw, Jakob Uszkoreit, ve Ashish Vaswani , 2018, Göreceli Pozisyon Temsilleri ile Kendi Kendine Dikkat : https://arxiv.org/abs/1803.02155 
Hugging Face Çerçevesi ve Kaynakları : https://huggingface.co/ 
ABD Hukuku, Montana Şirketleri Yasaları : https://corporations.uslegal.com/state-corporation-law/montana-corporation-law/#:~:text=Montana%20Corporation%20Law,carrying%20out%20its%20business%20activities 
Thomas Jefferson tarafından Amerika Birleşik Devletleri Bağımsızlık Bildirgesi: https://www.gutenberg.org/ebooks/1 
Amerika Birleşik Devletleri tarafından Amerika Birleşik Devletleri Haklar Bildirgesi: https://www.gutenberg.org/ebooks/2

Bu çeviride herhangi bir python kodu bulunmamaktadır. Çeviri işlemi manuel olarak yapılmıştır.

Eğer kaynakçada geçen linkleri ayrıştırmak isteseydik, python kodu kullanarak aşağıdaki şekilde yapabilirdik:

```python
import re

# Kaynakça metni
metin = """
Ashish Vaswani, Noam Shazeer, Niki Parmar, Jakob Uszkoreit, Llion Jones, Aidan N. Gomez, Lukasz Kaiser, and Illia Polosukhin , 2017, Attention Is All You Need : https://arxiv.org/abs/1706.03762 Peter Shaw, Jakob Uszkoreit, and Ashish Vaswani , 2018, Self-Attention with Relative Position Representations : https://arxiv.org/abs/1803.02155 Hugging Face Framework and Resources : https://huggingface.co/ US Legal, Montana Corporate Laws : https://corporations.uslegal.com/state-corporation-law/montana-corporation-law/#:~:text=Montana%20Corporation%20Law,carrying%20out%20its%20business%20activities The Declaration of Independence of the United States of America by Thomas Jefferson: https://www.gutenberg.org/ebooks/1 The United States Bill of Rights by the United States: https://www.gutenberg.org/ebooks/2
"""

# Linkleri ayrıştırmak için regular expression kullanıyoruz
linkler = re.findall('https?://\S+', metin)

# Linkleri yazdırma
for link in linkler:
    print(link)
```

Bu kod, metinde geçen linkleri `https?://\S+` regular expression pattern'ı kullanarak bulur ve yazdırır.

1. `import re`: Regular expression kütüphanesini import eder.
2. `metin = "..."`: Kaynakça metnini değişkene atar.
3. `linkler = re.findall('https?://\S+', metin)`: Metinde geçen linkleri bulur.
   - `https?`: "http" veya "https" eşleştirir. `?` işareti `s` karakterinin optional olduğunu belirtir.
   - `://`: "://" karakterlerini eşleştirir.
   - `\S+`: Boşluk karakteri olmayan bir veya daha fazla karakteri eşleştirir.
4. `for link in linkler`: Bulunan linkleri döngüye sokar ve yazdırır.

---

