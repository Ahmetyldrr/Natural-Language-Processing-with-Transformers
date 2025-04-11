# Klasik K-Means Kümeleme Algoritması Uygulanması

Klasik bir k-means kümeleme algoritması, 4 küme oluşturmak için incelemelerin gömme matrisine uygulanır:
```python
from sklearn.cluster import KMeans

# Küme sayısı
n_clusters = 4

# KMeans nesnesi oluşturma
kmeans = KMeans(
    n_clusters=n_clusters,  # Küme sayısı
    init="k-means++",  # Başlangıç yöntemi
    n_init=10,  # Farklı başlangıçlarla deneme sayısı
    random_state=42  # Rastgele sayı üreticisi için tohum değeri
)

# KMeans'i gömme matrisine uydurma
kmeans.fit(matrix)

# Küme etiketlerini alma
labels = kmeans.labels_

# Küme etiketlerini dataframe'e ekleme
df["Cluster"] = labels

# Her kümedeki ortalama puanı hesaplama ve sıralama
df.groupby("Cluster").Score.mean().sort_values()
```
Çıktı, 4 kümenin her birindeki tüm veri noktalarının ortalama noktasını gösterir:
```
2    4.081560
1    4.191176
0    4.221805
3    4.344937
Name: Score, dtype: float64
```
Kümeleri -t-SNE ile görselleştirebiliriz.

---

