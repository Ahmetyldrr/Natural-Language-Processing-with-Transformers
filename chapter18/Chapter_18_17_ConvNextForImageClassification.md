# Liu ve Ekibi (2022) tarafından yapılan çalışma ve ConvNext Modeli

Liu ve diğerleri (2022), saf bir evrişimli ağın hibrit dönüştürücü modeller kadar iyi, hatta daha iyi performans gösterebileceğini kanıtlamak için ConvNext'i yarattılar. ConvNext modeli aşağıdaki bileşenlerden oluşur:

*   Giriş görüntüsünden özellikler çıkaran bir kök katman (stem layer).
*   Dört aşamadan oluşan bir dizi.
*   Her bir aşama, bir dizi dönüştürücü bloklarından oluşur.
*   Her bir dönüştürücü bloğu, bir kendi kendine dikkat katmanı (self-attention layer), bir evrişimli katman ve bir artık bağlantı (residual connection) içerir.
*   Giriş görüntüsü için sınıf olasılıklarını çıktı olarak veren bir sınıflandırma başlığı (classification head).

ConvNext modelinin sınıflandırma başlığı, aşamaların çıktısını girdi olarak alır ve bir sınıf olasılıkları vektörü çıktısı verir. Vektördeki sınıf sayısı, modelin eğitildiği veri kümesindeki sınıf sayısına bağlıdır.

Aşağıdaki kod ile modelin konfigürasyonunu görselleştirebiliriz:

```python
model_name = "Denis1976/autotrain-training-cifar-10-81128141663"
model = transformers.AutoModelForImageClassification.from_pretrained(model_name, use_auth_token=token)
print(model.config)
```

Bu kod, önceden eğitilmiş bir modeli yükler ve konfigürasyonunu yazdırır.

# Model Konfigürasyonu

Çıktı, sınıflandırma işlevselliğine sahip bir evrişimli ağ gösterir:

```json
ConvNextConfig {
  "_name_or_path": "Denis1976/autotrain-training-cifar-10-81128141663",
  "architectures": [
    "ConvNextForImageClassification"
  ],
  "depths": [
    3,
    3,
    9,
    3
  ],
  "drop_path_rate": 0.0,
  "hidden_act": "gelu",
  "hidden_sizes": [
    96,
    192,
    384,
    768
  ],
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
  "layer_norm_eps": 1e-12,
  "layer_scale_init_value": 1e-06,
  "max_length": 128,
  "model_type": "convnext",
  "num_channels": 3,
  "num_stages": 4,
  "out_features": [
    "stage4"
  ],
  "out_indices": [
    4
  ],
  "padding": "max_length",
  "patch_size": 4,
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

# Modelin Sınıflandırma Performansının Değerlendirilmesi

Bu evrişimli ağ modeli bir arabayı bulabilir mi? Bu soruyu cevaplamak için, modelin sınırını adım adım değerlendireceğiz.

İlk olarak, siste bir araba görüntüsünü deniyoruz:

```python
model_name = "autotrain-training-cifar-10-81128141663"
output = query("car_in_fog.png", model_name)
classify_image(output)
```

Model başarısız oluyor:

```
score:0.5243 ship
score:0.3771 airplane
score:0.0838 truck
score:0.0149 automobile
```

Bu görüntü sınıflandırılamadı.

Daha sonra, daha az zor olan gece araba görüntüsünü deniyoruz:

```python
model_name = "autotrain-training-cifar-10-81128141663"
output = query("car_in_night.jpg", model_name)
classify_image(output)
```

Model bu daha az zor görüntüde de başarısız oluyor:

```
score:0.4904 airplane
score:0.2331 automobile
score:0.2075 ship
score:0.069 truck
```

Bu görüntü de sınıflandırılamadı.

Son olarak, siyah arka plan üzerinde beyaz bir araba bulunan en kolay görüntüyü deniyoruz:

```python
model_name = "autotrain-training-cifar-10-81128141663"
output = query("/content/generate_an_image_of_a_car_in_space.jpg", model_name)
classify_image(output)
```

Model arabayı tanıyor:

```
score:0.8055 automobile
score:0.1242 airplane
score:0.0411 ship
score:0.0291 truck
```

Artık, eğitilmiş bir modelin algılama seviyesini belirlemek için zorluk seviyesi 3 (çok zor), 2 (zor) ve 1 (kolay) olan küçük bir veri kümesi oluşturduk.

---

