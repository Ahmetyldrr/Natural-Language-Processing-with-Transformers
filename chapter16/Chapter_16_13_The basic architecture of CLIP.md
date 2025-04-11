# Kontrastif Model: CLIP'in Çalışma Prensibi

Model kontrastiftir: görüntüler, farklılıkları ve benzerlikleri aracılığıyla nasıl birbirine uyduğunu öğrenmek için eğitilir. Görüntü ve altyazılar, (ortak metin, görüntü) ön eğitimi yoluyla birbirlerine doğru yol alır. Ön eğitimden sonra, CLIP yeni görevleri öğrenir. CLIP, GPT modelleri gibi, video dizilerinde eylem tanıma gibi yeni görsel kavramları öğrenebildiği için aktarılabilir. Altyazılar sonsuz uygulamaya yol açar.

# CLIP'in Mimarisi

ViT, görüntüleri kelime benzeri parçalara böler. CLIP, kosinüs benzerliğini en üst düzeye çıkarmak için (altyazı, görüntü) çiftleri için metin ve görüntü kodlayıcılarını ortaklaşa eğitir, Şekil 16.8'de gösterildiği gibi:

## Şekil 16.8: Metin ve Görüntüleri Ortaklaşa Eğitmek

Şekil 16.8, transformerin metin girişi için standart bir transformer kodlayıcı çalıştıracağını gösterir. ResNet 50 katmanlı CNN'yi görüntüler için bir transformer yapısında çalıştıracaktır. ResNet 50, bir dikkat havuzlama mekanizmasında ortalama havuzlama katmanı çalıştırmak üzere değiştirildi ve çok başlı QKV dikkat başlığı kullanıldı.

### Python Kodları ile Açıklama

Aşağıdaki kod, basit bir şekilde CLIP'in nasıl çalıştığını gösterir. Bu kod, PyTorch kütüphanesini kullanır.

```python
import torch
import torch.nn as nn
import torchvision.models as models

# ResNet 50 modelini yükle
resnet = models.resnet50(pretrained=True)

# CLIP'in görüntü kodlayıcı kısmı
class ImageEncoder(nn.Module):
    def __init__(self, resnet):
        super(ImageEncoder, self).__init__()
        self.resnet = nn.Sequential(*list(resnet.children())[:-1])  # Son katmanı kaldır

    def forward(self, x):
        x = self.resnet(x)
        return x

# CLIP'in metin kodlayıcı kısmı (basit bir transformer kodlayıcı)
class TextEncoder(nn.Module):
    def __init__(self):
        super(TextEncoder, self).__init__()
        self.transformer = nn.TransformerEncoderLayer(d_model=512, nhead=8)

    def forward(self, x):
        x = self.transformer(x)
        return x

# CLIP modeli
class CLIP(nn.Module):
    def __init__(self, image_encoder, text_encoder):
        super(CLIP, self).__init__()
        self.image_encoder = image_encoder
        self.text_encoder = text_encoder

    def forward(self, image, text):
        image_features = self.image_encoder(image)
        text_features = self.text_encoder(text)
        # Kosinüs benzerliğini hesapla
        similarity = nn.CosineSimilarity(dim=1)(image_features, text_features)
        return similarity

# CLIP modelini oluştur
image_encoder = ImageEncoder(resnet)
text_encoder = TextEncoder()
clip_model = CLIP(image_encoder, text_encoder)

# Örnek kullanım
image = torch.randn(1, 3, 224, 224)  # Görüntü girişi
text = torch.randn(1, 10, 512)  # Metin girişi (örneğin, 10 kelime, her biri 512 boyutlu)
similarity = clip_model(image, text)
print(similarity)
```

Bu kod, CLIP'in temel bileşenlerini gösterir: görüntü kodlayıcı, metin kodlayıcı ve kosinüs benzerliğini hesaplamak için kullanılan CLIP modeli. Gerçek CLIP modelinde daha karmaşık mimariler ve eğitim yöntemleri kullanılır.

# CLIP'in Öğrenme Süreci

CLIP, metin-görüntü dizilerini öğrenerek tahminlerde bulunmayı öğrenir. Yukarıdaki kodda gösterildiği gibi, görüntü ve metin kodlayıcıları ortaklaşa eğiterek kosinüs benzerliğini en üst düzeye çıkarır. Bu sayede, CLIP yeni görsel kavramları öğrenebilir ve çeşitli görevlerde kullanılabilir.

---

