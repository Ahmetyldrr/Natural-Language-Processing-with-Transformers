# Stability AI Araştırma Blogu

Stability AI araştırma blogu: https://stability.ai/research cümlesinin birebir Türkçe çevirisi aşağıdaki gibidir.

Stability AI araştırma blogu: https://stability.ai/research

İngilizce paragrafın Türkçe çevirisi:

Stability AI araştırma blogu: https://stability.ai/research Discord'da Topluluğumuza Katılın Yazarlar ve diğer okuyucularla tartışmalar için topluluğumuzun Discord alanına katılın: https://www.packt.link/Transformers

Çeviri ayrıntıları:

- Stability AI research blog: https://stability.ai/research -> Stability AI araştırma blogu: https://stability.ai/research
- Join our community on Discord -> Discord'da Topluluğumuza Katılın
- Join our community’s Discord space for discussions with the authors and other readers: -> Yazarlar ve diğer okuyucularla tartışmalar için topluluğumuzun Discord alanına katılın:
- https://www.packt.link/Transformers -> https://www.packt.link/Transformers (değişmedi, çünkü bir URL)

Python kodu olmadığı için açıklama yapmaya gerek yoktur. Çeviri elle yapılmıştır.

Eğer bir python kodu ile çeviri yapmamız gerekirse aşağıdaki gibi bir kod kullanılabilir.

```python
# Çeviri yapmak için gerekli kütüphane import edilir.
from deep_translator import GoogleTranslator

def ceviri(metin):
    # GoogleTranslator kütüphanesi kullanılarak İngilizce metin Türkçe'ye çevrilir.
    translated_text = GoogleTranslator(source='en', target='tr').translate(metin)
    return translated_text

# Çeviri yapılacak metin
metin = "Stability AI research blog: https://stability.ai/research Join our community on Discord Join our community’s Discord space for discussions with the authors and other readers: https://www.packt.link/Transformers"

# Çeviri yapılır.
ceviri_sonucu = ceviri(metin)

# Çeviri sonucu yazdırılır.
print(ceviri_sonucu)
```

Bu python kodu deep_translator kütüphanesini kullanarak ingilizce metni türkçeye çevirir. 

1. `from deep_translator import GoogleTranslator` : deep_translator kütüphanesinden GoogleTranslator sınıfını import eder.
2. `def ceviri(metin):` : ceviri adında bir fonksiyon tanımlar. Bu fonksiyonun amacı ingilizce metni türkçeye çevirmektir.
3. `translated_text = GoogleTranslator(source='en', target='tr').translate(metin)` : GoogleTranslator kullanarak ingilizce metni türkçeye çevirir. 
   - `source='en'`: Kaynak dilin ingilizce olduğunu belirtir.
   - `target='tr'`: Hedef dilin türkçe olduğunu belirtir.
4. `return translated_text` : Çeviri sonucunu döndürür.
5. `metin = "Stability AI research blog: https://stability.ai/research Join our community on Discord Join our community’s Discord space for discussions with the authors and other readers: https://www.packt.link/Transformers"` : Çeviri yapılacak metni tanımlar.
6. `ceviri_sonucu = ceviri(metin)` : ceviri fonksiyonunu çağırarak çeviri sonucunu `ceviri_sonucu` değişkenine atar.
7. `print(ceviri_sonucu)` : Çeviri sonucunu yazdırır.

---

