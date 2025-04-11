# Google Cloud Vision'ın car_in_fog.jpg Görüntüsü için Ürettiği Sonuçlar

Google Cloud Vision'ın car_in_fog.jpg görüntüsü için ürettiği sonuçlar nelerdir? Çıktı, Şekil 19.22'de gösterildiği gibi kafa karıştırıcıdır: 
Şekil 19.12: Siste bir araba görüntüsünün çıktısı 
Kolay ve zor görüntülerden farklı olarak, görme modeli arabanın etrafında düzgün bir dikdörtgen çizmedi. Hava koşulları üst sıralarda yer alıyor. Ancak, görüntünün özelliklerinden biri %85 güven seviyesiyle bir araçtır. Bu, umut verici bir adım ileriye doğru. 

### JSON Çıktısını Ayrıştırma

Önce JSON çıktısını bir dosyaya kopyalayalım: 
```bash
!curl -L https://raw.githubusercontent.com/Denis2054/Transformers_3rd_Edition/master/Chapter19/GCV3.json --output "GCV3.json"
```
Şimdi, özellikleri bir pandas DataFrame'de görüntüleyebiliriz:
```python
import json
with open("GCV3.json") as f:
    # Dosyadan JSON verilerini yükler
    data = json.load(f)

labels = []
for label in data["labelAnnotations"]:
    # Her bir label için açıklama ve skor değerlerini labels listesine ekler
    labels.append([label["description"], label["score"]])

# labels listesinden bir DataFrame oluşturur
df = pd.DataFrame(labels, columns=["description", "score"])
df
```
### Çıktının Analizi

Çıktı, bir araba için iki özellik içerir: araç ve otomotiv aydınlatması. Hava koşulları üst sıralarda yer alıyor: 
Şekil 19.13: Modelin çok zor bir gece araba görüntüsünü analiz etmesi 

Bu deneyin sonucu oldukça ilginçtir, göreceğiz. Bu çıktıyı okuyan bir insan, modelin açıkça çıkarımda bulunmamasına rağmen, bir aracın kötü hava koşullarında sürmekte olduğu sonucuna varacaktır. Şimdi, özel bir cross-platform sistemi uygulayacağız.

---

