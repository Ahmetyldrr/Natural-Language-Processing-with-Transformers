# Şimdiye Kadar İncelenenler

Şimdiye kadar, kodlayıcı ve kod çözücü katmanlarına sahip Orijinal Transformer modelinin varyasyonlarını inceledik. Ayrıca, yalnızca kodlayıcı veya yalnızca kod çözücü katman yığınlarına sahip diğer modelleri de araştırdık. Ayrıca, katmanların ve parametrelerin boyutu arttı. Ancak, Transformer'ın temel mimarisi, aynı katmanları ve dikkat başlarının hesaplanmasının paralelleştirilmesini koruyarak orijinal yapısını korur. Bu bölümde, Orijinal Transformer'ın temel yapısına saygı duyan ancak bazı önemli değişiklikler yapan yenilikçi transformer modellerini keşfedeceğiz. LEGO © parçalarının verdiği birçok olasılık gibi, birçok transformer modeli ortaya çıkacaktır. Bu parçaları yüzlerce şekilde birleştirebilirsiniz! Transformer model alt katmanları ve katmanları, gelişmiş Yapay Zeka'nın LEGO © parçalarıdır. ViT, CLIP, DALL-E ve GPT-4V gibi güçlü bilgisayarlı görü transformerlarını keşfedeceğiz.

# Yeni Nesil Transformer Modelleri

CLIP, DALL-E ve GPT-4V'yi OpenAI ChatGPT, GPT-4, Google PaLM ve Google BERT (Google tarafından eğitilmiş) ile birlikte büyüyen Üretken Yapay Zeka Temel Modelleri ailesine ekleyebiliriz. Bu güçlü çok modlu Temel Modellerin mimarisini keşfedeceğiz ve transformerların görevden bağımsız olduğunu kanıtlayacağız. Bir transformer, dizileri öğrenir. Bu diziler, görme, ses ve herhangi bir tür veriyi içerir. Resimler, dil gibi veri dizileri içerir. ViT ve CLIP'i çalıştırarak mimarilerini öğreneceğiz. Görme modellerini yenilikçi seviyelere taşıyacağız. OpenAI DALL-E 2 ve DALL-E 3'ün nasıl ana akım üretken sanat ve tasarım haline geldiğini göreceğiz. Son olarak, GPT-4V ile bir not defteri oluşturacağız ve DALL-E 3'ün metin-görüntü etkileşimlerini diverjan semantik ilişkilendirmeye genişleteceğiz. OpenAI modellerini, yüksek diverjan semantik ilişkilendirme yaratıcılığının yeni dünyasına taşıyacağız.

# Bölüm Konuları

Bu bölümde aşağıdaki konuları ele alacağız:
- Görevden bağımsız modellerden görme modellerine
- ViT, görme transformerları
- Kodda ViT
- Metin-görüntü görme transformerları ile CLIP
- Kodda CLIP
- DALL-E 1, 2 ve 3
- GPT-4V, DALL-E 3 ve diverjan semantik ilişkilendirme
- GPT-4V API'sini Uygulama

Bu son teknoloji alanında yapılan tüm yenilikler ve kütüphane güncellemeleri nedeniyle, paketler ve modeller düzenli olarak değişmektedir. Lütfen en son kurulum ve kod örnekleri için GitHub deposuna gidin: https://github.com/Denis2054/Transformers-for-NLP-and-Computer-Vision-3rd-Edition/tree/main/Chapter16 . Ayrıca, bu veya herhangi bir bölümdeki kodu çalıştırırken herhangi bir sorun yaşarsanız, Discord topluluğumuza bir mesaj gönderebilirsiniz ( https://www.packt.link/Transformers ). İlk adımımız, Büyük Dil Modellerinin (LLM'ler) nasıl görme transformerlarına evrildiğini görmek olacaktır.

Python kodları içermediğinden, kod açıklaması yapılmamıştır. Ancak, kod içeren kısımlar için örnek bir python kodu aşağıdaki gibi açıklanabilir.

Örneğin, ViT modelini kodda uygularken:
```python
# ViT modelini import etme
from transformers import ViTForImageClassification, ViTFeatureExtractor

# Modeli ve feature extractor'ı yükleme
model = ViTForImageClassification.from_pretrained('google/vit-base-patch16-224')
feature_extractor = ViTFeatureExtractor.from_pretrained('google/vit-base-patch16-224')

# Görüntüyü işleme
inputs = feature_extractor(images=image, return_tensors="pt")

# Modeli çalıştırma
outputs = model(**inputs)

# Sonuçları alma
logits = outputs.logits
```
Yukarıdaki kodda:
1. `ViTForImageClassification` ve `ViTFeatureExtractor` sınıflarını `transformers` kütüphanesinden import ediyoruz.
2. Önceden eğitilmiş ViT modelini ve feature extractor'ı yüklüyoruz.
3. Görüntüyü feature extractor ile işliyoruz.
4. İşlenmiş girdileri modele veriyoruz ve sonuçları alıyoruz.
5. Modelin çıktılarını işleyerek sınıflandırma sonuçlarını elde ediyoruz.

---

