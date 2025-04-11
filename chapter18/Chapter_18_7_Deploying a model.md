# Hugging Face Model Kartı ve Model Yayınlama

En son sürekli değişen belgeleri okuduğunuzdan emin olun ve en son Hugging Face arayüzlerini keşfedin. Arayüz değişebilir, ancak modeliniz için bir model kartı oluşturmanız gerekecektir. Profilimize gidip eğitilmiş modellerimizden birinin model kartını seçerek modelin ayarlarına erişebilir ve nasıl dağıtılacağına karar verebiliriz, Şekil 18.11'de gösterildiği gibi: 
## Şekil 18.11: Eğitilmiş bir modelin model kartı

Bir dağıtım yöntemi seçebiliriz: örneğin, bir uç nokta oluşturmak için AWS gibi bir platformda dağıtabilir veya doğrudan transformer'larda modeli çalıştırabiliriz. Bu bölümde, modelleri doğrudan transformer'ları kullanarak çalıştıracağız. Öncelikle model kartına giderek, ardından Ayarlar'a giderek her modeli herkese açık hale getirmemiz gerekiyor, Şekil 18.12'de gösterildiği gibi:
## Şekil 18.12: Hugging Face modelini herkese açık hale getirme

Herkese açık yap'ı tıklamak modelinizi herkese açık hale getirecektir (Şekil 18.13):
## Şekil 18.13: Model görünürlük durumu

Şimdi, modelleri değerlendirmeyi başlatmak için en hızlı yol olarak Hugging Face tarafından sunulan barındırılan çıkarım hizmetlerini kullanacağız.

Bu çeviride python kodları bulunmamaktadır. 

Eğer ingilizce metinde python kodları olsaydı, satır satır açıklama verebilirdim. 

Örneğin eğer aşağıdaki gibi bir kod olsaydı:
```python
model = AutoModelForSequenceClassification.from_pretrained("model_name")
```
Açıklaması şu şekilde olurdu:
- `model = AutoModelForSequenceClassification.from_pretrained("model_name")` satırında, `AutoModelForSequenceClassification` sınıfını kullanarak önceden eğitilmiş bir model yükleniyor. 
- `from_pretrained` methodu, Hugging Face model deposundan "model_name" adıyla kayıtlı modeli indirir ve yükler.
- Yüklenen model, `model` değişkenine atanır. 

Ancak verdiğiniz metinde python kodları bulunmamaktadır.

---

