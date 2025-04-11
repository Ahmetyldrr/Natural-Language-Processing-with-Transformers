# Programlama Dilleri de Birer Dildir
Programlama dilleri de dildir. Eğer kaynak kod için bir transformatörün "kafası"na bakma sürecini tekrarlarsak, transformatör de ortaya çıkacaktır. Model, diğer herhangi bir dil dizisi gibi davranacak ve her katman ve başlık için puanlar üretecektir. GitHub'ın kaynak koduyla eğitildikten sonra, OpenAI GPT modellerinde olduğu gibi, kod satırları üretebilir. Ayrıca, dili çok iyi anladığından, kod hakkında yorum yapabilir. İşte tam olarak olan şey buydu ve OpenAI'ın yaptığı da buydu! Bu kitabın GitHub deposunun Chapter03 klasöründe bulunan `From_training_to_emergence.ipynb` dosyasını açın. Program, https://openai.com/ adresinde sadece ChatGPT Plus ile GPT-4 tarafından yazıldı, yorumlandı ve açıklandı. Talimatları ben yazdım: Denis:
Python'da 1000 rastgele değişken kullanan, k-En Yakın Komşu karar sınırını, 5 sınıfı kullanan ve sonucu MatPlotlib ile görüntüleyen bir k-en yakın komşu programı yazın: ChatGPT Plus, GPT-4 ile bazı ön açıklamalar yazdı, aşağıdaki alıntıda gösterildiği gibi: ... k-NN komşu sınırı, tek bir iyi tanımlanmış sınır değil, daha ziyade düzensiz ve potansiyel olarak ayrık sınırların bir koleksiyonudur, bu da karmaşık ve spesifik veri kümesine ve 'k' seçimine oldukça bağlı olabilir. 'k' küçük olduğunda, karar sınırları gürültüye oldukça duyarlı olabilir ve aşırı uyuma yol açabilir. Öte yandan, 'k' çok büyük olduğunda, karar sınırları çok yumuşak hale gelebilir ve yetersiz uyuma yol açabilir. 'k' nin optimal değerini seçmek, k-NN algoritması ile iyi performans elde etmek için çok önemlidir. .../... Ardından ChatGPT Plus, GPT-4 ile kodu yazdı:

```python
!pip install scikit-learn
import numpy as np
import matplotlib.pyplot as plt
from sklearn.datasets import make_blobs
from sklearn.model_selection import train_test_split
from sklearn.neighbors import KNeighborsClassifier
from matplotlib.colors import ListedColormap

# 5 sınıf ile 1000 rastgele veri noktası oluştur
X, y = make_blobs(n_samples=1000, centers=5, random_state=42)

# Verileri eğitim ve test kümelerine ayır
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)

# k=5 ile bir k-NN sınıflandırıcısı oluştur
knn = KNeighborsClassifier(n_neighbors=5)

# Sınıflandırıcıyı eğitim verileriyle eğit
knn.fit(X_train, y_train)

# Karar sınırlarını çizmek için bir ağ oluştur
h = .02  # ağdaki adım boyutu
x_min, x_max = X[:, 0].min() - 1, X[:, 0].max() + 1
y_min, y_max = X[:, 1].min() - 1, X[:, 1].max() + 1
xx, yy = np.meshgrid(np.arange(x_min, x_max, h), np.arange(y_min, y_max, h))

# Ağ noktalarının sınıf etiketlerini tahmin et
Z = knn.predict(np.c_[xx.ravel(), yy.ravel()])

# Sonucu bir renk grafiğine koy
Z = Z.reshape(xx.shape)

cmap_light = ListedColormap(['#FFAAAA', '#AAFFAA', '#AAAAFF', '#AFAFAF', '#FFD700'])
cmap_bold = ListedColormap(['#FF0000', '#00FF00', '#0000FF', '#808080', '#FFA500'])

plt.figure()
plt.pcolormesh(xx, yy, Z, cmap=cmap_light)

# Eğitim noktalarını çiz
plt.scatter(X_train[:, 0], X_train[:, 1], c=y_train, cmap=cmap_bold, edgecolor='k', s=20)

plt.xlim(xx.min(), xx.max())
plt.ylim(yy.min(), yy.max())
plt.title("5-Sınıf sınıflandırma (k = 5, n_samples = 1000)")
plt.show()
```

## Kod Açıklaması

1. `!pip install scikit-learn`: scikit-learn kütüphanesini kurar.
2. `import numpy as np`, `import matplotlib.pyplot as plt`: gerekli kütüphaneleri içe aktarır.
3. `from sklearn.datasets import make_blobs`: `make_blobs` fonksiyonunu içe aktarır, bu fonksiyon rastgele veri noktaları oluşturur.
4. `X, y = make_blobs(n_samples=1000, centers=5, random_state=42)`: 5 sınıf ile 1000 rastgele veri noktası oluşturur.
5. `X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)`: verileri eğitim ve test kümelerine ayırır.
6. `knn = KNeighborsClassifier(n_neighbors=5)`: k=5 ile bir k-NN sınıflandırıcısı oluşturur.
7. `knn.fit(X_train, y_train)`: sınıflandırıcıyı eğitim verileriyle eğitir.
8. `xx, yy = np.meshgrid(np.arange(x_min, x_max, h), np.arange(y_min, y_max, h))`: karar sınırlarını çizmek için bir ağ oluşturur.
9. `Z = knn.predict(np.c_[xx.ravel(), yy.ravel()])`: ağ noktalarının sınıf etiketlerini tahmin eder.
10. `plt.pcolormesh(xx, yy, Z, cmap=cmap_light)`: sonucu bir renk grafiğine koyar.
11. `plt.scatter(X_train[:, 0], X_train[:, 1], c=y_train, cmap=cmap_bold, edgecolor='k', s=20)`: eğitim noktalarını çizer.

Bu kodu Google Colab'a kopyaladım ve mükemmel bir grafik elde ettim: Şekil 3.6: ChatGPT Plus ile GPT-4 tarafından oluşturulan bir karar sınırı grafiği.

## Deneyden Çıkarımlar
Doğal dil modelleme, bir modeli kelimeleri veya dizileri bağlam içinde tahmin etmek için eğitir. NLU, modeli insan dilinin niyetlerine ve anlamlarına götürür. ChatGPT Plus ile GPT-4 ile konuşmalar yaparak ve çeşitli dillerde belgelenmiş ve yorumlanmış kaynak kodu üreterek devam edebiliriz. Artık downstream görevlerini ele almaya hazırız.

---

