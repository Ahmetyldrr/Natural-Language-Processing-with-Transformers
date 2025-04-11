# Programın İlk Adımları

Program önce transformers kütüphanesini kurar ve içe aktarır:
```python
!pip install transformers -qq
import transformers
```
İki tür Hugging Face tokeni, modeli halka açık hale getirmeye karar verene kadar özel bir model için gerekli olacaktır. Hugging Face API tokeninizi başkalarının göremeyeceği güvenli bir dosyada sakladığınızdan emin olun:
```python
f = open("drive/MyDrive/files/HF_TOKEN.txt", "r")
HF_TOKEN = f.readline()
f.close()
```
# Token İşlemleri

`HF_TOKEN` değişkeninden yeni satır karakterini kaldırın:
```python
HF_TOKEN_Bearer = HF_TOKEN.strip()
```
`HF_TOKEN` değişkeninden 'Bearer ' önekini kaldırın:
```python
token = HF_TOKEN.replace('Bearer ', '').strip()
```
`HF_TOKEN`, 'Bearer ' önekini ve daha sonra oluşturmanız gereken Hugging Face API tokenini kullanır, eğer repository'niz özel ise ve bazı Hugging Face fonksiyonları için. `token`, 'Bearer ' önekini kullanmaz ve yalnızca oluşturmanız gereken Hugging Face API tokenini içerir.

# Modeli Çalıştırma

Modeli çalıştırmak için bir yol, `requests` kullanarak bir API URL'si üzerinden geçmektir:
```python
import requests
BASE_URL = "https://api-inference.huggingface.co/models/Denis1976"
headers = {"Authorization": HF_TOKEN_Bearer}  # Bearer gerektirir
```
Bu örnekte, eğitilmiş modellerden birini çalıştıracağız: `autotrain-training-cifar-10-81128141658`. Program, istek fonksiyonunu tanımlar:
```python
def query(filename, model_name, base_url=BASE_URL, headers=headers):
    api_url = f"{base_url}/{model_name}"
    with open(filename, "rb") as f:
        data = f.read()
    response = requests.post(api_url, headers=headers, data=data)
    return response.json()
```
# Çıktı İşleme

Model ilk çağrıldığında bazen bir gecikme olur. Hücreyi çalıştırın. Model henüz yüklenmediyse, birkaç saniye veya bir dakika sonra tekrar deneyin. Program ayrıca çıktıyı işleyecek, skorları gösterecek ve eğer araç ("otomobil") resimlerinden biri sınıflandırılamazsa bir mesaj gösterecek bir çıktı işleme fonksiyonu tanımlar:
```python
def classify_image(output):
    # Skorların ve etiketlerin listesini oluşturun
    scores = []
    labels = []
    for item in output:
        scores.append(item['score'])
        labels.append(item['label'])
    # Skorları sıralayın
    scores, labels = zip(*sorted(zip(scores, labels), reverse=True))
    # Skorları ve etiketleri alt alta yazdırın
    for score, label in zip(scores, labels):
        print(f"score: {round(score, 4)} {label}")
    # En üstteki skorun "otomobil" olmadığını kontrol edin
    top_label = labels[0]
    if top_label != "automobile":
        print("Üzgünüm, bu resim sınıflandırılamıyor")
```
# Modeli Kullanma

Şimdi modele bir çıkarım yapmasını sorabiliriz. Modelin yüklenmesini beklemeniz gerekebilir ve hücreyi yeniden çalıştırın.
```python
model_name = "autotrain-training-cifar-10-81128141657"
output = query("generate_an_image_of_a_car_in_space.jpg", model_name)
classify_image(output)
```
Çıktı doğru:
```
score:0.9983 automobile
score:0.0009 airplane
score:0.0006 ship
score:0.0001 truck
```
Şimdi zorlu resim:
```python
model_name = "autotrain-training-cifar-10-81128141657"
output = query("car_in_fog.png", model_name)
classify_image(output)
```
Model, bir insan kolayca tanımlayabilse de, bir aracı tanımlayamıyor:
```
score:0.6011 airplane
score:0.1972 ship
score:0.1781 truck
score:0.0237 automobile
Üzgünüm, bu resim sınıflandırılamıyor
```
İnsan, aracı kesinlikle bir uçak olarak yorumlamaz! Eğitilmiş modellere daha fazla araştırma yapmamız ve çıktıları değerlendirmemiz gerekiyor.

---

