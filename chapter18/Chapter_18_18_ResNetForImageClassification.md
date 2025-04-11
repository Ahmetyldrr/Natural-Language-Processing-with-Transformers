# ResNet (Kalan Ağ) Modeli ve Uygulaması

ResNet (Kalan Ağ), ConvNext gibi bir sinir ağıdır. Bu bölümdeki eğitilmiş modelin aksine, ResNet 1.000 kata kadar içerebilir. ResNet modelindeki aşamalar, bir yığın evrişimli blokdan oluşur. Her aşamadaki her bir evrişimli blok aynı sayıda filtreden oluşur. Her aşamadaki filtre sayısı, model derinleştikçe artar.

## Eğitilmiş ResNet Modelinin Yapılandırması

Eğitilmiş ResNet modelinin yapılandırmasını görselleştirebiliriz:
```python
model_name = "Denis1976/autotrain-training-cifar-10-81128141659"
model = transformers.AutoModelForImageClassification.from_pretrained(model_name, use_auth_token=token)
print(model.config)
```
Bu kod, eğitilmiş modelin yapılandırmasını yazdırır.

### Yapılandırma Çıktısı

Çıktı olarak aşağıdaki yapılandırma bilgilerini elde ederiz:
```json
ResNetConfig {
  "_name_or_path": "Denis1976/autotrain-training-cifar-10-81128141659",
  "architectures": [
    "ResNetForImageClassification"
  ],
  "depths": [
    3,
    4,
    6,
    3
  ],
  "downsample_in_first_stage": false,
  "embedding_size": 64,
  "hidden_act": "relu",
  "hidden_sizes": [
    256,
    512,
    1024,
    2048
  ],
  "id2label": {
    "0": "airplane",
    "1": "automobile",
    "2": "ship",
    "3": "truck"
  },
  "label2id": {
    "airplane": "0",
    "automobile": "1",
    "ship": "2",
    "truck": "3"
  },
  "layer_type": "bottleneck",
  "max_length": 128,
  "model_type": "resnet",
  "num_channels": 3,
  "out_features": [
    "stage4"
  ],
  "out_indices": [
    4
  ],
  "padding": "max_length",
  "problem_type": "single_label_classification",
  "stage_names": [
    "stem",
    "stage1",
    "stage2",
    "stage3",
    "stage4"
  ],
  "torch_dtype": "float32",
  "transformers_version": "4.31.0"
}
```
## Modelin Sınırlamalarının Test Edilmesi

Şimdi, bu göreceli olarak küçük ResNet modelinin sınırlarını bulmak için küçük bir veri kümesi çalıştırabiliriz. Seviye 3, çok zor, bir görüntü ile başlıyoruz:
```python
model_name = "autotrain-training-cifar-10-81128141659"
output = query("car_in_fog.png", model_name)  # car in fog
classify_image(output)
```
Model başarısız olur:
```
score:0.5376 ship
score:0.4026 airplane
score:0.0336 truck
score:0.0262 automobile
Üzgünüm, bu görüntü sınıflandırılamadı
```
Daha sonra, seviye 2, zor, bir görüntü çalıştırıyoruz:
```python
model_name = "autotrain-training-cifar-10-81128141659"
output = query("car_in_night.jpg", model_name)
classify_image(output)
```
Model yine başarısız olur:
```
score:0.5016 airplane
score:0.4344 ship
score:0.0358 automobile
score:0.0281 truck
Üzgünüm, bu görüntü sınıflandırılamadı
```
Son olarak, seviye 1, kolay, bir görüntü çalıştırıyoruz:
```python
model_name = "autotrain-training-cifar-10-81128141659"
output = query("/content/generate_an_image_of_a_car_in_space.jpg", model_name)
classify_image(output)
```
Model başarılı olur:
```
score:1.0 automobile
score:0.0 truck
score:0.0 airplane
score:0.0 ship
```
## Sonuç

Deneme yanılma yoluyla, iyi hazırlanmış veri kümelerinin ötesine geçen görüntüleri sınıflandırmak için bir görüntü sınıflandırma modelini test etmek için küçük bir veri kümesi bulduk. Bu keşfi, eğitim oturumumuzun en üst sıradaki modeline uygulayalım.

---

