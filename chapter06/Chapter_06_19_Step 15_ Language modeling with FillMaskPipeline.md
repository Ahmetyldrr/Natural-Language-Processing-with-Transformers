# Dil Modelleme Görevi Olarak Fill-Mask Kullanma

Şimdi bir dil modelleme fill-mask görevi içe aktaracağız. Eğitilmiş modelimizi ve eğitilmiş tokenizer'ımızı Makine Öğrenimi Maskeleme (MLM) için kullanacağız:

```python
from transformers import pipeline
fill_mask = pipeline("fill-mask",
    model="./KantaiBERT",
    tokenizer="./KantaiBERT")
```

Yukarıdaki kodda, `transformers` kütüphanesinden `pipeline` fonksiyonunu içe aktarıyoruz. `pipeline` fonksiyonu, önceden eğitilmiş modelleri kullanarak çeşitli Doğal Dil İşleme (NLP) görevlerini gerçekleştirmemizi sağlar. Burada, `"fill-mask"` görevi için bir pipeline oluşturuyoruz. `model` ve `tokenizer` parametrelerine, daha önce eğittiğimiz modelin ve tokenizörün bulunduğu dizini (`./KantaiBERT`) belirtiyoruz.

# Modeli İmmanuel Kant Gibi Düşünmeye Teşvik Etme

Şimdi modelimizi İmmanuel Kant gibi düşünmeye teşvik edebiliriz:

```python
fill_mask("Human thinking involves human <mask>.")
```

Bu kod, `<mask>` etiketiyle belirtilen yere en olası tokenleri tahmin etmek için eğitilmiş modeli kullanır.

## Çıktı ve Analizi

Çıktı her çalıştırdığımızda değişebilir çünkü model stokastiktir. Ayrıca, modeli sınırlı miktarda veri ile sıfırdan eğitiyoruz. Ancak, bu çalıştırma sırasında elde edilen çıktı ilginçtir çünkü kavramsal dil modellemeyi tanıtır:

```json
[
  {'score': 0.038927942514419556, 'token': 393, 'token_str': ' reason', 'sequence': 'Human thinking involves human reason.'},
  {'score': 0.014990510419011116, 'token': 446, 'token_str': ' law', 'sequence': 'Human thinking involves human law.'},
  {'score': 0.011723626405000687, 'token': 418, 'token_str': ' conception', 'sequence': 'Human thinking involves human conception.'},
  {'score': 0.01163031067699194, 'token': 531, 'token_str': ' experience', 'sequence': 'Human thinking involves human experience.'},
  {'score': 0.010935084894299507, 'token': 600, 'token_str': ' understanding', 'sequence': 'Human thinking involves human understanding.'}
]
```

Tahminler her çalıştırdığımızda ve Hugging Face modellerini güncellediğinde değişebilir. Ancak, aşağıdaki çıktı sıklıkla ortaya çıkar:
"Human thinking involves human reason."

## Sonuç

Buradaki amaç, bir transformer modelinin nasıl eğitileceğini görmekti. İlginç, insan benzeri tahminler yapabildiğimizi görebiliriz. Bu sonuçlar deneyseldir ve eğitim süreci boyunca değişkenlik gösterebilir. Bu nedenle, modeli her yeniden eğittiğimizde değişeceklerdir. Model, diğer Aydınlanma Çağı düşünürlerinden çok daha fazla veriye ihtiyaç duyacaktır. Ancak, bu modelin amacı, belirli bir tür karmaşık dil modelleme görevi için bir transformer eğitmek üzere veri kümeleri oluşturabileceğimizi göstermektir. Şimdi, bir Üretken Yapay Zeka modeli oluşturarak bunu yapalım.

---

