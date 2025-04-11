# Matthews Korelasyon Katsayısı (MCC) Çevirisi

Matthews Korelasyon Katsayısı (MCC) başlangıçta ikili sınıflandırmaların kalitesini ölçmek için tasarlanmıştır ve çok sınıflı bir korelasyon katsayısına dönüştürülebilir. İki sınıflı bir sınıflandırma, her bir tahmin için dört olasılıkla yapılabilir: TP = Gerçek Pozitif TN = Gerçek Negatif FP = Yanlış Pozitif FN = Yanlış Negatif Biyokimyager Brian W. Matthews, 1975 yılında seleflerinin phi fonksiyonundan esinlenerek bunu tasarladı. O zamandan beri, aşağıdaki gibi çeşitli formatlara evrimleşmiştir: MCC tarafından üretilen değer -1 ile +1 arasındadır. +1, bir tahminin maksimum pozitif değeridir. -1, ters bir tahmindir. 0, ortalama rastgele bir tahmindir. Dil kabul edilebilirliği MCC ile ölçülebilir.

## MCC'nin sklearn.metrics'ten İçe Aktarılması

MCC, sklearn.metrics'ten içe aktarılır:
```python
# Matthew'un korelasyon katsayısını kullanarak her bir test grubunu içe aktarın ve değerlendirin
from sklearn.metrics import matthews_corrcoef
```
Bir tahminler kümesi oluşturulur:
```python
matthews_set = []
```
MCC değeri hesaplanır ve matthews_set'e depolanır:
```python
for i in range(len(true_labels)):
    # matthews_corrcoef fonksiyonunu kullanarak MCC değerini hesaplayın
    matthews = matthews_corrcoef(true_labels[i],
                                 # predictions[i]'nin en yüksek olasılıklı sınıfını bulun
                                 np.argmax(predictions[i], axis=1).flatten())
    # MCC değerini matthews_set'e ekleyin
    matthews_set.append(matthews)
```
Kütüphane ve modül sürüm değişiklikleri nedeniyle mesajlar görebilirsiniz. Nihai puan, tüm test setine dayanacaktır.

### Python Kodlarının Açıklaması

1. `from sklearn.metrics import matthews_corrcoef`: sklearn.metrics modülünden matthews_corrcoef fonksiyonunu içe aktarır. Bu fonksiyon, Matthews Korelasyon Katsayısı'nı hesaplamak için kullanılır.

2. `matthews_set = []`: Boş bir liste oluşturur. Bu liste, her bir test grubunun MCC değerlerini depolamak için kullanılır.

3. `for i in range(len(true_labels)):`: true_labels listesindeki her bir eleman için döngü oluşturur.

4. `matthews = matthews_corrcoef(true_labels[i], np.argmax(predictions[i], axis=1).flatten())`:
   - `true_labels[i]`: i. test grubunun gerçek etiketlerini temsil eder.
   - `predictions[i]`: i. test grubunun tahmin edilen olasılıklarını temsil eder.
   - `np.argmax(predictions[i], axis=1)`: predictions[i]'nin her bir satırındaki en yüksek olasılıklı sınıfın indeksini bulur.
   - `.flatten()`: Elde edilen diziyi düzleştirir.
   - `matthews_corrcoef(...)`: Gerçek etiketler ve tahmin edilen etiketler arasındaki MCC değerini hesaplar.

5. `matthews_set.append(matthews)`: Hesaplanan MCC değerini matthews_set listesine ekler.

---

