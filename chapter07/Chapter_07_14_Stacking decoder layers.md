# OpenAI GPT Modelinin Mimarisi

Artık OpenAI ekibinin dil modellemeye odaklandığını anlıyoruz. Bu nedenle, maskeli dikkat alt katmanını korumak mantıklıdır. Brown ve diğerleri (2020) mükemmel sonuçlar elde etmek için decoder-only transformer modellerinin boyutunu önemli ölçüde artırdılar. GPT modelleri, Vaswani ve diğerleri (2017) tarafından tasarlanan Orijinal Transformer'ın decoder yığınları ile aynı yapıya sahiptir. Decoder yığınlarını Bölüm 2'de, Transformer Modelinin Mimarisine Başlarken bölümünde anlattık. Gerekirse, Orijinal Transformer'ın mimarisini tekrar gözden geçirmek için birkaç dakika ayırın. GPT modeli, Şekil 7.2'de gösterildiği gibi decoder-only mimarisine sahiptir:

## Şekil 7.2: GPT decoder-only mimari

Metin ve pozisyon gömme alt katmanını, maskeli çoklu-başlı öz-dikkat katmanını, normalizasyon alt katmanlarını, ileri beslemeli alt katmanı ve çıktıları tanıyabiliriz. OpenAI ekibi, decoder modelini modelden modele özelleştirdi ve ince ayar yaptı. Radford ve diğerleri (2019) en az dört GPT modeli sundu ve Brown ve diğerleri (2020) en az sekiz model tanımladı. GPT-3 175B modeli, dünya çapında birkaç takımın erişebileceği bilgisayar kaynakları gerektiren benzersiz bir boyuta ulaştı: 
- `n_params = 175.0B` 
- `n_layers = 96` 
- `d_model = 12288` 
- `n_heads = 96`

OpenAI, önemli sayıda model ve varyasyon üretmektedir.

Python kodları bulunmamaktadır, ancak bazı değişken isimleri ve değerleri verilmiştir. Bunlar aşağıda açıklanmıştır:

- `n_params`: Modelin parametre sayısı
- `n_layers`: Modeldeki katman sayısı
- `d_model`: Modelin boyutu
- `n_heads`: Çoklu-başlı öz-dikkat mekanizmasındaki baş sayısı

Bu değişkenler ve değerleri, GPT-3 175B modelinin özelliklerini tanımlamak için kullanılmıştır.

---

