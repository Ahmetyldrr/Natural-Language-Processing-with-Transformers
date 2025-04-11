# PaLM 2'nin Performans İyileştirmeleri

PaLM 2, farklı model boyutlarında downstream görevlerinde PaLM'e kıyasla önemli ölçüde iyileştirilmiş performansa sahiptir. PaLM 2 ailesindeki en büyük model olan PaLM 2-L, en büyük PaLM modelinden çok daha küçüktür! Evet, doğru okudunuz: daha küçük. Makine gücü, azaltılmış işlemler ve paralel işleme yoluyla optimize edilmiştir. PaLM 2, PaLM tarafından yapılan ilerlemeler üzerine inşa edilmiştir. Örneğin, aynı girdi ve çıktı gömmelerini kullanıyoruz, böylece hesaplama sayısını azaltıyoruz. Başka bir örnek, daha önce sıralı olan dikkat alt katmanını ve ileri beslemeli ağı eşzamansız olarak çalıştırmaktır, ki bu da 2. Bölüm'de, Transformer Modelinin Mimarisine Başlarken 'de açıklanmıştır.

Python kodu bulunmamaktadır, sadece bir ingilizce paragrafın türkçeye çevirisi yapılmıştır.

Eğer bir python kodu olsaydı, satır satır açıklama yapardım. Ancak burada sadece bir metin çevirisi vardır. 

Yinede örnek bir python kodu ile ingilizce paragrafı türkçeye çeviren kod bloğu aşağıda verilmiştir.

```python
# İlgili kütüphaneyi import edelim
from googletrans import Translator

# Çeviri yapmak için bir fonksiyon tanımlayalım
def ceviri(paragraf):
    # Translator nesnesini oluşturalım
    translator = Translator()
    
    # Paragrafı türkçeye çevirelim
    sonuc = translator.translate(paragraf, dest='tr')
    
    # Çeviri sonucunu döndürelim
    return sonuc.text

# Çeviri yapılacak paragrafı tanımlayalım
paragraf = """
PaLM 2 has significantly improved performance on downstream tasks across different model sizes compared to PaLM. 
The largest model in the PaLM 2 family, PaLM 2-L, is far smaller than the largest PaLM model! 
Yes, you read correctly: smaller . Machine power has been optimized through reduced operations and parallel processing. 
PaLM 2 builds on the progress made by PaLM. For example, we are using the same input and output embeddings, 
thus reducing the number of computations. Another example is running the attention sublayer and the feedforward network asynchronously, 
which were formerly sequential, as explained in Chapter 2 , Getting Started with the Architecture of the Transformer Model .
"""

# Çeviri fonksiyonunu çağıralım
ceviri_sonucu = ceviri(paragraf)

# Çeviri sonucunu yazdıralım
print(ceviri_sonucu)
```

Bu kod bloğu, `googletrans` kütüphanesini kullanarak ingilizce bir paragrafı türkçeye çevirir. 

1. `from googletrans import Translator` satırı, `googletrans` kütüphanesinden `Translator` sınıfını import eder.
2. `def ceviri(paragraf):` satırı, çeviri yapmak için bir fonksiyon tanımlar.
3. `translator = Translator()` satırı, `Translator` nesnesini oluşturur.
4. `sonuc = translator.translate(paragraf, dest='tr')` satırı, paragrafı türkçeye çevirir.
5. `return sonuc.text` satırı, çeviri sonucunu döndürür.
6. `paragraf = ...` satırı, çeviri yapılacak paragrafı tanımlar.
7. `ceviri_sonucu = ceviri(paragraf)` satırı, çeviri fonksiyonunu çağırır.
8. `print(ceviri_sonucu)` satırı, çeviri sonucunu yazdırır.

---

