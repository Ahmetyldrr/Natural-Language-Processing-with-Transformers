# Tahmin Sürecinin Çıktısına Derinlemesine Bakış

Tahmin sürecinin çıktısına derinlemesine bakmak ilginçtir. `batch_predictions`'dan sonraki kodlara bakalım. Süreci beş adımda özetleyebilir ve kendi fonksiyonumuzu ekleyebiliriz.

## Adım 1: Cümlenin Gösterilmesi
```python
print(f"Sentence: {sentence}")
```
Bu, değerlendirilmek üzere olan cümleyi gösterir. Örneğin:
```
Sentence: somebody just left - guess who.
```

## Adım 2: Modelin Tahmininin Gösterilmesi
```python
print(f"Prediction: {logits[i]}")
```
Şimdi, ince ayarlanmış modelin tahminini gösterebiliriz:
```
Prediction: [-2.6922598  2.1979954]
```
İlk eleman, `-2.6922598`, ilk sınıfın logit değerini temsil eder, bu durumda yanlış cümleleri temsil eder. İkinci eleman, `2.1979954`, ikinci sınıfın logit değerini temsil eder, bu durumda kabul edilebilir cümleleri temsil eder.

## Adım 3: Softmax Fonksiyonunun Uygulanması
```python
print(f"Softmax probabilities", softmax(logits[i]))
```
Sonuçları yorumlamak için bir softmax fonksiyonu uygulayalım. 
```python
# Softmax logitleri
import numpy as np
def softmax(logits):
    e = np.exp(logits)
    return e / np.sum(e)
```
Bu fonksiyon, logit değerlerini olasılıklara dönüştürür.

## Adım 4: Softmax Olasılıklarının Gösterilmesi
Softmax fonksiyonunun sonucu, toplamı 1 olan iki olasılık dizisidir:
```
Softmax probabilities [0.00746338 0.9925366 ]
```
İlk eleman, kabul edilemez sınıf, `0.00746338` olasılığa sahiptir. İkinci eleman, kabul edilebilir sınıf, `0.9925366` olasılığa sahiptir. Kabul edilebilir sınıfın olasılığının kabul edilemez sınıfın olasılığını aştığını görebiliriz.

## Adım 5: Modelin Tahmininin ve Gerçek Etiketin Gösterilmesi
```python
print(f"Prediction: {batch_predictions[i]}")
```
Modelin cümle için tahmini:
```
Prediction: 1
```
Bu, yaptığımız ayrıntılı çıktı analizimizle eşleşir.
```python
print(f"True label: {label_ids[i]}")
```
Veri kümesinin etiketi:
```
True label: 1
```
Bu durumda, tahminin veri kümesindeki gerçek etiketle eşleştiğini görebiliriz.

## Tahminlerin Değerlendirilmesi
Tahminler yapıldıktan sonra, ham tahminler ve gerçek etiketleri saklanır:
```python
predictions.append(logits)
true_labels.append(label_ids)
```
Program şimdi tahminleri değerlendirebilir.

---

