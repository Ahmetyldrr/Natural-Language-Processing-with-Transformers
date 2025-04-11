# İleri Beslemeli Ağ (FFN) Girişi

İleri Beslemeli Ağ (FFN) girişi, önceki alt katmanın post-LN çıkışının d model = 512 değeridir:

## Şekil 2.21: İleri beslemeli alt katman

İleri Beslemeli alt katman aşağıdaki şekilde açıklanabilir:

*   FFN'ler hem kodlayıcıda hem de çözücüde tam bağlıdır.
*   FFN, pozisyon bazlı bir ağdır. Her pozisyon ayrı ve aynı şekilde işlenir.
*   FFN iki katman içerir ve bir ReLU aktivasyon fonksiyonu uygular.
*   FFN katmanlarının girişi ve çıkışı d model = 512'dir, ancak iç katman d ff = 2048 ile daha büyüktür.

    Bu işlem python kodu ile aşağıdaki şekilde gösterilebilir:
    ```python
# FFN katmanlarının tanımlanması
d_model = 512
d_ff = 2048

# ReLU aktivasyon fonksiyonu
def relu(x):
    return max(0, x)

# FFN işlemi
def ffn(x, W1, b1, W2, b2):
    # İlk katman işlemi
    output = relu(x @ W1 + b1)  # '@' operatörü matris çarpımı için kullanılır
    # İkinci katman işlemi
    output = output @ W2 + b2
    return output
```
    Burada `x @ W1` işlemi matris çarpımıdır ve `b1` bias değerini ekler. `relu` fonksiyonu ReLU aktivasyonunu uygular.

*   FFN, boyutu 1 olan çekirdeklerle iki evrişimli işlem olarak görülebilir.

Bu açıklamayı dikkate alarak, optimize edilmiş ve standardize edilmiş FFN aşağıdaki şekilde tanımlanabilir:

FFN(x) = max(0, xW1 + b1)W2 + b2

Bu işlem yukarıdaki python kodunda `ffn` fonksiyonu ile gösterilmiştir.

FFN çıkışının post-LN'ye gittiği ve daha sonra kodlayıcı yığınının bir sonraki katmanına ve çözücü yığınının çok başlı dikkat katmanına gönderildiği önceki bölümde açıklanmıştır.

Şimdi çözücü yığınına bakalım.

Bu çevirideki python kodları aşağıdaki gibidir:
```python
# FFN katmanlarının tanımlanması
d_model = 512
d_ff = 2048

# ReLU aktivasyon fonksiyonu
def relu(x):
    return max(0, x)

# FFN işlemi
def ffn(x, W1, b1, W2, b2):
    # İlk katman işlemi
    output = relu(x @ W1 + b1)  
    # İkinci katman işlemi
    output = output @ W2 + b2
    return output
```
Satır satır açıklamaları aşağıdaki gibidir:

1.  `d_model = 512`: Modelin boyutunu 512 olarak tanımlar.
2.  `d_ff = 2048`: İç katmanın boyutunu 2048 olarak tanımlar.
3.  `def relu(x):`: ReLU aktivasyon fonksiyonunu tanımlar.
4.  `return max(0, x)`: ReLU aktivasyonunu uygular, yani negatif değerleri 0'a çevirir.
5.  `def ffn(x, W1, b1, W2, b2):`: FFN işlemini tanımlar.
6.  `output = relu(x @ W1 + b1)`: İlk katman işlemini uygular. `x @ W1` matris çarpımıdır, `b1` bias değerini ekler ve ReLU aktivasyonunu uygular.
7.  `output = output @ W2 + b2`: İkinci katman işlemini uygular. `output @ W2` matris çarpımıdır ve `b2` bias değerini ekler.
8.  `return output`: FFN işleminin sonucunu döndürür.

---

