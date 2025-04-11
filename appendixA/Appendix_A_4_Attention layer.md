# İngilizce Paragrafın Türkçe Çevirisi

Jay'in neyi sevdiğine bakarsak, "portakal" kelimesinin boyutları (veya parametreleri) birkaç ilişki içerir:
Boyut 1: portakal ile akşam arasındaki ilişki
Boyut 2: portakal ve sabah
Boyut 3: Jay ve portakal
Boyut 4: Jay ve sabah
…
Boyut z.
İlişkilerin ikili olarak tanımlandığını unutmayın: bir kelime bir kelimeye. Bu, bir transformatörde kendi kendine dikkatin nasıl çalıştığıdır. 
Bunu Big O gösterimi ile temsil edersek, O(1) elde ederiz. "O" "mertebesinde" anlamına gelir. Örneğin, O(1) "1. mertebeden" veya sabit zaman karmaşıklığı sınıfıdır. 
İkili analizde her bir kelime için başka bir kelime ile ilişkiyi bulmak üzere bir işlem gerçekleştiririz, O(1). 
Bu sayılarla ifade edilecek olursa: 
n = dizinin uzunluğu, bu durumda 11 kelime.
d = kayan noktalı sayılarla ifade edilen boyut sayısı. 
Makine öğreniminde, boyutlar kayan noktalı sayılarla ifade edilir. 
Örneğin, x bir kelime ise, değerler şu şekilde olabilir: [-0.2333, 03.8559, 0.9844…0394]. 
Model, geniş bir kaynak yelpazeden milyarlarca metin veri noktası aracılığıyla bu değerleri öğrenecektir. 
Bu ikili ilişki, Şekil A.1'de gösterildiği gibi bir n * n hesaplamasıdır:
Şekil A.1: Kelime-kelime ilişkileri
O(1) bu durumda bellek karmaşıklığını temsil eder. 
Bir dikkat katmanının hesaplama karmaşıklığı böylece O(n^2 * d) olur. 
n^2, tüm dizi n'nin ikili (kelime-kelime) işlemidir. 
d, modelin öğrendiği boyutları temsil eder. 
Bu ikili, kelime-kelime hesaplama, tek bir matris çarpımı (matmul) ile yapılabilir. 
Yani, bir matris çarpma işlemi işi halledecektir! 
Bunu bir tekrarlayan katman ile arasındaki farkı görelim.

# Python Kodları Açıklaması

Paragrafta bahsedilen matris çarpımı (matmul) işlemi Python'da NumPy kütüphanesi kullanılarak gerçekleştirilebilir. 
Aşağıda örnek bir kod verilmiştir:

```python
import numpy as np

# İki matris tanımlayalım
matrix1 = np.array([[1, 2], [3, 4]])
matrix2 = np.array([[5, 6], [7, 8]])

# Matris çarpımı işlemi
result = np.matmul(matrix1, matrix2)

print(result)
```

1. `import numpy as np`: NumPy kütüphanesini içe aktarır ve `np` takma adını verir.
2. `matrix1 = np.array([[1, 2], [3, 4]])`: İlk matrisi tanımlar.
3. `matrix2 = np.array([[5, 6], [7, 8]])`: İkinci matrisi tanımlar.
4. `result = np.matmul(matrix1, matrix2)`: Matris çarpımı işlemini gerçekleştirir ve sonucu `result` değişkenine atar.
5. `print(result)`: Sonucu yazdırır.

Bu kod, iki matrisi çarpar ve sonucu ekrana basar. Matris çarpımı, dikkat katmanındaki kelime-kelime ilişkilerinin hesaplanmasında kullanılan bir işlemdir.

---

