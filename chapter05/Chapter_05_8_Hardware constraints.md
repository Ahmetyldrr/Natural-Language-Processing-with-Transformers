# Dönüşüm Ölçeği ve Donanım Gereksinimi

Dönüştürücü modelleri eğitmek ve ince ayar yapmak için gereken hesaplama ölçeği, onları donanım odaklı hale getirir. Bu, hızla bir kaynak kısıtlamasına dönüşür. Küçük dönüştürücü modeller yerel makinelerde veya sınırlı sunucu yapılandırmalarında eğitilebilir ve ince ayar yapılabilir. Ancak, son teknoloji büyük OpenAI modelleri ve Google AI modelleri gibi büyük modeller benzersiz makine gücüne ihtiyaç duyar. Büyük Dil Modelleri (LLM'ler) tarafından gereken makine gücü, finansal erişilebilirlik eşiği oluşturdu. Bu nedenle, Hugging Face dönüştürücü modellerini keşfetmek ve uygulamak için makul bir giriş noktası sunar. Dönüştürücü modeller böylece GPU'ların paralel işleme yeteneğinden yararlanır. GPU'lar, hesaplama görevlerini CPU'lardan çok daha verimli bir şekilde gerçekleştirir ve eğitim veya ince ayar sürecini hızlandırır.

# GPU Kullanımı

Google Colab'da Çalışma Zamanı menüsüne gidin, Çalışma zamanı türünü değiştir'i seçin ve Donanım Hızlandırıcı açılır listesinde GPU'yu seçin. Program, daha sonra kuracağımız Hugging Face modüllerini kullanacaktır.

Python kodları içermediğinden, çeviri ve markdown düzenlemesi dışında bir açıklama yapılmamıştır. Çeviri birebir yapılmıştır.

Eğer python kodları olsaydı, her bir satır için açıklama yapılacaktı. Örneğin:

```python
# bir kod satırı olsaydı
import torch  # torch kütüphanesini içe aktarır
```

Bu şekilde açıklama yapılırdı. Ancak metinde python kodları bulunmamaktadır.

---

