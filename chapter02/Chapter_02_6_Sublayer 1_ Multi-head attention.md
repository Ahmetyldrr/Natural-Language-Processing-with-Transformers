# Çoklu Kafalı Dikkat Alt Katmanı
Çoklu kafalı dikkat alt katmanı sekiz kafadan oluşur ve ardından katman normalizasyonu uygulanır. Bu, alt katmanın çıktısına artık bağlantıların eklenmesi ve normalleştirilmesi anlamına gelir.

## Çoklu Kafalı Dikkat Mimarisi
Çoklu kafalı dikkatin girdi vektörü, her kelimenin embedding ve pozisyonel kodlamasını içerir. İlk katmanın girdi vektörünün boyutu $d_{model} = 512$'dir.

Her kelimenin temsiliyeti $d_{model} = 512$ boyutlu bir vektör haline gelir. Her kelime, bir dizi içinde nasıl uyduğunu belirlemek için diğer tüm kelimelerle eşlenir.

### Python Koduyla Çoklu Kafalı Dikkat Uygulaması
Aşağıdaki Python kodu, çoklu kafalı dikkat mekanizmasını uygular.

#### Adım 1: Girdiyi Temsil Etme
```python
import numpy as np
from scipy.special import softmax

# Girdi vektörünü temsil etme
print("Adım 1: Girdi: 3 girdi, d_model=4")
x = np.array([[1.0, 0.0, 1.0, 0.0], 
              [0.0, 2.0, 0.0, 2.0], 
              [1.0, 1.0, 1.0, 1.0]])
print(x)
```

#### Adım 2: Ağırlık Matrislerini Başlatma
```python
# Ağırlık matrislerini başlatma
print("Adım 2: Ağırlıklar 3 boyut x d_model=4")
print("w_query")
w_query = np.array([[1, 0, 1],
                    [1, 0, 0],
                    [0, 0, 1],
                    [0, 1, 1]])
print(w_query)
```

#### Adım 3: Q, K ve V'yi Hesaplama
```python
# Q, K ve V'yi hesaplama
print("Adım 3: Matris çarpımı Q, K, V'yi elde etmek için")
print("Sorgu: x * w_query")
Q = np.matmul(x, w_query)
print(Q)
```

#### Adım 4: Ölçekli Dikkat Skorları
```python
# Ölçekli dikkat skorları
print("Adım 4: Ölçekli Dikkat Skorları")
k_d = 1 
attention_scores = (Q @ K.transpose()) / k_d
print(attention_scores)
```

#### Adım 5: Ölçekli Softmax Dikkat Skorları
```python
# Ölçekli softmax dikkat skorları
print("Adım 5: Ölçekli softmax dikkat skorları her vektör için")
attention_scores[0] = softmax(attention_scores[0])
attention_scores[1] = softmax(attention_scores[1])
attention_scores[2] = softmax(attention_scores[2])
print(attention_scores[0])
print(attention_scores[1])
print(attention_scores[2])
```

#### Adım 6: Nihai Dikkat Gösterimleri
```python
# Nihai dikkat gösterimleri
print("Adım 6: attention value obtained by score1/k_d * V")
print(V[0])
print(V[1])
print(V[2])
print("Dikkat 1")
attention1 = attention_scores[0].reshape(-1, 1)
attention1 = attention_scores[0][0] * V[0]
print(attention1)
```

#### Adım 7: Sonuçları Toplama
```python
# Sonuçları toplama
print("Adım 7: Sonuçları toplayarak çıktı matrisinin ilk satırını oluşturma")
attention_input1 = attention1 + attention2 + attention3
print(attention_input1)
```

#### Adım 8: Tüm Girdiler için Adım 1-7'yi Uygulama
```python
# Tüm girdiler için Adım 1-7'yi uygulama
print("Adım 8: Adım 1-7'yi tüm girdiler için uygulama")
attention_head1 = np.random.random((3, 64))
print(attention_head1)
```

#### Adım 9: Dikkat Alt Katmanının Çıktısı
```python
# Dikkat alt katmanının çıktısı
print("Adım 9: 8 kafanın çıktısını oluşturma")
z0h1 = np.random.random((3, 64))
z1h2 = np.random.random((3, 64))
z2h3 = np.random.random((3, 64))
z3h4 = np.random.random((3, 64))
z4h5 = np.random.random((3, 64))
z5h6 = np.random.random((3, 64))
z6h7 = np.random.random((3, 64))
z7h8 = np.random.random((3, 64))
print("Bir kafanın şekli", z0h1.shape, "8 kafanın boyutu", 64 * 8)
```

#### Adım 10: Kafaların Çıktısını Birleştirme
```python
# Kafaların çıktısını birleştirme
print("Adım 10: Kafaları birleştirerek orijinal 8x64=512 çıktı boyutunu elde etme")
output_attention = np.hstack((z0h1, z1h2, z2h3, z3h4, z4h5, z5h6, z6h7, z7h8))
print(output_attention)
```

## Katman Normalizasyonu
Her dikkat alt katmanından ve her beslemeli alt katmandan sonra, Post-Layer Normalizasyonu (Post-LN) uygulanır.

Post-LN, artık bağlantıları işleyen bir ekleme işlevi ve bir katman normalizasyon işlemi içerir. Artık bağlantıların amacı, kritik bilgilerin kaybolmamasını sağlamaktır.

Post-LN veya katman normalizasyonu şu şekilde tanımlanabilir:

LayerNormalization(x + Sublayer(x))

Burada Sublayer(x) alt katmanın kendisidir ve x, Sublayer(x)'in girdi adımında bulunan bilgidir.

LayerNormalization'un girdisi, x + Sublayer(x)'den elde edilen bir vektör v'dir.

$d_{model} = 512$ her girdi ve çıktı için, tüm işlemleri standart hale getirir.

Birçok LayerNormalization yöntemi mevcuttur ve farklı modeller arasında varyasyonlar mevcuttur.

Temel kavram, v = x + Sublayer(x) için LayerNormalization(v) olarak tanımlanabilir.

Değişkenler:

- $\mu$ v'nin boyut d'ye göre ortalamasıdır.
- $\sigma$ v'nin boyut d'ye göre standart sapmasıdır.
- $\gamma$ bir ölçeklendirme parametresidir.
- $\beta$ bir bias vektörüdür.

Bu LayerNormalization(v) sürümü, birçok olası post-LN yönteminin genel fikrini gösterir.

---

