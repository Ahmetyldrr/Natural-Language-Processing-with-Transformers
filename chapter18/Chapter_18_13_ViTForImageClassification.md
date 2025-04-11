# Görüntü Sınıflandırma için ViT Modelinin İncelenmesi

Devrim niteliğindeki Yapay Zeka çağının başlangıcında, metnin ötesinde: Görüntü Dönüştürücüleri (Vision Transformers) konusunu 16. Bölümde ele aldık. Ancak modelin mimarisini bu bölümün not defterinde gözden geçirelim. Not defterindeki ViT şunları içerir:
- Bir görüntü kodlayıcı (image encoder) olarak bir dizi dönüştürücü bloklarından oluşur. Her bir Dönüştürücü bloğu bir kendi dikkat katmanı (self-attention layer), bir evrişimli katman (convolutional layer) ve bir artık bağlantı (residual connection) içerir.
- Giriş görüntüsü için sınıf olasılıklarını çıktı olarak veren bir sınıflandırma başlığı (classification head).

ViT modelindeki görüntü kodlayıcı, giriş görüntüsünü bir dizi yamaya (patch) dönüştürmek için bir yama gömme katmanı (patch embedding layer) kullanır. Dönüştürücü bloklarının yığını daha sonra her bir yamayı işler. ViT modelindeki sınıflandırma başlığı, görüntü kodlayıcısının çıktısını girdi olarak alır ve bir sınıf olasılıkları vektörü çıktı olarak verir. Vektördeki sınıf sayısı, modelin eğitildiği veri kümesindeki sınıf sayısına bağlıdır.

Modelin özel konfigürasyonu aşağıdaki kod ile görüntülenebilir:
```python
model_name = "Denis1976/autotrain-training-cifar-10-81128141658"
model = transformers.AutoModelForImageClassification.from_pretrained(model_name, use_auth_token=token)
print(model.config)
```
Bu kod, modelin konfigürasyonunu yazdırır:
```json
ViTConfig {
  "_name_or_path": "Denis1976/autotrain-training-cifar-10-81128141658",
  "architectures": [
    "ViTForImageClassification"
  ],
  "attention_probs_dropout_prob": 0.0,
  "encoder_stride": 16,
  "hidden_act": "gelu",
  "hidden_dropout_prob": 0.0,
  "hidden_size": 768,
  "id2label": {
    "0": "airplane",
    "1": "automobile",
    "2": "ship",
    "3": "truck"
  },
  "image_size": 224,
  "initializer_range": 0.02,
  "intermediate_size": 3072,
  "label2id": {
    "airplane": "0",
    "automobile": "1",
    "ship": "2",
    "truck": "3"
  },
  "layer_norm_eps": 1e-12,
  "max_length": 128,
  "model_type": "vit",
  "num_attention_heads": 12,
  "num_channels": 3,
  "num_hidden_layers": 12,
  "padding": "max_length",
  "patch_size": 16,
  "problem_type": "single_label_classification",
  "qkv_bias": true,
  "torch_dtype": "float32",
  "transformers_version": "4.31.0"
}
```
Mimariyi incelediğimizde birkaç soru ortaya çıkıyor:
- Model neden 12 dikkat başıyla (attention head) dondurulmuş ve neden daha fazlası yok?
- Sadece 12 katman neden var?
- ViT modeli, kaynak kullanıma sunulduğundan beri evrim geçirdi mi?
- Daha karmaşık mimariler mevcut mu?

Program, sis içindeki araba görüntüsünü sınıflandırmaya çalışır:
```python
model_name = "autotrain-training-cifar-10-81128141658"
output = query("car_in_fog.png", model_name)
classify_image(output)
```
Model, arabayı tanımlayamıyor:
```
score:0.571 airplane
score:0.294 ship
score:0.0856 truck
score:0.0494 automobile
Üzgünüm, bu görüntü sınıflandırılamıyor
```
Tahminler tatmin edici değilse, diğer modelleri aramalı ve kör otomatik eğitim için bütçemizi harcamadan önce analiz etmeliyiz. Yapay Zeka uzmanlarının uzun bir kariyeri var!

Şimdi, 16. Bölümdeki "Görüntü Dönüştürücüleri Kodda" bölümünde tanımlanan fonksiyonu kullanarak sis içindeki arabayı tanımlamaya çalışacağız: ViT-base-patch16-224

```python
image_path = "/content/car_in_fog.png"
import PIL
image = PIL.Image.open(image_path)
from transformers import ViTFeatureExtractor, ViTForImageClassification
from PIL import Image
import requests

feature_extractor = ViTFeatureExtractor.from_pretrained('google/vit-base-patch16-224')
model = ViTForImageClassification.from_pretrained('google/vit-base-patch16-224')
inputs = feature_extractor(images=image, return_tensors="pt")
outputs = model(**inputs)
logits = outputs.logits
```
Program, en yüksek logitlerin etiketlerini görüntüler:
```python
# model, 1000 ImageNet sınıfından birini tahmin ediyor
predicted_class_idx = logits.argmax(-1).item()
print("Tahmin edilen sınıf:", predicted_class_idx, ":", model.config.id2label[predicted_class_idx])
```
Tahmin edilen sınıf projektör (spotlight):
```
Tahmin edilen sınıf: 818 :  spotlight, spot
```
Projektör, kesinlikle bir far değil! Eğer gerçek bir durumda, kendi kendine giden bir arabada olsaydık, bu tahmin sürücü için tehlikeli olurdu. Yapay Zeka başarısız olduğunda, Yapay Zeka olmayan bir profesyonel, Yapay Zeka uzmanına başvurmalı, açıklamasını istemeli ve işlem hattını (pipeline) geliştirmelidir: veri kümesi, hiperparametreler ve konfigürasyon. Bir Yapay Zeka uzmanı, diğer modelleri anlamak için analiz etmek, veri kümelerini değiştirmek ve farklı hiperparametreleri test etmek zorunda kalabilir.

Not defterindeki bir sonraki model Swin'dir.

---

