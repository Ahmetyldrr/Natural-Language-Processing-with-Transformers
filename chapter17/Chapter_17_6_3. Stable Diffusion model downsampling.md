# Analoji
Bir "gürültülü" görüntüyü iyileştirdiğinizi hayal edin. Eğer aynı anda çok fazla değişiklik yaparsanız, konudan uzaklaşabilirsiniz. Çalışmanızı küçük adımlara bölmelisiniz. Her küçük ve kademeli adımda, yaratıcılığınızın konuya uyduğundan emin olmak için konuyu yeniden kontrol etmelisiniz. Ayrıca, konuya uyan görüntünün ana özelliklerini özetliyormuş gibi küçültmeye karar verirsiniz.

# Açıklama
Kademeli ve adım adım yapılan işlem, süreci "kararlı" hale getirir. Görüntüyü, konunun en temsil edici özelliklerini koruyarak küçültürsünüz. Görüntüyü bu yöntemlerle işleyerek, görüntüyü "yayıyorsunuz".

# Matematik
Yayılma süreci, yinelemeli bir denklem olarak temsil edilebilir:
```
I t+1 = I t - α • (I t - istenilen durum)
```
Bu denklemde:
- `I`, görüntünün matrisidir.
- `t`, bir yinelemeyi (iteration) temsil eder, bir dizi içindeki zaman-adımı gibi.
- `I t+1`, bir sonraki yinelemeyi temsil eder.
- `α`, yayılmanın ne kadar yavaş veya hızlı olacağını kontrol ederek kararlılığı belirler.
- `I t`, bir yinelemede görüntünün durumudur.
- `istenilen durum`, metin embedding'lerinden türetilen bağlamsallaştırılmış token vektörleri tarafından yönlendirilen hedef görüntü konfigürasyonudur.
- `I t - istenilen durum`, kelime embedding'lerinin etkisi yoluyla her yinelemede azaltılacak sapmanın tahmini.

# Kod
Bu alt bölümde bahsedilen kaynak kodu, https://github.com/keras-team/keras-cv/blob/master/keras_cv/models/stable_diffusion/diffusion_model.py adresinde görüntülenebilir. Kaynak kodun her satırını incelemeyeceğiz, ancak yalnızca küçültme işleminin ana kısmına odaklanacağız.

Bir küçültme sürümünü temsil eden kod şu şekilde başlar:
```python
class DiffusionModelV2(keras.Model):
    def __init__(self, img_height, img_width, max_text_length, name=None, download_weights=True):
        context = keras.layers.Input((max_text_length, 1024))
        t_embed_input = keras.layers.Input((320,))
        latent = keras.layers.Input((img_height // 8, img_width // 8, 4))
        t_emb = keras.layers.Dense(1280)(t_embed_input)
        t_emb = keras.layers.Activation("swish")(t_emb)
        t_emb = keras.layers.Dense(1280)(t_emb)

        # Küçültme akışı
        outputs = []
        x = PaddedConv2D(320, kernel_size=3, padding=1)(latent)
        outputs.append(x)
        ...
```
Bu kod parçasının ana işlevlerini şu şekilde özetleyebiliriz:
- Küçültme akışı, latent girdiye bir evrişim (convolution) uygulanarak başlar. Bu sonuç, `outputs` listesine kaydedilir.
- Sonraki işlemler, iki yineleme için bir döngü içinde yapılır. Her döngüde:
  - Artan derinlik (kanallar) ile bir `ResBlock` uygulanır.
  - `SpatialTransformer` uygulanır. Amaç, modelin geometrik değişmezliğini (çeviriler, ölçekler ve döndürmeler) geliştirmektir.
  - İşlenmiş tensör, `outputs` listesine kaydedilir.
- Her iki yinelemede bir, özellik haritası (feature map), stride 2 olan bir evrişim kullanılarak 2 faktörü ile küçültülür.
- Bu küçültme dizisi, çoklu çözünürlüklerde (320, 640, 1280) uygulanır. Derinlik arttıkça, uzaysal boyutlar azalır (küçültme nedeniyle), ancak temsil kapasitesi artar.

Python kodlarının satır satır açıklaması:

1. `class DiffusionModelV2(keras.Model):` - `DiffusionModelV2` adlı bir sınıf tanımlar ve bu sınıf `keras.Model` sınıfından miras alır.
2. `def __init__(self, img_height, img_width, max_text_length, name=None, download_weights=True):` - Sınıfın yapıcı (constructor) metodunu tanımlar. Bu metod, nesne oluşturulduğunda çağrılır.
3. `context = keras.layers.Input((max_text_length, 1024))` - `max_text_length` uzunluğunda ve 1024 boyutlu bir girdi katmanı tanımlar.
4. `t_embed_input = keras.layers.Input((320,))` - 320 boyutlu bir girdi katmanı daha tanımlar.
5. `latent = keras.layers.Input((img_height // 8, img_width // 8, 4))` - `(img_height // 8, img_width // 8)` boyutlarında ve 4 kanallı bir girdi katmanı tanımlar.
6. `t_emb = keras.layers.Dense(1280)(t_embed_input)` - `t_embed_input` girdisini 1280 boyutlu bir çıktıya dönüştüren yoğun (dense) bir katman tanımlar.
7. `t_emb = keras.layers.Activation("swish")(t_emb)` - `t_emb` üzerine "swish" aktivasyon fonksiyonunu uygular.
8. `outputs = []` - `outputs` adlı boş bir liste tanımlar.
9. `x = PaddedConv2D(320, kernel_size=3, padding=1)(latent)` - `latent` girdisine, 320 filtreli, kernel boyutu 3 ve padding 1 olan bir evrişim katmanı (`PaddedConv2D`) uygular.
10. `outputs.append(x)` - Elde edilen `x` değerini `outputs` listesine ekler.

---

