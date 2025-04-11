# Open ViT_CLIP.ipynb 
Bu bölümde, GitHub'da bu bölüm için olan depoda bulunan Open ViT_CLIP.ipynb dosyasını açın. Ardından, not defterinin CLIP hücresine gidin. Program PyTorch ve CLIP'i kurarak başlar: 
```python
!pip install ftfy regex tqdm
!pip install git+https://github.com/openai/CLIP.git
```
Program ayrıca modülleri ve resimlere erişmek için CIFAR-100'u içe aktarır: 
```python
import os
import clip
import torch
from torchvision.datasets import CIFAR100
```
0 ile 9,999 arasında bir indeks ile erişilebilen 10,000 resim mevcuttur. Bir sonraki adım, tahmin yapmak istediğimiz bir resmi seçmektir: 
Şekil 16.9: Bir resim indeksi seçme

Program daha sonra modeli mevcut cihazda (GPU veya CPU) yükler: 
```python
# Modeli yükle
device = "cuda" if torch.cuda.is_available() else "cpu"
model, preprocess = clip.load('ViT-B/32', device)
```
Resimler indirilir: 
```python
# Veri setini indir
cifar100 = CIFAR100(root=os.path.expanduser("~/.cache"), download=True, train=False)
```
Giriş hazırlanır: 
```python
# Girişleri hazırla
image, class_id = cifar100[index]
image_input = preprocess(image).unsqueeze(0).to(device)
text_inputs = torch.cat([clip.tokenize(f"a photo of a {c}") for c in cifar100.classes]).to(device)
```
Tahmini çalıştırmadan önce seçtiğimiz girişi görselleştirelim: 
```python
import matplotlib.pyplot as plt
from torchvision import transforms
plt.imshow(image)
```
Çıktı, indeks 15'in bir aslan olduğunu gösterir: 
Şekil 16.10: İndeks 15'in resmi

Bu bölümdeki resimler Learning Multiple Layers of Features from Tiny Images, Alex Krizhevsky, 2009: https://www.cs.toronto.edu/~kriz/learning-features-2009-TR.pdf kaynağından alınmıştır. CIFAR-10 ve CIFAR-100 veri setlerinin bir parçasıdır (toronto.edu): https://www.cs.toronto.edu/~kriz/cifar.html.

Bunu bir aslan olarak tanımlayabiliyoruz çünkü biz insanız. Başlangıçta NLP için tasarlanan bir transformer modeli, bir resmin ne olduğunu öğrenmelidir. Şimdi, resimleri ne kadar iyi tanıyabildiğini göreceğiz.

Program, özellikleri hesaplarken resim girdisini metin girdisinden ayırarak ortak bir transformer modelini çalıştırdığını gösterir: 
```python
# Özellikleri hesapla
with torch.no_grad():
    image_features = model.encode_image(image_input)
    text_features = model.encode_text(text_inputs)
```
Şimdi, CLIP bir tahmin yapar ve en üstteki beş tahmini gösterir: 
```python
# Resim için en benzer 5 etiketi seç
image_features /= image_features.norm(dim=-1, keepdim=True)
text_features /= text_features.norm(dim=-1, keepdim=True)
similarity = (100.0 * image_features @ text_features.T).softmax(dim=-1)
values, indices = similarity[0].topk(5)

# Sonucu yazdır
print("\nEn iyi tahminler:\n")
for value, index in zip(values, indices):
    print(f"{cifar100.classes[index]:>16s} : {100 * value.item():.2f}%")
```
Daha fazla veya daha az tahmin elde etmek isterseniz topk(5) değerini değiştirebilirsiniz. En üstteki beş tahmin gösterilir: 
```
En iyi tahminler:
            lion: 96.34%
           tiger: 1.04%
           camel: 0.28%
      lawn_mower: 0.26%
         leopard: 0.26%
```
CLIP aslanı buldu, bu da transformer mimarilerinin esnekliğini gösterir. Vizyon modelleri, LLM modelleri gibi stokastiktir, bu nedenle çıktı bir çalışmadan diğerine değişebilir.

Bir sonraki hücre sınıfları gösterir: 
```python
cifar100.classes
```
Sınıfları inceleyebilirsiniz, yalnızca bir etiket ile kısıtlı olmasına rağmen CLIP iyi bir iş çıkardı: 
```python
[...,'kangaroo','keyboard','lamp','lawn_mower','leopard','lion',
 'lizard', ...]
```
Not defterinde CLIP'in mimarisi ve konfigürasyonu hakkında daha fazla bilgi edinebileceğiniz birkaç hücre daha vardır. Model hücresi özellikle ilginçtir çünkü ViT modeli gibi bir convolutional embedding ile başlayan ve ardından "standart" boyutta 768 transformer ile devam eden görsel kodlayıcıyı görebilirsiniz: 
```python
CLIP(
  (visual): VisionTransformer(
    (conv1): Conv2d(3, 768, kernel_size=(32, 32), stride=(32, 32), bias=False)
    (ln_pre): LayerNorm((768,), eps=1e-05, elementwise_affine=True)
    (transformer): Transformer(
      (resblocks): Sequential(
        (0): ResidualAttentionBlock(
          (attn): MultiheadAttention(
            (out_proj): NonDynamicallyQuantizableLinear(in_features=768, out_features=768, bias=True)
          )
          (ln_1): LayerNorm((768,), eps=1e-05, elementwise_affine=True)
          (mlp): Sequential(
            (c_fc): Linear(in_features=768, out_features=3072, bias=True)
            (gelu): QuickGELU()
            (c_proj): Linear(in_features=3072, out_features=768, bias=True)
          )
          (ln_2): LayerNorm((768,), eps=1e-05, elementwise_affine=True)
        )
```
Model hücresinin bir diğer ilginç yönü ise resim kodlayıcı ile birlikte çalışan boyut-512 metin kodlayıcısına bakmaktır: 
```python
(transformer): Transformer(
    (resblocks): Sequential(
      (0): ResidualAttentionBlock(
        (attn): MultiheadAttention(
          (out_proj): NonDynamicallyQuantizableLinear(in_features=512, out_features=512, bias=True)
        )
        (ln_1): LayerNorm((512,), eps=1e-05, elementwise_affine=True)
        (mlp): Sequential(
          (c_fc): Linear(in_features=512, out_features=2048, bias=True)
          (gelu): QuickGELU()
          (c_proj): Linear(in_features=2048, out_features=512, bias=True)
        )
        (ln_2): LayerNorm((512,), eps=1e-05, elementwise_affine=True)
      )
```
CLIP'in verileri nasıl temsil ettiğini görmek için mimari, konfigürasyon ve parametreleri açıklayan hücreleri inceleyin.

Görev-agnostik transformer modellerinin resim-metni çiftlerini metin-metni çiftleri olarak işlediğini gösterdik. Görev-agnostik modelleri müzik-metni, ses-metni, müzik-resimleri veya herhangi bir veri çifti için uygulayabiliriz. Şimdi, resimleri ve metni işleyebilen başka bir görev-agnostik transformer modeli olan DALL-E'yi keşfedeceğiz.

---

