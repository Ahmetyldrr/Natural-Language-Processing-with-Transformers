# Küçük Veri Setimizi En İyi Sıralamaya Sahip Eğitilmiş Model Üzerinde Çalıştırma

Şimdi küçük veri setimizi en üst sıralarda yer alan eğitilmiş model üzerinde çalıştıracağız: 
```python
model_name = "Denis1976/autotrain-training-cifar-10-81128141658"
model = transformers.AutoModelForImageClassification.from_pretrained(model_name, use_auth_token=token)
```
- Yukarıdaki kodda `transformers` kütüphanesini kullanarak `AutoModelForImageClassification` sınıfından bir model oluşturuyoruz. 
- `from_pretrained` metodu ile daha önceden eğitilmiş bir modeli yüklüyoruz. 
- `model_name` değişkeni modelin adını, `use_auth_token` parametresi ise kimlik doğrulama token'ını temsil ediyor.

İlk olarak çok zor olan 3. seviyedeki görüntü ile başlıyoruz: 
```python
model_name = "autotrain-training-cifar-10-81128141659"
output = query("car_in_fog.png", model_name) 
# car_in_fog.png görüntüsünü sınıflandır
classify_image(output)
```
- `query` fonksiyonu bir görüntü dosyasını (`car_in_fog.png`) belirtilen model ile sınıflandırıyor.
- `classify_image` fonksiyonu sınıflandırma sonucunu işliyor.

Model bu seviyede başarısız oluyor:
```
score:0.5376 ship
score:0.4026 airplane
score:0.0336 truck
score:0.0262 automobile
```
Üzgünüz, bu görüntü sınıflandırılamadı.

Şimdi, 2. seviyedeki görüntü ile deneyelim: 
```python
model_name = "autotrain-training-cifar-10-81128141658"
output = query("car_in_night.jpg", model_name)
classify_image(output)
```
- Yine `query` fonksiyonu ile `car_in_night.jpg` görüntüsünü sınıflandırıyoruz.

Çıkarım başarılı oldu!
```
score:0.5064 automobile
score:0.2387 ship
score:0.1574 airplane
score:0.0975 truck
```

Son olarak, kolay olan görüntüyü tekrar deniyoruz: 
```python
model_name = "autotrain-training-cifar-10-81128141659"
output = query("/content/generate_an_image_of_a_car_in_space.jpg", model_name)
classify_image(output)
```
- `/content/generate_an_image_of_a_car_in_space.jpg` görüntüsünü sınıflandırıyoruz.

Çıktı başarılı:
```
score:1.0 automobile
score:0.0 truck
score:0.0 airplane
score:0.0 ship
```

Artık bir görüntü sınıflandırma modelini ölçmek için küçük bir standardımız var. Üretime geçmeye karar verirsek, aşağıdaki adımlara ihtiyacımız olacak:

- Modeli daha kapsamlı ve çeşitli bir veri seti ile eğitmek.
- Modeli zorlayabilmek için 2. seviye (zor) ve 3. seviye (çok zor) görüntüleri ayrı dizinlerde eklemek.
- Kontrol edemediğimiz limitler hakkında son kullanıcıları uyarmak.

Bu durumda, ne beklememiz gerektiğini biliyorduk. Ancak açık bir ortamda, her türden rastgele görüntülerle bu lükse sahip olmayacağız. Profesyonel bir proje yöneticisi, bu not defterindeki deneylerden fazla sonuç çıkaramaz. Hugging Face modelleri daha büyük veya optimize edilmiş bir veri seti ile daha iyi sonuçlar üretebilir. Ayrıca, diğer modelleri de deneyebiliriz. Platform, veri seti ve model seçimi her projenin hedeflerine bağlıdır. Her durumda, insan AI profesyonellerine bir süre daha uzmanlık ve yardım sağlamak için ihtiyaç duyulacaktır!

---

