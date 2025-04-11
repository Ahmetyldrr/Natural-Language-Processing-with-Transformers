# BEiT Modeli
Bir BEiT modeli, BERT modelinden türetilmiştir: BERT Pre-Training of Image Transformers (BEiT). BEiT şunları içerir:
- Bir görüntü kodlayıcı, 12 transformer bloğundan oluşan bir yığından oluşur. 
- Her bir transformer bloğu, bir self-attention katmanı, bir convolutional katman ve bir residual bağlantıdan oluşur.
- Giriş görüntüsü için sınıf olasılıklarını çıktı olarak veren bir sınıflandırma başlığı.
- Giriş görüntüsünün anlamsal segmentasyonunu tahmin eden bir yardımcı başlık.

## BEiT Modelinin Çalışması
BEiT modelindeki görüntü kodlayıcı, giriş görüntüsünü bir dizi patch'e dönüştürmek için bir patch embedding katmanı kullanır. Daha sonra transformer blokları yığını her bir patch'i işler. Transformer blokları, görüntüdeki farklı patch'lere dikkat etmeyi öğrenir ve ayrıca patch'ler arasındaki uzun menzilli bağımlılıkları öğrenir.

## Sınıflandırma ve Yardımcı Başlıklar
BEiT modelindeki sınıflandırma başlığı, görüntü kodlayıcısının çıktısını girdi olarak alır ve bir sınıf olasılıkları vektörü çıktı olarak verir. Vektördeki sınıf sayısı, modelin eğitildiği veri kümesindeki sınıf sayısına bağlıdır. BEiT modelindeki yardımcı başlık, görüntü kodlayıcısının çıktısını girdi olarak alır ve giriş görüntüsünün anlamsal segmentasyonunu tahmin eder. Anlamsal segmentasyon, görüntünün piksel düzeyinde sınıflandırılmasıdır, yani görüntüdeki her piksele bir sınıf etiketi atanır.

## BEiT Modelinin Yapılandırması
BEiT modelinin özel yapılandırması aşağıdaki kod ile görüntülenebilir:
```python
model_name = "Denis1976/autotrain-training-cifar-10-81128141661"
model = transformers.AutoModelForImageClassification.from_pretrained(model_name, use_auth_token=token)
print(model.config)
```
Bu kod, modelin yapılandırmasını yazdırır. Yapılandırma, diğer sınıflandırma modellerinin bir varyasyonudur.

### Yapılandırma Çıktısı
```json
BeitConfig {
  "_name_or_path": "Denis1976/autotrain-training-cifar-10-81128141661",
  "architectures": [
    "BeitForImageClassification"
  ],
  "attention_probs_dropout_prob": 0.0,
  "auxiliary_channels": 256,
  "auxiliary_concat_input": false,
  "auxiliary_loss_weight": 0.4,
  "auxiliary_num_convs": 1,
  "drop_path_rate": 0.1,
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
  "layer_scale_init_value": 0.1,
  "max_length": 128,
  "model_type": "beit",
  "num_attention_heads": 12,
  "num_channels": 3,
  "num_hidden_layers": 12,
  "out_indices": [
    3,
    5,
    7,
    11
  ],
  "padding": "max_length",
  "patch_size": 16,
  "pool_scales": [
    1,
    2,
    3,
    6
  ],
  "problem_type": "single_label_classification",
  "semantic_loss_ignore_index": 255,
  "torch_dtype": "float32",
  "transformers_version": "4.31.0",
  "use_absolute_position_embeddings": false,
  "use_auxiliary_head": true,
  "use_mask_token": false,
  "use_mean_pooling": true,
  "use_relative_position_bias": true,
  "use_shared_relative_position_bias": false,
  "vocab_size": 8192
}
```
## BEiT Modelinin Sınıflandırma Performansı
BEiT modeli, sis içindeki bir arabayı tanımlayabilir mi? Hadi deneyelim:
```python
model_name = "autotrain-training-cifar-10-81128141661"
output = query("car_in_fog.png", model_name)
classify_image(output)
```
Çıktı, bu eğitilmiş modelin de başarısız olduğunu gösteriyor:
```
score:0.8033 airplane
score:0.1801 ship
score:0.0121 truck
score:0.0045 automobile
Üzgünüm, bu görüntü sınıflandırılamıyor
Bir şeyler yapılması gerekiyor!
```
Swin mimarisinde eğitilen başka bir moda geçmeden önce durup düşünmemiz gerekiyor.

---

