# Orijinal Transformer Modelinin Katmanları

Orijinal Transformer modelinin kodlayıcı ve kod çözücü katmanları, üst üste katmanlardan oluşur. Kodlayıcı yığınının her bir katmanı aşağıdaki yapıya sahiptir:

Şekil 2.3: Transformer Kodlayıcı Yığınının Bir Katmanı
Orijinal kodlayıcı katman yapısı, Transformer modelinin tüm N = 6 katmanı için aynı kalır. Her bir katman iki ana alt katman içerir: çoklu başlı dikkat mekanizması ve tam bağlı konum bazlı ileri beslemeli ağ. Transformer modelinde, her bir ana alt katmanın etrafında bir artık bağlantı (residual connection) olduğunu unutmayın. Bu bağlantılar, bir alt katmanın işlenmemiş girdisini x, bir katman normalleştirme işlevine taşır. Bu şekilde, anahtar bilgilerin, örneğin konumsal kodlamanın, kaybolmadığından emin oluruz. Her bir katmanın normalize edilmiş çıktısı şu şekildedir:

`LayerNormalization(x + Sublayer(x))`

Kodlayıcının N = 6 katmanının her birinin yapısı aynı olsa da, her bir katmanın içeriği, her bir katmanın farklı ağırlıkları nedeniyle önceki katmanla tam olarak aynı değildir. Örneğin, embedding alt katmanı yalnızca yığının alt seviyesinde bulunur. Diğer beş katman, embedding katmanı içermez ve kodlanmış girdinin tüm katmanlar boyunca kararlı olmasını sağlar.

Ayrıca, çoklu başlı dikkat mekanizmaları, 1'den 6'ya kadar olan katmanlarda aynı işlevleri yerine getirir. Ancak, aynı görevleri yerine getirmezler. Her bir katman, önceki katmandan öğrenir ve dizideki tokenleri ilişkilendirmenin farklı yollarını araştırır. Bir kelime bulmacasını çözerken harflerin ve kelimelerin farklı ilişkilerini aradığımız gibi, kelimelerin çeşitli ilişkilerini arar.

Transformer tasarımcıları çok verimli bir kısıtlama getirdiler. Modelin her bir alt katmanının çıktısı, embedding katmanı ve artık bağlantılar dahil olmak üzere sabit bir boyuta sahiptir. Bu boyut `d_model`'dir ve hedeflerinize bağlı olarak başka bir değere ayarlanabilir. Orijinal Transformer mimarisinde, `d_model = 512`'dir.

`d_model` güçlü bir sonuca sahiptir. Pratik olarak tüm anahtar işlemler nokta ürünlerdir. Sonuç olarak, boyutlar kararlı kalır, bu da hesaplanacak işlem sayısını azaltır, makine kaynak tüketimini azaltır ve model boyunca bilgi akışını izlemeyi kolaylaştırır.

Kodlayıcının bu genel görünümü, Transformer'ın son derece optimize edilmiş mimarisini gösterir. Aşağıdaki bölümlerde, alt katmanların ve mekanizmaların her birine yakınlaşacağız. Embedding alt katmanı ile başlayacağız.

Python kodu bulunmamaktadır, ancak `LayerNormalization(x + Sublayer(x))` ifadesi bir Python kodu satırı olarak yazılabilir:

```python
def layer_normalization(x, sublayer_x):
    return LayerNormalization(x + sublayer_x)

# veya 
output = LayerNorm(x + sublayer(x))  # Bazı derin öğrenme kütüphanelerinde bu şekilde de kullanılabilir.
```

Bu kod satırında:

- `x`: İşlenmemiş girdi
- `sublayer_x` veya `sublayer(x)`: Alt katmanın çıktısı
- `LayerNormalization`: Katman normalleştirme işlevi

Bu kod, yukarıdaki metinde bahsedilen `LayerNormalization(x + Sublayer(x))` ifadesini uygular.

---

