# LIT'in Görsel Arayüzü ile Model Analizi

LIT'in görsel arayüzü, modelin yanlış işlemden geçirdiği örnekleri bulmanıza, benzer örnekleri analiz etmenize, bir bağlamı değiştirdiğinizde modelin nasıl davrandığını görmenize ve daha fazlasına yardımcı olacaktır. LIT, BertViz'in yaptığı gibi dikkat başlıklarının aktivitelerini görüntülemez. Ancak, neden işlerin yanlış gittiğini analiz etmek ve çözüm bulmaya çalışmak önemlidir. Bir Uniform Manifold Approximation ve Projection (UMAP) görselleştirmesi veya bir PCA projektör temsili seçebilirsiniz. PCA, belirli yönlerde ve büyüklükte daha lineer projeksiyonlar yapacaktır. UMAP, projeksiyonlarını mini kümelere ayıracaktır. Her iki yaklaşım da, bir modelin çıktısını analiz ederken ne kadar ileri gitmek istediğinize bağlı olarak anlam ifade eder. Hem PCA hem de UMAP'i çalıştırabilir ve aynı model ve örneklerin farklı perspektiflerini elde edebilirsiniz. Bu bölüm, LIT'i çalıştırmak için PCA'yı kullanacaktır. PCA'nın nasıl çalıştığına dair kısa bir hatırlatmayla başlayalım.

Python kodu bulunmamaktadır, ancak PCA ve UMAP ile ilgili bazı açıklamalar vardır. İşte bu kavramlarla ilgili kısa açıklamalar:

*   PCA (Principal Component Analysis): 
    *   PCA, yüksek boyutlu verileri daha düşük boyutlu bir uzaya yansıtmak için kullanılan bir tekniktir.
    *   Verilerin varyansını maksimize eden yönleri bulur ve verileri bu yönlere göre yansıtır.
*   UMAP (Uniform Manifold Approximation and Projection):
    *   UMAP, yüksek boyutlu verileri daha düşük boyutlu bir uzaya yansıtmak için kullanılan bir başka tekniktir.
    *   Verilerin yerel yapısını korumaya çalışır ve verileri daha anlamlı bir şekilde yansıtır.

Eğer PCA veya UMAP'i Python'da uygulamak isterseniz, aşağıdaki gibi kodlar kullanabilirsiniz:

```python
# PCA örneği
import pandas as pd
from sklearn.decomposition import PCA
from sklearn.preprocessing import StandardScaler

# Veri setini yükleyin
data = pd.read_csv("veri_seti.csv")

# Verileri standardize edin
scaler = StandardScaler()
data_scaled = scaler.fit_transform(data)

# PCA uygulayın
pca = PCA(n_components=2)
data_pca = pca.fit_transform(data_scaled)

# Sonuçları görselleştirin
import matplotlib.pyplot as plt
plt.scatter(data_pca[:, 0], data_pca[:, 1])
plt.show()

# UMAP örneği
import umap
import pandas as pd

# Veri setini yükleyin
data = pd.read_csv("veri_seti.csv")

# UMAP uygulayın
reducer = umap.UMAP(n_components=2)
data_umap = reducer.fit_transform(data)

# Sonuçları görselleştirin
import matplotlib.pyplot as plt
plt.scatter(data_umap[:, 0], data_umap[:, 1])
plt.show()
```

---

