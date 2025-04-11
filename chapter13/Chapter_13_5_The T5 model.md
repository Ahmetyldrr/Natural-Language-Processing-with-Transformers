# T5 Transformer Modelinin Giriş Formatının Standardizasyonu

Raffel ve ekibi (2019) metin çıktısı elde etmek için standart bir giriş formatı tasarlamaya odaklandı. Google T5 ekibi, BERT benzeri yalnızca kodlayıcı katmanları veya GPT benzeri yalnızca çözücü katmanları gibi Orijinal Transformer'dan türetilen yeni mimarileri denemek istemedi. Bunun yerine, ekip, Doğal Dil İşleme (NLP) görevlerini standart bir formatta tanımlamaya odaklandı. 

## T5 Modelinin Mimarisi

2. Bölüm'de, Transformer Modelinin Mimarisi ile Başlarken bölümünde tanımladığımız Orijinal Transformer modelini kullanmayı seçtiler, Şekil 13.4'te görebileceğimiz gibi:

Şekil 13.4: T5 tarafından kullanılan Orijinal Transformer modeli

Raffel ve ekibi (2019) Orijinal Transformer mimarisinin ve terimlerin çoğunu korudu. Ancak, bazı önemli yönleri vurguladılar. Ayrıca, bazı sözcük ve işlevsel değişiklikler yaptılar. Aşağıdaki liste T5 modelinin bazı ana yönlerini içerir:

* Kodlayıcı ve çözücü modelde kalır.
* Kodlayıcı ve çözücü katmanları "bloklar" haline gelir ve alt katmanlar bir kendi kendine dikkat katmanı ve bir feedforward ağı içeren "alt bileşenler" haline gelir.
* "Bloklar" ve "alt bileşenler" gibi LEGO benzeri bir dil kullanarak "blokları", parçaları ve bileşenleri birleştirerek modelinizi oluşturmanıza olanak tanır. 
* Transformer bileşenleri, birçok şekilde birleştirilebilen standart yapı taşlarıdır.
* Temel yapı taşlarını 2. Bölüm'de, Transformer Modelinin Mimarisi ile Başlarken bölümünde incelediğimiz için, herhangi bir transformer modelini anlayabilirsiniz.

## Kendi Kendine Dikkat ve Konumsal Kodlama

Kendi kendine dikkat "sıra bağımsızdır", yani işlemleri kümeler üzerinde gerçekleştirir, 2. Bölüm'de gördüğümüz gibi. Kendi kendine dikkat, matrislerin nokta ürünlerini kullanır, yinelemeyi değil. Bir dizideki her kelimenin diğerleriyle olan ilişkisini araştırır.

Konumsal kodlama, nokta ürünleri yapmadan önce kelimenin embedding'ine eklenir. Orijinal Transformer, sinüzoidal ve kosinüs sinyallerini transformer'a uyguladı. Veya, öğrenilen konum embedding'lerini kullandı. T5, girişe rastgele konumlar eklemek yerine göreceli konum embedding'lerini kullanır.

T5'te, konumsal kodlama, ikili ilişkiler arasında karşılaştırmalar yapmak için kendi kendine dikkatin bir uzantısına dayanır. Örneğin, "kedi fareyi kovaladı" cümlesinde, "kedi" kelimesi "fare"den üç konum uzaktadır. Göreceli konum, bir kelimenin başka bir kelimeyle olan ilişkisindeki konumunu yakalar. Mutlak konum, bir kelimenin bir dizideki konumunu (1, 2 veya x konumu) yakalar, 2. Bölüm'de gördüğümüz gibi. Daha fazla bilgi için, bu bölümün Referanslar bölümündeki Shaw ve ekibi (2018)'ye bakınız.

Konumsal embedding'ler paylaşılır ve modelin tüm katmanları boyunca yeniden değerlendirilir.

## T5 Modelinin Girişinin Standardizasyonu

T5 transformer modelinin girişinin standardizasyonunu metin-to-metin yaklaşımı ile tanımladık. Şimdi, T5'i belgeleri özetlemek için kullanalım.

Python kodları bulunmamaktadır, ancak dilerseniz T5 modelini kullanarak belge özetleme örneği için bir python kodu snippet'i ekleyebilirim. 

Örnek bir python kodu snippet'i:
```python
import torch
from transformers import T5Tokenizer, T5ForConditionalGeneration

# T5 modelini ve tokenizer'ı yükle
model = T5ForConditionalGeneration.from_pretrained('t5-small')
tokenizer = T5Tokenizer.from_pretrained('t5-small')

# Özetlenecek belgeyi tanımla
belge = "Özetlenecek belge buraya gelir..."

# Giriş verisini hazırla
input_ids = tokenizer.encode("summarize: " + belge, return_tensors="pt")

# Özeti oluştur
output = model.generate(input_ids, max_length=50)

# Özeti yazdır
print(tokenizer.decode(output[0], skip_special_tokens=True))
```

---

