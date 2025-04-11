# Swin Transformer Modelinin Açıklaması ve Uygulaması

Swin, bilgisayarlı görü için genel amaçlı bir model olarak tasarlanmıştır. Swin transformer, görüntülerin temsillerini öğrenmek için öz-dikkat ve evrişimlerin bir kombinasyonunu kullanan hiyerarşik bir transformer mimarisidir. Bu, modelin başlangıcındaki blokların girdi görüntüsünden düşük seviyeli özellikler çıkardığı, modelin sonundaki blokların ise yüksek seviyeli özellikler çıkardığı anlamına gelir.

## SwinForImageClassification Modelinin Katmanları

SwinForImageClassification modeli aşağıdaki katmanlardan oluşur:
- Girdi görüntüsünden özellikler çıkaran bir evrişimli kök katman.
- Bir dizi Swin transformer bloğu. Her Swin transformer bloğu bir öz-dikkat katmanı, bir evrişimli katman ve bir artık bağlantıdan oluşur.
- Girdi görüntüsü için sınıf olasılıklarını çıkaran bir sınıflandırma başlığı.

## Swin Modelinin Yapılandırılması

Swin modelinin yapılandırmasını aşağıdaki kod ile görselleştirebiliriz:
```python
model_name = "Denis1976/autotrain-training-cifar-10-81128141660"
model = transformers.AutoModelForImageClassification.from_pretrained(model_name, use_auth_token=token)
print(model.config)
```
Bu kod, modelin yapılandırma ayarlarını yazdırır.

### Model Yapılandırma Ayarları

Çıktı, aşağıdaki yapılandırma ayarlarını gösterir:
```json
SwinConfig {
  "_name_or_path": "Denis1976/autotrain-training-cifar-10-81128141660",
  "architectures": [
    "SwinForImageClassification"
  ],
  "attention_probs_dropout_prob": 0.0,
  "depths": [
    2,
    2,
    18,
    2
  ],
  "drop_path_rate": 0.1,
  "embed_dim": 128,
  "encoder_stride": 32,
  "hidden_act": "gelu",
  "hidden_dropout_prob": 0.0,
  "hidden_size": 1024,
  "id2label": {
    "0": "airplane",
    "1": "automobile",
    "2": "ship",
    "3": "truck"
  },
  "image_size": 224,
  "initializer_range": 0.02,
  "label2id": {
    "airplane": "0",
    "automobile": "1",
    "ship": "2",
    "truck": "3"
  },
  "layer_norm_eps": 1e-05,
  "max_length": 128,
  "mlp_ratio": 4.0,
  "model_type": "swin",
  "num_channels": 3,
  "num_heads": [
    4,
    8,
    16,
    32
  ],
  "num_layers": 4,
  "out_features": [
    "stage4"
  ],
  "out_indices": [
    4
  ],
  "padding": "max_length",
  "patch_size": 4,
  "path_norm": true,
  "problem_type": "single_label_classification",
  "qkv_bias": true,
  "stage_names": [
    "stem",
    "stage1",
    "stage2",
    "stage3",
    "stage4"
  ],
  "torch_dtype": "float32",
  "transformers_version": "4.31.0",
  "use_absolute_embeddings": false,
  "window_size": 7
}
```

## Modelin Sınıflandırma Performansı

Modelin "car_in_fog.png" görüntüsünü sınıflandırma performansını aşağıdaki kod ile test edebiliriz:
```python
model_name = "autotrain-training-cifar-10-81128141660"
output = query("car_in_fog.png", model_name)
classify_image(output)
```
Bu kod, modelin sınıflandırma sonucunu yazdırır.

### Sınıflandırma Sonucu

Modelin sınıflandırma sonucu aşağıdaki gibidir:
```
score:0.5013 ship
score:0.418 airplane
score:0.0482 truck
score:0.0324 automobile
```
Model, görüntüyü doğru bir şekilde sınıflandıramamıştır.

## BEiT Modelinin Performansı

BEiT modelinin bu görüntü için daha iyi bir performans sergileyip sergilemediği sorusu ortaya çıkmaktadır.

---

