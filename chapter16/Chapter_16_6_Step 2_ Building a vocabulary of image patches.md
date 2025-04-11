# Adım 1: Görüntü Eşit Boyutlu Parçalara Dönüştürülür
Adım 1, bir görüntüyü eşit boyutlu parçalara dönüştürdü. Parçaların motivasyonu, görüntüyü piksel piksel işlemekten kaçınmaktır. Ancak, parçaları işleyecek bir yol bulma sorunu hala devam etmektedir. Google Research ekibi, Şekil 16.3'te gösterildiği gibi, görüntüyü 16x16 "kelime" haline getirmek için bölerek elde edilen parçalarla bir sözlük kullanmaya karar verdi:

# Şekil 16.3: Görüntü Parçalarından Sözlük Oluşturma
Özellik çıkarıcının çıktısı, bu durumda 16x16 görüntü (16x16 piksellik) parçalarından oluşan bir sözlüktür. Bu çıktı, dönüştürücünün girişi için görüntülerin doğrusal 1D bir temsilidir.

Python kodu bulunmamaktadır, ancak eğer görüntü parçalama işlemi python ile yapılacak olsaydı, aşağıdaki gibi bir kod kullanılabilirdi:

```python
import numpy as np

# Görüntü yükleme
img = ...  # örneğin: img = cv2.imread('image.jpg')

# Görüntüyü 16x16 parçalara bölme
patch_size = 16
height, width, _ = img.shape
patches = []
for i in range(0, height, patch_size):
    for j in range(0, width, patch_size):
        patch = img[i:i+patch_size, j:j+patch_size]
        patches.append(patch)

# Parçaları düzleştirme (1D temsil)
patches = [patch.flatten() for patch in patches]
```

Satır satır açıklaması:

1. `import numpy as np`: Numpy kütüphanesi içe aktarılır.
2. `img = ...`: Görüntü yüklenir (örneğin, OpenCV kütüphanesinin `imread` fonksiyonu kullanılarak).
3. `patch_size = 16`: Parça boyutu 16 olarak belirlenir.
4. `height, width, _ = img.shape`: Görüntünün yüksekliği, genişliği ve kanal sayısı alınır.
5. `patches = []`: Parçaları saklamak için boş bir liste oluşturulur.
6. `for i in range(0, height, patch_size)`: Görüntünün yüksekliği boyunca 16'şar adımlarla döngü kurulur.
7. `for j in range(0, width, patch_size)`: Görüntünün genişliği boyunca 16'şar adımlarla döngü kurulur.
8. `patch = img[i:i+patch_size, j:j+patch_size]`: Görüntünün mevcut konumdaki 16x16'luk parçası alınır.
9. `patches.append(patch)`: Parça, `patches` listesine eklenir.
10. `patches = [patch.flatten() for patch in patches]`: Her bir parça, doğrusal 1D bir temsile dönüştürülür (düzleştirilir).

---

