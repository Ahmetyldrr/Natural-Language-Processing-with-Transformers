# PCA ve Doğal Dil İşleme (NLP)

PCA, verileri alır ve daha yüksek bir seviyede temsil eder. Kendinizi mutfağınızda hayal edin. Mutfak, 3D Kartezyen koordinat sistemidir. Mutfaktaki nesneler de spesifik x, y, z koordinatlarına sahiptir. Bir tarif hazırlamak ve malzemeleri mutfak masanızda toplamak istiyorsunuz. Mutfak masanız, mutfağınızdaki tarifin daha yüksek seviyeli bir temsilidir. Mutfak masanız da bir Kartezyen koordinat sistemi kullanır. Ancak mutfağınızın ana özelliklerini çıkarıp tarifinizi mutfak masanızda temsil ettiğinizde, PCA gerçekleştiriyorsunuz demektir. Bunun nedeni, belirli bir tarifi oluşturmak için bir araya gelen temel bileşenleri görüntülemenizdir.

Aynı temsil, Doğal Dil İşleme (NLP) için de uygulanabilir. Örneğin, bir sözlük, kelimelerin listesidir. Ancak anlamlı bir şekilde birlikte kullanılan kelimeler, bir dizinin temel bileşenlerinin temsilini oluşturur. LIT'deki dizilerin PCA temsili, bir transformatörün çıktılarını görselleştirmeye yardımcı olacaktır.

# NLP PCA Temsilini Elde Etmek İçin Ana Özellikler

- **Varyans**: Bir kelimenin veri kümesindeki sayısal varyansı; örneğin, sıklığı ve anlamının sıklığı.
- **Kovaryans**: Birden fazla kelimenin varyansının veri kümesindeki başka bir kelimenin varyansı ile ilişkisi.
- **Özdeğerler ve Özvektörler**: Kartezyen sistemdeki bir temsili elde etmek için kovaryansların vektör ve büyüklük temsilini elde etmemiz gerekir. Özvektörler vektörlerin yönünü sağlayacaktır. Özdeğerler ise büyüklüklerini sağlayacaktır.

# Veri Türetme

Son adım, özellik vektörlerini orijinal veri kümesine uygulamak ve satır özellik vektörünü satır verisiyle çarpmaktır:
```python
# Veri göstermek için = özellik vektörünün satırı * verinin satırı
gosterilecek_veri = ozellik_vektoru_satiri * veri_satiri
```
PCA projeksiyonları, analiz edilecek veri noktalarının net doğrusal bir görselleştirmesini sağlar.

Şimdi LIT ile başlayalım.

**Python Kodları Yok**, sadece basit bir matematiksel işlem örneği var, o da yukarıdaki satırda gösterilmiştir. 

Eğer bir python kodu olsaydı, örneğin PCA işlemi için kullanılan bir kod:
```python
import numpy as np

# Veri matrisi
data = np.array([[1, 2], [3, 4], [5, 6]])

# Kovaryans matrisi hesaplama
cov_matrix = np.cov(data.T)

# Özdeğer ve özvektörleri hesaplama
eigenvalues, eigenvectors = np.linalg.eig(cov_matrix)

# Özvektörleri kullanarak verileri yeni koordinat sistemine dönüştürme
new_data = np.dot(data, eigenvectors)

print(new_data)
```
Bu kod için satır satır açıklama:
1. `import numpy as np`: NumPy kütüphanesini `np` takma adıyla içe aktarır. Bu kütüphane, sayısal işlemler için kullanılır.
2. `data = np.array([[1, 2], [3, 4], [5, 6]])`: Bir NumPy dizisi (array) oluşturur ve `data` değişkenine atar. Bu, veri noktalarını temsil eder.
3. `cov_matrix = np.cov(data.T)`: Veri matrisinin transpozunun kovaryans matrisini hesaplar. Kovaryans, iki değişken arasındaki ilişkiyi ölçer.
4. `eigenvalues, eigenvectors = np.linalg.eig(cov_matrix)`: Kovaryans matrisinin özdeğerlerini ve özvektörlerini hesaplar. Özvektörler, yeni koordinat sisteminin yönlerini temsil eder.
5. `new_data = np.dot(data, eigenvectors)`: Orijinal verileri, özvektörler tarafından tanımlanan yeni koordinat sistemine dönüştürür. Bu, PCA'nın temel adımlarından biridir.
6. `print(new_data)`: Dönüştürülmüş verileri yazdırır. Bu, verilerin PCA uzayındaki temsilidir.

---

