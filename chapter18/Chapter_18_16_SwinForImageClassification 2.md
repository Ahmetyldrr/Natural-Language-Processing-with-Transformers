# Otomatik Eğitim Deneyinin Sınırları

Şimdiye kadar, eğitilen tüm modeller bir otomobilin sis içindeki görüntüsünü tanımlayamadı, ancak bu durum otonom bir araç için sıkça karşılaşılan bir durumdur. Bu bölümde, SwinForImageClassification 1 bölümünde Swin'in konfigürasyonunu kısaca gözden geçirdik. Bu bölümde, bu Otomatik Eğitim deneyinin sınırlarına odaklanacağız. Bazı temel düşünceler ortaya çıkıyor: CIFAR-10 veri kümesi üzerinde eğitim yapmak yüksek doğruluk sağlayacak mı, ancak genelleme yeteneği zayıf olacak mı? Eğitilen modeller aşırı uyuma kurban mı oldu? Model mimarileri yeterli mi? Bu modelleri sıfırdan eğitmedik. Önceden yeterince eğitildiler mi? Karanlık ve sisli ortamlarda araçları tanımlamak için daha iyi bir veri kümesi sağlanmalı mıydı? Modeller daha iyi sınıflandırılır mıydı? Bu sorulara matematiksel veya bilimsel cevaplar yoktur. Dönüştürücülerin eğitimi, iyileştirme için ampirik deneme yanılmaya dayanır. Bu soruları cevaplamak proje, hedef ve sorunları çözmek için mevcut kaynaklara bağlı olacaktır. Yine de Swin'in bu versiyonunu deneyeceğiz: 
```python
model_name = "Denis1976/autotrain-training-cifar-10-81128141657"
model = transformers.AutoModelForImageClassification.from_pretrained(model_name, use_auth_token=token)
```
Sis içindeki araba görüntüsü gönderilir:
```python
model_name = "autotrain-training-cifar-10-81128141657"
output = query("car_in_fog.png", model_name)
classify_image(output)
```
Çıktı, modelin arabayı tanımlayamadığını gösterir:
```
score:0.6011 airplane
score:0.1972 ship
score:0.1781 truck
score:0.0237 automobile
```
Üzgünüm, bu görüntü sınıflandırılamıyor. 
Bu mesaj şimdi çoğu etkileşimli AI sitesinde olduğu gibi bir reddi beyan olarak görünüyor. 
Gecenin karanlığında belirgin bir araba olan bir görüntüyü ve bir sis görüntüsünü indirebiliriz:
```bash
# Üretim aşamasına geçerken silinecek geliştirme erişimi
!curl -L https://raw.githubusercontent.com/Denis2054/Transformers_3rd_Edition/master/Chapter18/car_in_night.jpg --output "car_in_night.jpg"
```
İnsanlar bu görüntü gösterildiğinde arabayı daha iyi ayırt edebilir mi?
```python
from PIL import Image

# Görüntünün yolu
image_path = "/content/car_in_night.jpg"

# Görüntüyü aç
image = Image.open(image_path)
image
```
Çıktı, gecenin karanlığında ve sis içinde bir araba olduğunu açıkça gösterir:
# Şekil 18.16: Sisli bir gecede araba görüntüsü

Eğitilen modelimiz bu kez arabayı tanımlayabilecek mi?
```python
model_name = "autotrain-training-cifar-10-81128141657"
classify_image(output)
```
Hayır, model yine bariz bir araba görüntüsünde başarısız oldu! 
Çıktı:
```
score:0.8055 automobile
score:0.1242 airplane
score:0.0411 ship
score:0.0291 truck
```
Aşağıdaki bölümde, modelin sınırını bulmak için bir yol tasarlamamız gerekiyor.

---

