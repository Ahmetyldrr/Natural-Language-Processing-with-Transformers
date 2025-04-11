# Veri Noktalarının t-SNE Algoritması ile Görselleştirilmesi

Şimdi veri noktalarını t-SNE algoritması kullanarak görüntüleyeceğiz. t-SNE, 1.536 boyutlu yüksek boyutlu verilerimizi alıp, verilerdeki ilişkileri ve desenleri koruyarak 2 boyuta indirecektir. Bu sayede, kümeleri görselleştirebileceğiz:

```python
# Gerekli kütüphanelerin import edilmesi
from sklearn.manifold import TSNE
import matplotlib
import matplotlib.pyplot as plt

# t-SNE nesnesinin oluşturulması
tsne = TSNE(
    n_components=2,  # Çıktı boyut sayısı
    perplexity=15,  # Komşuluk boyutu
    random_state=42,  # Rastgele durum için seed
    init="random",  # Başlangıç yöntemi
    learning_rate=200  # Öğrenme oranı
)

# Verilerin t-SNE ile dönüştürülmesi
vis_dims2 = tsne.fit_transform(matrix)

# x ve y koordinatlarının ayrılması
x = [x for x, y in vis_dims2]
y = [y for x, y in vis_dims2]

# Kümelerin renklere göre ayrılması ve görselleştirilmesi
for category, color in enumerate(["purple", "green", "red", "blue"]):
    # Kategoriye göre x ve y değerlerinin filtrelenmesi
    xs = np.array(x)[df.Cluster == category]
    ys = np.array(y)[df.Cluster == category]
    
    # Noktaların scatter plot ile çizilmesi
    plt.scatter(xs, ys, color=color, alpha=0.3)
    
    # Kümelerin ortalama noktalarının hesaplanması ve işaretlenmesi
    avg_x = xs.mean()
    avg_y = ys.mean()
    plt.scatter(avg_x, avg_y, marker="x", color=color, s=100)

# Grafiğin başlığının belirlenmesi
plt.title("t-SNE ile 2 Boyutta Görselleştirilen Kümeler")

# Çıktı, kümelerin güzel bir görsel temsilidir:
# Şekil 11.10: t-NSE ile Kümelerin Görselleştirilmesi

# Metin örnekleri çalıştırmaya hazırız.
```

Bu kod, yüksek boyutlu verileri t-SNE algoritması kullanarak 2 boyuta indirger ve kümeleri görselleştirir. Her bir küme farklı bir renge sahiptir ve kümelerin ortalama noktaları "x" işareti ile gösterilir.

---

