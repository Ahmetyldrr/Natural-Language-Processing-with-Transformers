# Özellik Çıkarıcının Yapılandırması ve Model Çıktılarının İncelenmesi

Bu bölümde, erişebileceğimiz ana bileşenlerin ve tensörlerin içeriğini görüntüleyeceğiz. Kodda görünme sırasına göre bunları inceleyeceğiz. Aşağıdaki kod, özellik çıkarıcının (Feature_extractor) yapılandırmasını gösterir.

```python
# Özellik çıkarıcının yapılandırması
ViTFeatureExtractor {
  "do_normalize": true,
  "do_rescale": true,
  "do_resize": true,
  "image_mean": [
    0.5,
    0.5,
    0.5
  ],
  "image_processor_type": "ViTFeatureExtractor",
  "image_std": [
    0.5,
    0.5,
    0.5
  ],
  "resample": 2,
  "rescale_factor": 0.00392156862745098,
  "size": {
    "height": 224,
    "width": 224
  }
}
```

Özellik çıkarıcının 224x224 boyutunda bir görüntüyü nasıl normalize ettiği, yeniden ölçeklendirdiği, yeniden boyutlandırdığı ve ortalama hesapladığı görülebilir. Özellik çıkarıcının çıktısı, daha önce gördüğümüz gibi, transformer için girdileri içerir:

```python
inputs = feature_extractor(images=image, return_tensors="pt")
print(inputs['pixel_values'].shape)
```

Çıktı şaşırtıcıdır:

```python
torch.Size([1, 3, 224, 224])
```

1 görüntü ve 3 kanal görüyoruz ve hala orijinal 224x224 görüntünün boyutuna sahibiz, 16x16 boyutundaki patch'lerin 1D olarak düzleştirilerek girdi tokenları haline getirilmemiştir! Dosovitskiy ve diğerleri (2021), sayfa 3, Şekil 1'de, bir görüntüyü sabit boyutlu patch'lere böldüklerini, doğrusal olarak gömdüklerini ve gömülü vektörlerin sırasını standart bir Transformer kodlayıcısına gönderdiklerini belirtirler. Orijinal Transformer, Vaswani ve diğerleri (2017) tarafından detaylandırılmıştır, bir CNN değildir. Yani, bir şeyler oluyor ve bunu bulmalıyız!

# Model Yapılandırmasının İncelenmesi

Bu soruyu cevaplamak için modelin yapılandırmasına bakmalıyız:

```python
model
```

Çıktı, yapılandırmayı gösterir:

```python
ViTForImageClassification(
  (vit): ViTModel(
    (embeddings): ViTEmbeddings(
      (patch_embeddings): ViTPatchEmbeddings(
        (projection): Conv2d(3, 768, kernel_size=(16, 16), stride=(16, 16))
      )
      (dropout): Dropout(p=0.0, inplace=False)
    )
    (encoder): ViTEncoder(
      (layer): ModuleList(
        (0-11): 12 x ViTLayer(
          (attention): ViTAttention(
            (attention): ViTSelfAttention(
              (query): Linear(in_features=768, out_features=768, bias=True)
              (key): Linear(in_features=768, out_features=768, bias=True)
              (value): Linear(in_features=768, out_features=768, bias=True)
              (dropout): Dropout(p=0.0, inplace=False)
            )
            (output): ViTSelfOutput(
              (dense): Linear(in_features=768, out_features=768, bias=True)
              (dropout): Dropout(p=0.0, inplace=False)
            )
          )
          (intermediate): ViTIntermediate(
            (dense): Linear(in_features=768, out_features=3072, bias=True)
            (intermediate_act_fn): GELUActivation()
          )
          (output): ViTOutput(
            (dense): Linear(in_features=3072, out_features=768, bias=True)
            (dropout): Dropout(p=0.0, inplace=False)
          )
          (layernorm_before): LayerNorm((768,), eps=1e-12, elementwise_affine=True)
          (layernorm_after): LayerNorm((768,), eps=1e-12, elementwise_affine=True)
        )
      )
    )
    (layernorm): LayerNorm((768,), eps=1e-12, elementwise_affine=True)
  )
  (classifier): Linear(in_features=768, out_features=1000, bias=True)
)
```

Kodu incelediğimizde, yapılandırmada Dosovitskiy ve diğerleri (2021) tarafından önerilen orijinal ViT modeline göre farklılıklar olduğunu görürüz. Bu, hızlı hareket eden bir pazarda kritik bir sorun değildir. Verimli modeller oluşturmak için tek bir yol yoktur. Ana fark, Dosovitskiy ve diğerleri (2021) tarafından önerilen orijinal ViT modelinin bir CNN içermemesidir.

# Model Çıktılarının İncelenmesi

Şimdi, transformer'ın ham çıktılarını inceleyelim. Önce boyutunu görüntüleyelim:

```python
print(outputs.logits.shape)
```

Çıktı:

```python
torch.Size([1, 1000])
```

Çıktı mantıklıdır. 999 logit (tensörler 0'dan başlar) görüntüleyebileceğimiz etiket sayısına karşılık gelir:

```python
model.config.id2label
```

Çıktının bir alıntısı, 999 etiketimiz olduğunu gösterir:

```python
...
986: "yellow lady's slipper, yellow lady-slipper, Cypripedium calceolus, Cypripedium parviflorum",
987: 'corn',
988: 'acorn',
989: 'hip, rose hip, rosehip',
990: 'buckeye, horse chestnut, conker',
991: 'coral fungus',
992: 'agaric',
993: 'gyromitra',
994: 'stinkhorn, carrion fungus',
995: 'earthstar',
996: 'hen-of-the-woods, hen of the woods, Polyporus frondosus, Grifola frondosa',
997: 'bolete',
998: 'ear, spike, capitulum',
999: 'toilet tissue, toilet paper, bathroom tissue'
```

Şimdi, ham çıktıları inceleyelim:

```python
outputs.logits
```

Çıktının bir alıntısı:

```python
tensor([[ 6.1340e-01, -9.8148e-01, -5.1315e-01, -3.4200e-03, -5.6267e-01, -4.3624e-02, -3.6142e-01, -5.5693e-01, -1.6004e-01,  2.5686e-01,  9.4831e-01, -4.7462e-01, -1.5970e-01,  4.6159e-01, -4.5225e-01,  2.4756e-01, -1.0305e+00, -4.4374e-01,  9.7872e-02,  2.5128e-01,  6.9956e-01, -8.4190e-01, -7.8326e-01, -1.6319e+00, -2.3764e-01,  8.5236e-02, -2.9821e-01,  9.5420e-02, -2.0551e-01, -6.6383e-01,  4.5386e-01, -6.2507e-01, -6.1109e-01, -5.1631e-01, -3.5809e-01,  4.1768e-01, -1.0091e+00,  4.3412e-02,  3.9691e-01, -1.2114e+00, -1.1627e+00, -3.8514e-01, -5.4429e-01, -1.4018e+00, -7.6280e-01…]])
```

Herhangi bir transformer modelinin çıktıları, bu model de dahil olmak üzere, stokastiktir, bu nedenle çıktılar bir çalışmadan diğerine farklılık gösterebilir.

# Çıktıların İşlenmesi

Çıktıları işlemek için softmax fonksiyonunu uygulayabiliriz:

```python
import torch
import pandas as pd

# Softmax fonksiyonunu uygulayarak logitleri olasılıklara dönüştürme
probs = torch.nn.functional.softmax(logits, dim=-1)
```

Ardından, en üst 5 olasılığı ve karşılık gelen etiketleri bulmak için top-k uygulayabiliriz:

```python
# En üst 5 tahmini sınıf olasılığını ve karşılık gelen indisleri bulma
top_5_probs, top_5_labels = torch.topk(probs, 5)

top_5_probs = top_5_probs.detach().cpu().numpy()
top_5_labels = top_5_labels.detach().cpu().numpy()

# ID'lerden etiketlere eşlemeyi alma
id2label = model.config.id2label

# En üst 5 tahmini, karşılık gelen etiketlere ve olasılıklara eşleyen bir sözlük oluşturma
pred_dict = {"Index": [], "Probability": [], "Label": []}

for i in range(5):
    pred_dict["Index"].append(top_5_labels[0][i])
    pred_dict["Probability"].append(top_5_probs[0][i])
    pred_dict["Label"].append(id2label[top_5_labels[0][i]])

# Sözlüğü bir DataFrame'e dönüştürme
pred_df = pd.DataFrame(pred_dict)

# DataFrame'i görüntüleme
pred_df
```

Çıktı, en üst 5 olasılığı, karşılık gelen skorları ve etiketleri gösterir:

```
   Index  Probability           Label
0    404     0.276161       limousine
1    817     0.134495        minivan
2    656     0.073818          pickup
3    436     0.058666           maillot
4    511     0.044341  sports_car, sport car
```

Bu bölümde, ViT modelinin yapılandırmasını ve çıktılarını inceledik. Çıktıları işlemek için softmax fonksiyonunu ve top-k uyguladık. Bir sonraki bölümde, CLIP modelini inceleyeceğiz.

---

