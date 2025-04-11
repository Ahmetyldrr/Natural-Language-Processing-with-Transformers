# F-AGI'nın Bilinci ve Kapsamı
F-AGI'nin hiç bir şekilde bilinci yoktur. Ayrıca, F-AGI insan entelektüel aktivitesinin toplamı gibi her şeyi yapamaz. Bu bölümün ve kitabın kapsamı kesinlikle insanları değiştirmek ve iş kayması ve yer değiştirmeyi yaratmak değildir. Bu bölüm ayrıca zararlı içerikten uzak durur.

# F-AGI'nın Uygulama Alanları
F-AGI birçok alanda gerçekten insan seviyesinde varlıklar haline gelebilir, örneğin:
- İnsan görüşünü taklit ederek, insan varlığının olmadığı alanlarda yangın algılayıcıları kullanarak orman yangınlarını mümkün olan en kısa sürede tespit etmek. Kaliforniya eyalet genelinde yangın algılama kameraları kurmaya başladı. Hizmet, 7/24 uygulanması mümkün olmayan insan seviyesinde hizmetler sunar. Örneğin, Pano orman yangını yönetimi için AI destekli görüş hizmetleri sunar (Referanslar bölümüne bakınız).
- İnsan uzmanları her zaman mevcut olmadığında, insan görüşünü taklit ederek cilt kanseri tespiti yapmak. IBM birkaç yıl önce Avustralya'da bir cilt kanseri projesi başlattı. Avustralya, dünyadaki en yüksek melanom oranına sahiptir. Tahminlere göre her altı saatte bir Avustralyalı melanomdan ölüyor. İnsanlar bazen bir dermatologla randevu almak için haftalarca beklemek zorunda kalıyor. IBM erken cilt kanseri tespiti için hizmetler sunar (Referanslar bölümüne bakınız).
- Kritik koşullarda (örneğin, sisli bir yolda gece vakti araçta) insan görüşünü taklit ederek yardımcı sürüş (özerk değil) sağlamak. AI destekli sürüş birçok araç markasına eklendi. Biz burada araba reklamları yapmıyoruz, ne de özerk araçların sorunlarını çözeceğimizi iddia ediyoruz. Ancak, AI destekli sürüş gibi kapalı bir ortamda F-AGI'nın nasıl hayat kurtarabileceğini gösterebiliriz.

# Bu Bölümün Odak Noktası
Bu bölümün odak noktası aşağıdaki konular olacaktır:
- Zor bir görüntüde (video karesi simülasyonu) araç tanımlama problemini çözmek. Bu problem 18. Bölüm, Hugging Face AutoTrain: Kodlama Olmadan Görüş Modelleri Eğitimi'nde çözülememişti. Bu bölümde, bilgisayar görüşünün sınırlarını genişletmenin yollarını bulacağız.
- Zor görüntü tanıma problemini çözmek için HuggingGPT'nin felsefesini kullanmak. HuggingGPT, ChatGPT'yi kullanarak bir girdiyi analiz eder, Hugging Face model kartlarını ve özelliklerini okur ve birçok NLP ve görüş görevi için bir veya birkaç model etkinleştirir.

# Otomatik Model Seçimi ve Model Zincirleme
- Sistemleri bir platformun ötesine taşımak (örneğin, Google, Microsoft, OpenAI, Hugging Face, vb.) ve herhangi bir platformda model zincirleme yapmak. Bu bölümde, yenilikçi kodsuz platformların işlevselliğini kullanarak ve en iyi bilgisayar görüşü modelleriyle etkileşime girerek problemimizi çözeceğiz.
- Bu bölümün nihai amacı:
  - Sisli bir yolda gece vakti araç tanımlama problemini çözmek.
  - Otomatik model seçimi ve model zincirlemenin F-AGI'ya nasıl yol açacağını, bir modelin (örneğin, Google Cloud Vision) çıktısını başka bir modelin (örneğin, OpenAI) girdisi olarak kullanarak göstermek.
  - Hugging Face'in ChatGPT'yi etkin bir denetleyici olarak kullanarak, Hugging Face model kartlarını (ve özelliklerini) okuyarak ve bir görevi çözmek için bir veya birkaç model seçerek nasıl F-AGI'ya ulaştığını göstermek.

# HuggingGPT ve Eşitleri
- AutoML, HuggingGPT'den önce de vardı, Hugging Face'in platformunda da dahil. Ancak, ChatGPT'yi AutoML için bir denetleyici olarak tanıtmak cesur bir hareketti.
- Hugging Face, ChatGPT'yi bir denetleyici olarak kullanarak heterojen modelleri bir araya getirme kapısını açtı. Bu başarı büyük bir övgüyü hak ediyor. Biz bu kavramı daha da ileri götüreceğiz, bu kapıdan geçeceğiz ve araç tanımlama problemimizi çözmek için herhangi bir yararlı modeli ekleyeceğiz!

# Gerçek Hayat Projelerinde Uygulama
- Gerçek bir hayat projesinde, bir pipeline içinde çalıştırabileceğimiz modelleri seçmek için Google Vertex PaLM 2 gibi başka bir LLM'yi de kullanabiliriz.
- HuggingGPT zaten bir çapraz platform çözümüdür çünkü Hugging Face tokenına OpenAI tokenını eklemeyi gerektirir!
- Örneğin, Microsoft Bing'in sohbet aracı gibi istediğimiz LLM'yi kullanarak çapraz platform bir süreç uygulayabiliriz.

Örneğin, Bing'e bir görüntü sınıflandırabilen bir transformatör bilgisayar görüşü modeli adı ve ardından bilgisayar görüşü modelinin metin çıktısını analiz edebilen ve önerilerde bulunabilen bir transformatör LLM modeli adı sorabiliriz:
- Bir görüntü sınıflandırabilen bir transformatör bilgisayar görüşü modeli adı: Vision Transformer (ViT)
- Bilgisayar görüşü modelinin metin çıktısını açıklayabilen ve önerilerde bulunabilen bir transformatör LLM modeli: VisionEncoderDecoderModel

# Sonuç
- Bu bölümde, işi halletmek için ihtiyacımız olan her şeyi keşfedeceğiz. Keşfimizin kaydını tutmak için bir not defteri kullanacağız. Gerekli kütüphaneleri kurarak ve içe aktararak başlayalım.

Python kodları bulunmamaktadır, ancak kütüphaneleri kurmak ve içe aktarmak için aşağıdaki gibi bir kod kullanılabilir:
```python
# Kütüphaneleri kurmak
!pip install transformers

# Kütüphaneleri içe aktarmak
import transformers
from transformers import AutoModel, AutoTokenizer
```
Bu kod, `transformers` kütüphanesini kurar ve içe aktarır. İleriki adımlarda, spesifik modellere ve görevlere göre daha fazla kütüphane ve modül içe aktarılabilir.

---

