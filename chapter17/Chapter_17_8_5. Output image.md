# Analoji
İlk görüntü, hayal gücünüz ve yaratıcılığınızla geliştirme sürecinin tamamını tamamladınız. İyi tanımlanmış çıktı görüntüsü, stabil difüzyon modelindeki metin embeddings'in doruk noktasıdır.

# Matematik
Çıktı görüntüsü, aslında önceki tüm işlemlerin sonucudur: 
I_output = D(c(v_i), I_diffused)

# Kod
Bu alt bölümün kaynak kodu için çıkış akışı https://github.com/keras-team/keras-cv/blob/master/keras_cv/models/stable_diffusion/diffusion_model.py adresinde görülebilir. 
Çıkış akışı aşağıdaki kodla başlar:
```python
# Çıkış akışı
x = keras.layers.GroupNormalization(epsilon=1e-5)(x)
x = keras.layers.Activation("swish")(x)
output = PaddedConv2D(4, kernel_size=3, padding=1)(x)
...
```
- `x = keras.layers.GroupNormalization(epsilon=1e-5)(x)`: 
  - Bu satır, `GroupNormalization` katmanını kullanarak `x` girdisinin normalizasyonunu sağlar. 
  - `epsilon` değeri, sıfıra bölme hatasını önlemek için kullanılır ve burada `1e-5` olarak ayarlanmıştır.

- `x = keras.layers.Activation("swish")(x)`:
  - Bu satır, `Swish` aktivasyon fonksiyonunu `x` girdisine uygular. 
  - `Swish` fonksiyonu, Google tarafından tanıtılan ve `swish(x) = x * sigmoid(x)` şeklinde tanımlanan bir aktivasyon fonksiyonudur.

- `output = PaddedConv2D(4, kernel_size=3, padding=1)(x)`:
  - Bu satır, `PaddedConv2D` katmanını kullanarak `x` girdisine evrişim işlemi uygular. 
  - `kernel_size=3` parametresi, evrişim çekirdeğinin boyutunu belirtir.
  - `padding=1` parametresi, girdinin kenarlarına dolgu ekler.
  - `4` parametresi, çıktı kanallarının sayısını belirtir.

Çıkış akışı, klasik bir derin öğrenme çıktı süreciyle devam eder:
- Ağın aktivasyonlarını ayarlamak için `GroupNormalization` kullanılır.
- Google tarafından tanıtılan `Swish` aktivasyon katmanı kullanılır: `swish(x) = x * sigmoid(x)`.
- Son çıktıyı hazırlamak için dolgulu evrişim katmanı (`PaddedConv2D`) kullanılır.

---

