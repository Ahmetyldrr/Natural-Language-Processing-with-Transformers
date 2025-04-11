# İngilizce Paragrafın Türkçe Çevirisi

Arayüzdeki car_in_night.jpg görüntüsünün çıktısı sadece bir özellik içerir: Araba (Şekil 19.10): 
Şekil 19.10: Gece bir arabanın Google Cloud Vision analizi 
Daha fazla araştırmak için bir metin dosyasına saklanan JSON çıktısını almamız gerekir: 
```bash
!curl -L https://raw.githubusercontent.com/Denis2054/Transformers_3rd_Edition/master/Chapter19/GCV2.json --output "GCV2.json"
```
JSON dosyasını yükleyelim ve ayrıştıralım:
```python
import json
with open("GCV2.json") as f:
    # Dosyayı açar ve içeriğini json.load() fonksiyonuna geçirir.
    data = json.load(f)
    # "labelAnnotations" anahtarına karşılık gelen değeri alır.
labels = [] 
for label in data["labelAnnotations"]:
    # Her bir label'ın "description" ve "score" değerlerini labels listesine ekler.
    labels.append([label["description"], label["score"]])
    # labels listesini DataFrame'e çevirir.
df = pd.DataFrame(labels, columns=["description", "score"])
    # DataFrame'i döndürür.
df
```
Çıktı çok ilginç özellikler gösterir:
Şekil 19.11: Modelin gece araba analizi 
Bir arabanın özelliklerini ama aynı zamanda yolun özelliklerini de görebiliriz. 
Artık araç ve yol özelliklerine dair daha fazla bilgi edindik. 
Sonunda çok zor bir görüntü ile sonuç elde edecek miyiz?

# Python Kodlarının Satır Satır Açıklaması

## JSON Dosyasını Yükleme ve Ayrıştırma

1. `import json`: json modülünü içe aktarır. Bu modül JSON verilerini işlemek için kullanılır.
2. `with open("GCV2.json") as f:`: "GCV2.json" dosyasını açar ve `f` değişkenine atar. `with` ifadesi dosya işlemleri için kullanılır ve dosya işlemleri bittikten sonra otomatik olarak dosyayı kapatır.
3. `data = json.load(f)`: `f` değişkenindeki dosyayı json.load() fonksiyonuna geçirir ve JSON verilerini Python nesnelerine çevirir.

## LabelAnnotations'ı İşleme

1. `labels = []`: Boş bir liste oluşturur.
2. `for label in data["labelAnnotations"]:`: `data` değişkenindeki "labelAnnotations" anahtarına karşılık gelen değeri alır ve her bir label'ı döngüye sokar.
3. `labels.append([label["description"], label["score"]])`: Her bir label'ın "description" ve "score" değerlerini `labels` listesine ekler.

## DataFrame Oluşturma

1. `df = pd.DataFrame(labels, columns=["description", "score"])`: `labels` listesini DataFrame'e çevirir ve sütun isimlerini "description" ve "score" olarak atar.
2. `df`: DataFrame'i döndürür.

---

