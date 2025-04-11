# Doğruluk Skoru ve F1-Skoru Çevirisi

Doğruluk skoru ve F1-skoru, bir transformer modelinin çıktısını objektif bir şekilde ölçmenin yollarıdır. MCC başka bir ölçüm aracı sağlar. Bu araçlar, aynı modeli farklı konfigürasyonlarla karşılaştırmamıza yardımcı olur. Ayrıca transformer modellerini sıralamamıza da yardımcı olurlar. MCC, 5. Bölüm'de "Matthews Korelasyon Katsayısı Kullanarak Değerlendirme" bölümünde uygulanacaktır, "BERT ile İnce Ayarlamaya Dalmak". MCC, gerçek pozitifler (TP), gerçek negatifler (TN), yanlış pozitifler (FP) ve yanlış negatifler (FN) ile bir ölçüm hesaplar. MCC aşağıdaki denklem ile özetlenebilir:

MCC, sınıfların boyutları farklı olsa bile ikili sınıflandırma modelleri için mükemmel bir metrik sağlar. Şimdi, belirli bir transformer modelinin sonuçlarını ölçmek ve diğer transformer modelleri veya NLP modelleriyle karşılaştırmak için iyi bir fikre sahibiz. Bazı skor yöntemlerini akılda tutarak, insan değerlendirmesinin değerli ölçümlere nasıl katkıda bulunabileceğini şimdi göreceğiz.

Python kodu bulunmamaktadır, sadece bir ingilizce paragraf çevirisi yapılmıştır.

Eğer MCC hesaplaması için bir python kodu yazılırsa, aşağıdaki gibi olabilir:

```python
def matthews_correlation_coefficient(tp, tn, fp, fn):
    # MCC hesaplaması
    numerator = tp * tn - fp * fn
    denominator = ((tp + fp) * (tp + fn) * (tn + fp) * (tn + fn)) ** 0.5
    mcc = numerator / denominator
    return mcc

# Örnek kullanım:
tp = 100  # gerçek pozitif
tn = 50   # gerçek negatif
fp = 20   # yanlış pozitif
fn = 30   # yanlış negatif

mcc = matthews_correlation_coefficient(tp, tn, fp, fn)
print("MCC:", mcc)
```

Bu kodda:

*   `matthews_correlation_coefficient` adlı bir fonksiyon tanımlanmıştır.
*   Bu fonksiyon, gerçek pozitif (`tp`), gerçek negatif (`tn`), yanlış pozitif (`fp`) ve yanlış negatif (`fn`) değerlerini alır.
*   MCC hesaplaması için numerator (pay) ve denominator (payda) hesaplanır.
*   MCC, numerator / denominator olarak hesaplanır.
*   Fonksiyon, MCC değerini döndürür.
*   Örnek kullanımda, `tp`, `tn`, `fp` ve `fn` değerleri verilerek MCC hesaplanır ve yazdırılır.

---

