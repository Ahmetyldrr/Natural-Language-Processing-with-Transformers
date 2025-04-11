# İngilizce Paragrafın Birebir Türkçe Çevirisi

Hangi varyantı kullanırsanız kullanın, doğruluk skoru pratik bir değerlendirmedir. Skor fonksiyonu, her bir sonuç için kesin bir doğru veya yanlış değeri hesaplar. Modelin çıktıları, belirli bir alt küme, örnekler i, için doğru tahminlerle, y, eşleşir veya eşleşmez. Birincil fonksiyon: 
Bunu şu şekilde açıklayabiliriz:

- Modelin çıktıları ile doğru tahminler (y) karşılaştırılır.
- Belirli bir örnekler alt kümesi (örnekler i) için bu karşılaştırma yapılır.
- Eğer alt küme için sonuç doğruysa 1, yanlışsa 0 elde ederiz.

Şimdi daha esnek olan F1-skorunu inceleyelim.

# Python Kodları ve Açıklamaları

Paragraf içinde Python kodları bulunmamaktadır, ancak F1-skoru ve doğruluk skorunun hesaplanması ile ilgili Python kodları aşağıdaki gibidir:

```python
# Doğruluk Skorunun Hesaplanması
from sklearn.metrics import accuracy_score

y_true = [0, 1, 2, 0, 1, 2]  # Gerçek değerler
y_pred = [0, 2, 1, 0, 0, 1]  # Tahmin edilen değerler

accuracy = accuracy_score(y_true, y_pred)
print("Doğruluk Skoru:", accuracy)

# F1-Skorunun Hesaplanması
from sklearn.metrics import f1_score

y_true = [0, 1, 2, 0, 1, 2]  # Gerçek değerler
y_pred = [0, 2, 1, 0, 0, 1]  # Tahmin edilen değerler

f1 = f1_score(y_true, y_pred, average='macro')
print("F1 Skoru:", f1)
```

## Kod Açıklamaları

1. **Doğruluk Skorunun Hesaplanması**
   - `accuracy_score` fonksiyonu `y_true` (gerçek değerler) ve `y_pred` (tahmin edilen değerler) parametreleri ile kullanılır.
   - Bu fonksiyon, doğru tahmin edilen örneklerin oranını hesaplar.

2. **F1-Skorunun Hesaplanması**
   - `f1_score` fonksiyonu `y_true` (gerçek değerler) ve `y_pred` (tahmin edilen değerler) parametreleri ile kullanılır.
   - `average` parametresi, çok sınıflı problemler için F1-skorunun nasıl hesaplanacağını belirler. `'macro'` seçeneği, her bir sınıf için F1-skorunu hesaplar ve ağırlıksız ortalamasını alır.

---

