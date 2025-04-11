# Yapay Zeka Sınırında: Otomasyon ve Bilgisayarlı Görü

Bu bölüm bizi otomasyonun hüküm sürdüğü yapay zeka sınırına getirdi. Dünyadaki rakipler, yapay zekayı ana akım kullanıcılar için erişilebilir hale getirmek için mücadele ediyorlar. OpenAI'ın ChatGPT'si, otomatik görevlerin akışına kapı açtı. Hugging Face, platformlarında çok sayıda otomatik işlevi başarıyla devreye aldı, transformerları çalıştırmayı kolaylaştırdı ve diğer birçok üretken işlevi sağladı. Hugging Face AutoTrain, yapay zeka modellerini eğitmek ve dağıtmak için kodlama gerektirmeyen bir hizmet sunar. Bir Hugging Face Space ile bir görüntü sınıflandırma projesi oluşturarak başladık. Ulaşım görüntüleri içeren bir CIFAR-10 veri kümesini yükledik. Daha sonra modelleri zor ve kolay bir araba görüntüsüyle çalıştırarak devam ettik. Öncelikle modelleri sorgulamak için bir API işlevi ve üretilen puanları görüntülemek için bir çıktı işleme işlevi oluşturduk. Keşfedilen modeller ViT, Swin, BEiT, ConvNext ve ResNet idi. Bölüm not defteri, her modelin yapılandırmasını kısa bir model açıklaması eşliğinde görüntüledi. Modellerin doğrulukları mükemmel olsa da, modeller sisli bir gecede bir araba görüntüsünü tespit edemedi. Bilgisayarlı görü modellerini uygulamanın kritik bir yönü, en etkili modellerin bile sınırlarını kabul etmekte yatmaktadır. Sınır aşıldığında, önce bir modelin ne yapabileceğini ve ne yapamayacağını tanımlamak için bilimsel bir yaklaşım oluşturmanın bir yolunu bulmalıyız. Böylece, sonunda, sınıflandırmak için kolay, zor ve çok zor bir araba görüntüsü içeren bir mini doğrulama kümesi oluşturduk. En iyi modelimiz, Denis1976/autotrain-training-cifar-10-81128141658, kolay ve zor görüntülerde bir arabayı başarıyla tespit etti. Ancak sisli görüntüdeki çok zor arabayı tespit edemedi. Gerçek hayattaki bir ulaşım görüntüsü çıkarım projesinde, klasik kümelerin (arabalar, uçaklar, gemiler ve kamyonlar) ötesinde her kategori için birçok temsili görüntü içeren kapsamlı veri kümeleri oluşturmalıyız (kolay, zor ve çok zor). Bazı durumlarda, yapay zeka uzmanı olmayan bir kişi, Hugging Face AutoTrain'i engelle karşılaşmadan başarıyla kullanabilir. Ancak, bir yapay zeka projesini mükemmel veri kümeleri, doğru modeller ve mükemmel performanslarla otomatik hizmetler aracılığıyla harika bir yolculuk olarak özetleyemeyiz. Bunu kimsenin inandırıcı bulması etik olmaz. Herhangi bir yapay zeka projesi gibi, başarılı bir bilgisayarlı görü projesi de problem çözme becerileri, hayal gücü ve sabır gerektirir! Bu bölümde eğitilen modellerden daha iyisini yapabilecek başka modeller veya yöntemler var mı? Deneylerimize Bölüm 19'da, HuggingGPT ve Eşdeğerleri ile Fonksiyonel YZ Sınırında devam edeceğiz.

Python kodları bulunmamaktadır, ancak metinde Hugging Face AutoTrain ve diğer AI kütüphanelerinin kullanımından bahsedilmektedir. 

Eğer python kodları olsaydı, satır satır açıklama şu şekilde olurdu:
Örneğin aşağıdaki kod bloğu için:
```python
# Modeli yükleme
from transformers import ViTForImageClassification, ViTFeatureExtractor

model_name = "google/vit-base-patch16-224-in21k"
model = ViTForImageClassification.from_pretrained(model_name)
feature_extractor = ViTFeatureExtractor.from_pretrained(model_name)
```
Açıklama:
1. `from transformers import ViTForImageClassification, ViTFeatureExtractor`: transformers kütüphanesinden ViTForImageClassification ve ViTFeatureExtractor sınıflarını içe aktarıyoruz.
2. `model_name = "google/vit-base-patch16-224-in21k"`: Kullanılacak modelin adını belirliyoruz.
3. `model = ViTForImageClassification.from_pretrained(model_name)`: Belirtilen model adıyla ViTForImageClassification modelini yüklüyoruz.
4. `feature_extractor = ViTFeatureExtractor.from_pretrained(model_name)`: Belirtilen model adıyla ViTFeatureExtractor'ı yüklüyoruz.

Bu şekilde her satır için açıklama yapılabilir. Ancak bu metinde python kodları bulunmamaktadır.

---

