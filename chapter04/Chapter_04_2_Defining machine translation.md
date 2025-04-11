# Vaswani ve Takımı (2017) tarafından Transformer'ın Tasarlanması

Vaswani ve takımı (2017), Transformer'ı tasarlarlarken en zor NLP problemlerinden birini ele aldılar. Makine çevirisi için insan bazlı performans sınırına ulaşmak, insan-makine zekası tasarımcıları olarak bizim için ulaşılmaz görünüyor. Ancak bu, Vaswani ve takımı (2017) tarafından Transformer mimarisini yayınlamasını ve state-of-the-art BLEU sonuçlarına ulaşmasını engellemedi. Bu bölümde, makine çevirisini tanımlayacağız.

# Makine Çevirisi Tanımı

Makine çevirisi, makine transdüksiyonları ve çıktıları yoluyla insan çevirisini yeniden üretme sürecidir:

## Şekil 4.1: Makine Çevirisi Süreci

Şekil 4.1'deki genel fikir, makinenin birkaç adımda aşağıdaki işlemleri yapmasıdır:
1. Çevrilecek bir cümle seçin.
2. Kelimelerin birbirleriyle yüz milyonlarca parametre ile nasıl ilişkili olduğunu öğrenin.
3. Kelimelerin birbirlerine ne kadar çok şekilde atıfta bulunduğunu öğrenin.
4. Öğrenilen parametreleri yeni dizilere aktarmak için makine transdüksiyonu kullanın.
5. Bir kelime veya dizi için aday çeviri seçin.

Sürecin her zaman başladığı nokta, kaynak dilde çevrilecek bir cümledir, A. Süreç, hedef dilde, B, çevrilmiş bir cümle içeren bir çıktı ile sona erer. Ara hesaplamalar transdüksiyonları içerir.

Python kodları bulunmamaktadır, ancak ilgili kavramları açıklayan bir kod snippet'i istenirse, makine çevirisi ile ilgili basit bir örnek verilebilir.

Örneğin, basit bir makine çevirisi modeli aşağıdaki gibi olabilir:
```python
# basit makine çevirisi modeli
from transformers import MarianMTModel, MarianTokenizer

# kaynak ve hedef diller
src_lang = "en"
tgt_lang = "tr"

# model ve tokenizer yükleme
model_name = f"Helsinki-NLP/opus-mt-{src_lang}-{tgt_lang}"
tokenizer = MarianTokenizer.from_pretrained(model_name)
model = MarianMTModel.from_pretrained(model_name)

# çeviri fonksiyonu
def translate(text):
    batch = tokenizer([text], return_tensors="pt")
    gen = model.generate(**batch)
    return tokenizer.decode(gen[0], skip_special_tokens=True)

# örnek kullanım
text = "Hello, how are you?"
print(translate(text))
```
Bu kod snippet'i, `transformers` kütüphanesini kullanarak basit bir makine çevirisi modeli oluşturur ve İngilizce'den Türkçe'ye çeviri yapar.

1. `MarianMTModel` ve `MarianTokenizer` sınıflarını `transformers` kütüphanesinden içe aktarın.
2. Kaynak ve hedef diller tanımlayın (`src_lang` ve `tgt_lang`).
3. Model ve tokenizer'ı önceden eğitilmiş model adıyla yükleyin (`model_name`).
4. Çeviri fonksiyonu (`translate`) tanımlayın: 
   - Giriş metnini (`text`) tokenizer ile işleyin (`batch`).
   - Model ile çeviri yapın (`gen`).
   - Çıktıyı tokenizer ile decode edin ve özel tokenleri atlayın (`skip_special_tokens=True`).
5. Örnek bir metni (`text`) çeviri fonksiyonu ile çevirin ve sonucu yazdırın.

Bu örnek, makine çevirisi konusunda basit bir yaklaşımı gösterir. Gerçek dünya uygulamaları daha karmaşık modeller ve daha fazla işlem içerir.

---

