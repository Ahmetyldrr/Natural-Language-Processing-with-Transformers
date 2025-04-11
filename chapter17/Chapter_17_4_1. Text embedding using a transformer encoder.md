# Analoji
Cümledeki her kelimeyi bir odadaki kişi olarak hayal edin. Bu kişiler (kelimeler) arkadaşlar, yabancılar veya aile üyeleri gibi birbirleriyle ilişkilidir. Transformer, herkesin nasıl ilişkili ve bağlantılı olduğunu öğrenen bir sosyal uzman gibidir.

# Açıklama
"Kelime" terimi, bir kelimenin tokenize edildikten sonra kelimenin belirteç(ler)ini ifade eden gevşek bir şemsiye terimidir.

# Matematik
Her kelimeyi yüksek boyutlu bir uzayda bir vektör $v_i$ olarak düşünün. Transformer'dan geçtikten sonra, her kelime vektörü bağlam kazanır ve bağlamsallaştırılmış bir vektör haline gelir: $C(V_i)$. İşlem, aşağıdaki gibi kelime belirteç vektörlerinden bağlamsallaştırılmış bir belirteç vektörünün oluşturulması olarak özetlenebilir: $C(V_i) = encoder(V_i)$

# Kod
Kodlayıcının kaynak kodunu inceleyelim. Bu alt bölümün kaynak koduna Keras Stable Diffusion GitHub deposunda erişilebilir: https://github.com/keras-team/keras-cv/blob/master/keras_cv/models/stable_diffusion/text_encoder.py. Kaynak kodu, metin kodlayıcının iki sürümünü içerir. Biz sadece aşağıdaki şekilde başlayan ilk sınıfa odaklanacağız:
```python
class TextEncoder(keras.Model):
    def __init__(self, max_length, vocab_size=49408, name=None, download_weights=True):
```
Kod, bir `TextEncoder(keras.Model)` sınıfıdır. Kodlayıcı iki girdi alır: tokenler (kelimeleri temsil eder) ve pozisyonlar (her kelimenin bir dizideki konumunu gösterir). Bu girdiler önce bir `CLIPEmbedding` katmanı kullanılarak dönüştürülür. Bu katman, tokenleri yoğun vektör gösterimlerine dönüştürür ve pozisyon gömmelerini ekler.

Dönüştürülmüş girdiler, bu sürümde 12 kez `CLIPEncoderLayer` katmanlarından geçer. Her `CLIPEncoderLayer`, katman normalizasyonu, bir kendi dikkat mekanizması (`CLIPAttention`) ve ileri beslemeli sinir ağları kullanarak bu gösterimleri geliştirir. Nihai gösterim, tüm girdiyi bağlamsallaştırılmış kelime gömmelerine dönüştürerek bir çıktı üretir.

Python kodlarının satır satır açıklaması:

1. `class TextEncoder(keras.Model):` 
   - `TextEncoder` adlı bir sınıf tanımlar ve bu sınıf `keras.Model` sınıfından miras alır.

2. `def __init__(self, max_length, vocab_size=49408, name=None, download_weights=True):`
   - Sınıfın yapıcı metodunu tanımlar. Bu metod, nesne oluşturulduğunda çağrılır.
   - `max_length`, `vocab_size`, `name` ve `download_weights` parametrelerini alır.

3. `tokens = keras.layers.Input(shape=(max_length,), dtype="int32", name="tokens")`
   - `keras.layers.Input` kullanarak bir girdi katmanı oluşturur.
   - `shape=(max_length,)` bu girdinin şeklini belirtir. Yani, bu girdi `max_length` uzunluğunda bir vektördür.
   - `dtype="int32"` bu girdinin veri tipini 32 bit tam sayı olarak belirtir.
   - `name="tokens"` bu girdiye "tokens" adını verir.

4. `positions = keras.layers.Input(shape=(max_length,), dtype="int32", name="positions")`
   - Aynı şekilde, "positions" adlı bir girdi katmanı daha oluşturur.

Bu kod parçacıkları, bir `TextEncoder` sınıfının nasıl tanımlandığını ve bu sınıfın girdileri nasıl işlediğini gösterir. Girdiler, tokenler ve pozisyonlar olarak iki farklı girdi katmanından alınır ve daha sonra işlenir.

---

