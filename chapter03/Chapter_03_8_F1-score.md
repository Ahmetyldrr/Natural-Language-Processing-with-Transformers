# F1-Skoru ve Matthews Korelasyon Katsayısı

F1-skoru, dengesiz sınıf dağılımları içeren veri kümeleriyle karşılaşıldığında yardımcı olabilecek daha esnek bir yaklaşım sunar. Bu denklemde, gerçek (T) pozitifler (p), yanlış (F) pozitifler (p) ve yanlış (F) negatifler (n) ilk olarak kesinlik (P) ve hatırlama (R) denklemlerine yerleştirilir: 
Daha sonra F1-skoru, kesinlik (P) ve hatırlama (R) değerlerini kullanarak metriği oluşturur: 
F1-skoru = 2 * (kesinlik * hatırlama) / (kesinlik + hatırlama)
F1-skoru böylece kesinlik (P) ve hatırlama (R) değerlerinin harmonik ortalaması (aritmetik ortalamanın tersi) olarak görülebilir: 
Şimdi Matthews Korelasyon Katsayısı (MCC) yaklaşımını inceleyelim.

Python kodu bulunmamaktadır, ancak F1-skoru hesaplamak için python kodu aşağıdaki gibidir:

```python
# F1-skoru hesaplama
def f1_score(precision, recall):
    return 2 * (precision * recall) / (precision + recall)

# Örnek kullanım
true_positives = 80
false_positives = 20
false_negatives = 30

# Kesinlik (P) hesaplama
precision = true_positives / (true_positives + false_positives)
print("Kesinlik (P):", precision)

# Hatırlama (R) hesaplama
recall = true_positives / (true_positives + false_negatives)
print("Hatırlama (R):", recall)

# F1-skoru hesaplama
f1 = f1_score(precision, recall)
print("F1-skoru:", f1)
```

Satır satır açıklaması:

1. `def f1_score(precision, recall):` F1-skoru hesaplamak için bir fonksiyon tanımlanır. Bu fonksiyon `precision` ve `recall` değerlerini alır.
2. `return 2 * (precision * recall) / (precision + recall)` F1-skoru formülünü uygular ve sonucu döndürür.
3. `true_positives = 80`, `false_positives = 20`, `false_negatives = 30` Örnek değerler atanır.
4. `precision = true_positives / (true_positives + false_positives)` Kesinlik (P) hesaplanır.
5. `recall = true_positives / (true_positives + false_negatives)` Hatırlama (R) hesaplanır.
6. `f1 = f1_score(precision, recall)` F1-skoru hesaplanır.
7. `print` ifadeleri sonuçları yazdırır.

---

