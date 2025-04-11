# Görüntü İşlemede Transformer Kullanımı: ViT Feature Extractor

Bu bölümde, bir görüntünün transformer girdisine dönüştürülmesini göstermek için bir özellik çıkarıcı simülatörü oluşturacağız. Vision Transformer (ViT) modeli, orijinal girdi görüntüsünü 16x16 küçük kare yamalar ızgarasına böler. Bu yamalar, standart bir transformer modeli için token'lara (bir cümledeki kelimeler gibi) eşdeğer olarak kabul edilir.

Aşağıdaki kodda, yamalar 224x224 boyutundaki girdi görüntüsünden PyTorch'un `unfold` fonksiyonu kullanılarak oluşturulur. Bu fonksiyon, bir girdi tensöründen (bu durumda, görüntü) kayan yerel blokları çıkarır. Bunu, görüntüyü küçük kare yamalar halinde dilimlemenin bir yolu olarak düşünebilirsiniz. `patch_size` parametresi, bu yamaların boyutunu tanımlar. Her yama daha sonra 1D vektöre düzleştirilir ve tüm bu vektörler, transformer'a beslenebilecek 2D girdi matrisini oluşturur. Bu matrisin her satırı, tek bir yamanın vektörüne karşılık gelir.

Yama sayısı 224/16 (genişlik) * 224/16 (yükseklik) = 196 yama'dır. Bu, metin token'larının sözlüğü gibi transformer modelinin sözlüğünü oluşturur.

Görüntü, makaleyi göstermek için aşağıdaki koda sunulmadan önce 224x224 piksele yeniden boyutlandırıldı: "An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale, Zhai et al. (2020)" : https://arxiv.org/abs/2010.11929 .

Orijinal ViT makalesinde, bu yamalar doğrudan transformer modeline, uygun bir boyuta doğrusal olarak gömüldükten sonra beslenir. Başka bir deyişle, bu yamalar transformer modelinin okuduğu "kelimeler"dir. Dolayısıyla, ViT bağlamında "işlenmiş yamalar", orijinal görüntüden oluşturulan ve daha sonra transformer için 2D girdi matrisine yeniden şekillendirilen yamaları ifade eder. Bu dönüşüm süreci, ViT'deki veri ön işlemenin önemli bir parçasıdır.

Aşağıdaki kod, bir görüntünün 16x16 piksel kelimelerine dönüştürülmesini gösterir.

### Görüntünün Yüklenmesi

```python
from IPython.display import Image  # Notebook'ta görüntüleri göstermek için kullanılır
from PIL import Image  # Görüntü işleme için kullanılır

# Görüntünün yolu
image_path = "/content/generate_an_image_of_a_car_in_space.jpg"

# Görüntüyü aç
image = Image.open(image_path)
```

### 16x16 Piksel Yamaların Oluşturulması

```python
import torchvision.transforms as transforms
import matplotlib.pyplot as plt

# Dönüşümü tanımla
transform = transforms.Compose([
    transforms.Resize((224, 224)),  # Görüntüyü 224x224'e yeniden boyutlandır
    transforms.ToTensor()  # Görüntüyü PyTorch tensörüne dönüştür
])

# Dönüşümü uygula
pixel_values = transform(image).unsqueeze(0)  # Toplu iş boyutu için ekstra boyut ekle

patch_size = 16  # Modelde kullanılan yama boyutuna uyacak şekilde değiştirin

# pixel_values girdi görüntü tensörünün şekli (toplu_boyut, kanal_sayısı, yükseklik, genişlik) olduğunu varsayalım
patches = pixel_values.unfold(2, patch_size, patch_size).unfold(3, patch_size, patch_size)
# patches şimdi (toplu_boyut, kanal_sayısı, yama_sayısı_yükseklik, yama_sayısı_genişlik, yama_boyutu, yama_boyutu) şeklinde olacaktır
```

### Yamaların Gösterilmesi

```python
# Kolay görüntüleme için patches tensörünü yeniden şekillendir
patches_reshaped = patches.permute(0, 2, 3, 1, 4, 5).contiguous().view(-1, 3, patch_size, patch_size)

# Tensörden PIL Görüntüsüne dönüşüm için bir transform oluştur
to_pil = transforms.ToPILImage()

for i in range(patches_reshaped.size(0)):
    print(f"Yama {i+1} / {patches_reshaped.size(0)} görüntüleniyor")
    patch_size = patches_reshaped[i].shape
    plt.title(f"Yama {i+1}, boyut: {patch_size}")
    plt.imshow(to_pil(patches_reshaped[i]))
    plt.axis("off")  # Eksenleri gizlemek için
    plt.show()
    userInput = input("Sonraki yamayı görüntülemek için Enter'a basın (veya çıkmak için 'q' tuşuna basın)... ")
    if userInput.lower() == 'q':
        break
```

Çıktı, 196 adet 16x16 "kelime" yamasını sırasıyla görüntüler.

### ViT Feature Extractor'ın Rolü

Feature extractor, ham girdi verilerini (bu durumda, bir görüntü) modele beslenebilecek uygun bir formata dönüştürmek için gerekli ön işleme işlemlerini gerçekleştiren model pipeline'ının temel bir bileşenidir.

ViT feature extractor'ın yaptığı işlemleri özetleyelim:
- Yeniden Boyutlandırma: Girdi görüntülerini modelin beklenen boyutuna yeniden boyutlandırır.
- Normalizasyon: Görüntünün piksel değerlerini [0,255] aralığından daha küçük bir aralığa, örneğin [0,1] veya [-1,1]'e normalize eder.
- PyTorch Tensörlerine Dönüştürme: Model, veri işleme için tensörleri gerektirir.
- Yamalama: Görüntüyü kare yamalar halinde böler. Bu, inovasyonun anahtar kısmıdır.
- Düzleştirme ve Gömme: Yamalar doğrudan transformer'a gönderilemez. Her yama 1D diziye düzleştirilir ve token-kelime-görüntü gömme vektörlerine dönüştürülür.

Özetle, feature extractor, ham görüntüyü modelin anlayabileceği bir formata dönüştürmek için gerekli tüm ön işleme işlemlerini gerçekleştirir.

### Gerçek Feature Extractor'ın Kullanımı

```python
from transformers import ViTFeatureExtractor, ViTForImageClassification
from PIL import Image
import requests

feature_extractor = ViTFeatureExtractor.from_pretrained('google/vit-base-patch16-224')
```

Şimdi, ViT mimarisinin transformer bileşenine geçeceğiz.

---

