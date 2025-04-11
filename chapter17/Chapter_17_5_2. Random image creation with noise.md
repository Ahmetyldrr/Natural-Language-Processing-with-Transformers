# Analoji
Bir konuya dayalı bir görüntüyü iyileştirmek zorunda olduğunuzu hayal edin. Konu yoruma açıktır. Görüntünün içeriği belirsiz, bulanık ve hiçbir şey ifade etmeyen birçok öğe ile doludur. İlk izlenim, görüntü içeriğinin konu ile hiçbir ilgisi olmayan çok fazla "gürültü" içerdiğidir. Ardından yaratıcılığınız devreye girer ve bu "gürültüyü" istediğiniz gibi iyileştirebileceğiniz "serbestlik dereceleri" olarak görürsünüz!

# Açıklama
"Görüntü" terimi, modele girdi olarak verilen bir yer tutucu görüntüyü ifade eder. Modelin mimarisine bağlı olarak, bu önceden var olan bir görüntü veya sadece rastgele bir piksel topluluğu olabilir.

# Matematik
Görüntü, bir matris I olarak düşünülebilir. Serbestlik derecesi, her piksele bir değişken eklemektir, böylece ilk görüntümüz haline gelir.  nin değeri, sistemin yaratıcılık düzeyini belirleyen bir parametredir.

# Kod
Gürültünün tanıtılması, aşağıdaki kodda olduğu gibi birçok şekilde gerçekleştirilebilir: https://github.com/keras-team/keras-cv/blob/master/keras_cv/models/stable_diffusion/stable_diffusion.py 
Aşağıdaki alıntı, gürültü tanıtma sürecine bir yaklaşımı göstermektedir:
```python
def _get_initial_diffusion_noise(self, batch_size, seed):
    if seed is not None:
        return tf.random.stateless_normal(
            (batch_size, self.img_height // 8, self.img_width // 8, 4),
            seed=[seed, seed],
        )
    else:
        return tf.random.normal(
            (batch_size, self.img_height // 8, self.img_width // 8, 4)
        )
```
Bu fonksiyon, rastgele gürültü üreten bir Rastgele Sayı Üreteci (RNG) dir. Bir seed argümanı ile, RNG deterministik gürültü (aynı çıktıları çalıştırma) pseudo-rastgele sayılarla üretir. Eğer seed yoksa, RNG non-deterministik gürültü üretir.

**Satır satır kod açıklaması:**

1. `def _get_initial_diffusion_noise(self, batch_size, seed):` 
   - Bu satır, `_get_initial_diffusion_noise` adlı bir fonksiyon tanımlar. Bu fonksiyon, `batch_size` ve `seed` adlı iki parametre alır.

2. `if seed is not None:` 
   - Bu satır, eğer `seed` parametresi `None` değilse, yani bir değer atanmışsa, aşağıdaki kod bloğunu çalıştırır.

3. `return tf.random.stateless_normal((batch_size, self.img_height // 8, self.img_width // 8, 4), seed=[seed, seed])`
   - Bu satır, TensorFlow'un `tf.random.stateless_normal` fonksiyonunu kullanarak rastgele sayılar üretir. 
   - Üretilen rastgele sayıların şekli `(batch_size, self.img_height // 8, self.img_width // 8, 4)` olarak belirlenmiştir. 
   - `seed=[seed, seed]` ifadesi, rastgele sayı üretme işleminin deterministik olmasını sağlar, yani aynı `seed` değeri ile aynı rastgele sayılar üretilir.

4. `else: return tf.random.normal((batch_size, self.img_height // 8, self.img_width // 8, 4))`
   - Eğer `seed` parametresi `None` ise, bu satır TensorFlow'un `tf.random.normal` fonksiyonunu kullanarak rastgele sayılar üretir. 
   - Üretilen rastgele sayıların şekli yine `(batch_size, self.img_height // 8, self.img_width // 8, 4)` olarak belirlenmiştir. 
   - Bu durumda, rastgele sayı üretme işlemi non-deterministik olur, yani her çalıştırma da farklı rastgele sayılar üretilir.

---

