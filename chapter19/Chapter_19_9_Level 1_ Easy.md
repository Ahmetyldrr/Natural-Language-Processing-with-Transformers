# Google Cloud Vision Çıktısı
Google Cloud Vision, doğrulama setindeki generate_an_image_of_a_car_in_space.jpg için Şekil 19.8'de gösterildiği gibi ilginç bir çıktı üretir: 
Şekil 19.8: Google Cloud Vision'un uzaydaki bir araba analizi
Google Cloud Vision, sonuçlara atlamakta isteksiz görünüyor. Bir araba tespit ediyor, ancak tekerlekler ve lastik de ekliyor.

## JSON Çıktısının Analizi
Çıktıyı analiz etmek için, işlemin JSON çıktısını bir dosyaya kopyaladıktan sonra ayrıştırabiliriz: 
```bash
!curl -L https://raw.githubusercontent.com/Denis2054/Transformers_3rd_Edition/master/Chapter19/GCV.json --output "GCV.json"
```
Bu komut, belirtilen URL'deki JSON dosyasını "GCV.json" olarak kaydeder.

## JSON Verisinin Okunması ve DataFrame'e Dönüştürülmesi
Not defteri, çıktıyı bir pandas DataFrame'de açabilir ve görüntüleyebilir:
```python
with open("GCV.json") as f:
    data = json.load(f)
```
Bu kod, "GCV.json" dosyasını açar ve içeriğini `data` değişkenine yükler.

```python
labels = []
for label in data["labelAnnotations"]:
    labels.append([label["description"], label["score"]])
```
Bu döngü, `data` içindeki "labelAnnotations" anahtarına karşılık gelen liste üzerinden dolaşır ve her bir `label` için "description" ve "score" değerlerini `labels` listesine ekler.

```python
df = pd.DataFrame(labels, columns=["description", "score"])
df
```
Bu satırlar, `labels` listesini "description" ve "score" sütunlarıyla bir pandas DataFrame'e dönüştürür ve DataFrame'i görüntüler.

## Model Çıktısının İncelenmesi
Bu şekilde, görme modelinin çıktısına daha iyi bir bakış açısı kazanabiliriz:
Şekil 19.9: Modelin uzaydaki araba analizi
18. Bölüm'de çalıştırdığımız sınıflandırma görevi modellerinin aksine, Hugging Face AutoTrain: Kodlama Olmadan Görme Modelleri Eğitimi, Google Cloud Vision bir sınıf yerine bu görüntü için bir özellik listesi görüntüler, ki bu ilginç bir yaklaşımdır. Liste, görüntüdeki araba hakkında özellikler içerir. Çıktı, modelin görüntü analiz ederken ürettiği en yüksek olasılıkları gösterir. Bu bilgi, modelin nasıl çıkarımlar yaptığına dair içgörüler sağlar.

## Zor Görüntünün Çıktısı
Zor görüntünün çıktısı ne üretecek?

---

