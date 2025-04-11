# Tokenizasyondan Sonra Kelime Gömmeleri (Word Embeddings)

Tokenizasyondan sonra, bir kelime, elde edilen kelime hazinesinde bir token haline gelir. Ardından, Word2Vec gibi modeller her bir benzersiz token'ı benzersiz bir ID veya dizine eşler. Kelimelere bir dizin eklemek bir sözlük oluşturur. Gömmeler (embeddings), sözlükteki kelimelerin temsilidir. Sözlükteki kelimeleri ve dizinlerini şu şekilde görüntüleyebiliriz:

```python
for word, index in model.wv.key_to_index.items():
    print(f"Kelime: {word}, Dizin: {index}")
```

Çıktı, sözlüğün içeriğini içerir, aşağıdaki alıntıda gösterildiği gibi:
Kelime: one, Dizin: 0
Kelime: truth, Dizin: 1
Kelime: thought, Dizin: 2
Kelime: reason, Dizin: 3
Kelime: may, Dizin: 4
Kelime: could, Dizin: 5
Kelime: heart, Dizin: 6
Kelime: u, Dizin: 7
Kelime: certain, Dizin: 8
Kelime: might, Dizin: 9
Kelime: even, Dizin: 10
Kelime: much, Dizin: 11
Kelime: many, Dizin: 12
Kelime: opinion, Dizin: 13
Kelime: would, Dizin: 14
Kelime: blood, Dizin: 15
Kelime: without, Dizin: 16
Kelime: time, Dizin: 17
…

# Kelime Çiftleri Arasındaki Kosinüs Benzerliği

Ayrıca, kelime listesinde kelime çiftleri arasındaki kosinüs benzerliğini, ilgili gömme vektörlerine göre belirleyen bir fonksiyon oluşturabiliriz. Öncelikle bir kelime listesi tanımlarız:

```python
import numpy as np
from gensim import matutils
import pandas as pd

# Kelime listesi tanımla
words = ["method", "reason", "truth", "rightly", "science", "seeking"]
```

Ardından, listedeki tüm kelime çiftlerini dolaşır ve kosinüs benzerliğini hesaplarız:

```python
# Sonuçları saklamak için liste başlat
data = []

# Tüm kelime çiftlerini dolaş
for i in range(len(words)):
    for j in range(len(words)):
        word1 = words[i]
        word2 = words[j]

        # Kelimelerin modelin kelime hazinesinde olduğundan emin ol
        if word1 not in model.wv or word2 not in model.wv:
            print(f"Bir veya her iki kelime ('{word1}', '{word2}') modelin kelime hazinesinde değil.")
            continue

        # Kosinüs benzerliğini hesapla
        vec1 = model.wv[word1]
        vec2 = model.wv[word2]
        similarity = np.dot(matutils.unitvec(vec1), matutils.unitvec(vec2))

        # Benzerliği uzaklığa çevir
        distance = 1 - similarity

        # Sonuçları ekle
        data.append({'word1': word1, 'word2': word2, 'distance': distance})
```

Son olarak, çıktıyı bir pandas DataFrame'de görüntüleriz:

```python
# DataFrame oluştur ve göster
df = pd.DataFrame(data)
display(df)
```

Çıktı, kelime çiftleri arasındaki kosinüs benzerliğini gösterir, aşağıdaki alıntıda gösterildiği gibi:

# Kosinüs Benzerliği

Bu yüksek boyutlu vektör uzayındaki kosinüs benzerliği skoru, -1 ile 1 arasında değerler üretecektir:
- 1, vektörlerin aynı olduğunu gösterir. Daha yüksek değerler daha yüksek benzerliği gösterir.
- 0, vektörlerin ilişkisiz olduğunu gösterir.
- -1, vektörlerin diametral olarak karşıt olduğunu gösterir.

Kosinüs benzerliği şu şekilde tanımlanabilir:
Kosinüs Benzerliği(A, B) = (A · B) / (||A|| ||B||)

Burada:
- A ve B vektörlerdir.
- “A · B”, A ve B'nin nokta çarpımını gösterir.
- “||A||” ve “||B||”, sırasıyla A ve B'nin büyüklüklerini (veya uzunluklarını) gösterir.

Kelime gömmelerini daha iyi görsel bir temsil için TensorFlow Projector ile görüntüleyebiliriz.

---

