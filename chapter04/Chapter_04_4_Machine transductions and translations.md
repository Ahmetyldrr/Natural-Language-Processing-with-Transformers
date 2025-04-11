# Orijinal Transformer Mimarisi

Orijinal Transformer mimarisinin dönüştürme işlemi, bir referans dizisini temsil etmek için kodlayıcı yığını, çözücü yığını ve modelin tüm parametrelerini kullanır. Bu çıktı dizisine referans olarak değineceğiz. Neden sadece "çıktı tahmini" demiyoruz? Sorun şu ki, tek bir çıktı tahmini yoktur. Transformer'lar, insanlar gibi, referans verebileceğimiz bir sonuç üretecek, ancak farklı şekilde eğitirsek veya farklı Transformer modelleri kullanırsak bu sonuç değişebilir! Hemen, insan dönüştürmesinin insan bazlı, bir dil dizisinin temsillerinin oldukça zorlu olduğunu fark ediyoruz. Ancak, çok ilerleme kaydedildi. Makine çevirisinin değerlendirilmesi, Doğal Dil İşleme (NLP) alanının ilerlediğini kanıtlıyor. Bir çözümün diğerinden daha iyi olduğunu belirlemek için, her NLP yarışmacısı, laboratuvarı veya organizasyonu, karşılaştırmanın geçerli olması için aynı veri kümelerine başvurmalıdır.

Şimdi, verdiğiniz İngilizce paragrafın birebir Türkçe çevirisini yaptım. Python kodları bulunmamaktadır, eğer bir kod örneği istiyorsanız lütfen belirtiniz.

Eğer bir kod örneği olarak çeviri işlemini göstermek istersek, basit bir Python kodu ile aşağıdaki şekilde yapabiliriz:

```python
# İngilizce paragraf
english_paragraph = """
The transduction process of the Original Transformer architecture uses the encoder stack, the decoder stack, and all the model’s parameters to represent a reference sequence . We will refer to that output sequence as the reference . Why not just say “output prediction”? The problem is that there is no single output prediction. Transformers, like humans, will produce a result we can refer to, but that can change if we train it differently or use different transformer models! We immediately realize that the human baseline of human transduction, representations of a language sequence, is quite a challenge. However, much progress has been made. An evaluation of machine translation proves that NLP has progressed. To determine that one solution is better than another, each NLP challenger, lab, or organization must refer to the same datasets for the comparison to be valid.
"""

# Çeviri işlemi
turkish_paragraph = """
Orijinal Transformer mimarisinin dönüştürme işlemi, bir referans dizisini temsil etmek için kodlayıcı yığını, çözücü yığını ve modelin tüm parametrelerini kullanır. Bu çıktı dizisine referans olarak değineceğiz. Neden sadece "çıktı tahmini" demiyoruz? Sorun şu ki, tek bir çıktı tahmini yoktur. Transformer'lar, insanlar gibi, referans verebileceğimiz bir sonuç üretecek, ancak farklı şekilde eğitirsek veya farklı Transformer modelleri kullanırsak bu sonuç değişebilir! Hemen, insan dönüştürmesinin insan bazlı, bir dil dizisinin temsillerinin oldukça zorlu olduğunu fark ediyoruz. Ancak, çok ilerleme kaydedildi. Makine çevirisinin değerlendirilmesi, Doğal Dil İşleme (NLP) alanının ilerlediğini kanıtlıyor. Bir çözümün diğerinden daha iyi olduğunu belirlemek için, her NLP yarışmacısı, laboratuvarı veya organizasyonu, karşılaştırmanın geçerli olması için aynı veri kümelerine başvurmalıdır.
"""

# Yazdırma işlemi
print("# Orijinal Transformer Mimarisi")
print(turkish_paragraph)
```

Bu kod, sadece İngilizce paragrafı ve Türkçe çevirisini yazdırır. Gerçek bir çeviri işlemi için, Google Translate API veya başka bir çeviri kütüphanesi kullanmanız gerekir. 

Örneğin, `deep_translator` kütüphanesini kullanarak:

```python
from deep_translator import GoogleTranslator

english_paragraph = """
The transduction process of the Original Transformer architecture uses the encoder stack, the decoder stack, and all the model’s parameters to represent a reference sequence . We will refer to that output sequence as the reference . Why not just say “output prediction”? The problem is that there is no single output prediction. Transformers, like humans, will produce a result we can refer to, but that can change if we train it differently or use different transformer models! We immediately realize that the human baseline of human transduction, representations of a language sequence, is quite a challenge. However, much progress has been made. An evaluation of machine translation proves that NLP has progressed. To determine that one solution is better than another, each NLP challenger, lab, or organization must refer to the same datasets for the comparison to be valid.
"""

turkish_paragraph = GoogleTranslator(source='auto', target='tr').translate(english_paragraph)

print("# Orijinal Transformer Mimarisi")
print(turkish_paragraph)
```

---

