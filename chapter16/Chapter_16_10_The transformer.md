# Ön İşlemden Geçirilmiş Görüntünün ViT Modeline Beslenmesi

Ön işlemden geçirilmiş görüntü daha sonra ViT modeline (ViTForImageClassification) beslenir, bu da logitleri çıktı olarak verir. Logitler, modelin son katmanının sınıflandırma görevindeki her sınıf için ham, normalleştirilmemiş skorlarıdır. Bu logitler daha sonra softmax fonksiyonu kullanılarak olasılıklara dönüştürülebilir ve en yüksek olasılığa sahip sınıf genellikle modelin tahmini olarak alınır.

# ViT Modelinin Girişi ve İşlemesi

Özellik çıkarıcının ön işlemden geçirilmiş görüntüsü ViT'nin girişi olur:
```python
model = ViTForImageClassification.from_pretrained('google/vit-base-patch16-224')
inputs = feature_extractor(images=image, return_tensors="pt")
```
Transformatör daha sonra özellik çıkarıcının çıktısını yalnızca kodlayıcı yığınında işler. Gerekirse, ViT'nin çok yakından takip ettiği Orijinal Transformatör'ün tam mimarisini 2. Bölüm, Transformatör Modelinin Mimarisi ile Başlarken bölümünde gözden geçirmek için zaman ayırın. Transformatör, özellik çıkarıcı tarafından sağlanan gömmeleri işler, dikkat katmanından ve feedforward ağ katmanından geçer ve ham logitler çıktısını üretir:
```python
inputs = feature_extractor(images=image, return_tensors="pt")
outputs = model(**inputs)
logits = outputs.logits
```
# Çıktının İşlenmesi ve Tahmin

Çıktının ham logitleri, bu görüntü sınıflandırma sürecinin akışını kontrol eden ardışık düzen tarafından işlenecektir. Bir softmax fonksiyonu uygulanabilir veya önce sıcaklık, sonra softmax ve ardından top_k ve top_p gibi, örneğin 14. Bölüm, Vertex AI ve PaLM 2 ile Keskin Kenarlı LLMLeri Keşfetme, Vertex AI PaLM 2 arayüzü bölümünde gördüğümüz gibi. Ardışık düzen şimdi ham çıktıları bir tahmine dönüştürür ve seçilen olasılığın etiketini üretir:
```python
# model, 1000 ImageNet sınıfından birini tahmin eder
predicted_class_idx = logits.argmax(-1).item()
print("Tahmin edilen sınıf:", predicted_class_idx, ": ", model.config.id2label[predicted_class_idx])
```
# Tahmin Sonuçları

Çıktı, görüntü sınıflandırma görevinin sonucunu gösterir:
```
Tahmin edilen sınıf: 627:  limuzin, limo
```
Tahmin, uzayda bir araba veya limuzin gibi görünen bir şeyi gönderdiğimiz göz önüne alındığında kabul edilebilir. Artık ViT'nin ana bileşenlerini incelediğimize göre, daha da ileri gidip işlediğimiz tensörlerin şekillerini ve içeriklerini inceleyebiliriz.

---

