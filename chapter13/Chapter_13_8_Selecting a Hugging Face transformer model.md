# Bu Alt Bölümde T5 Modeli Seçimi
Bu alt bölümde, bu bölümde uygulayacağımız T5 modelini seçeceğiz. Şekil 13.5'te görülebileceği gibi, Hugging Face modelleri sayfasında çok çeşitli modeller bulunabilir: 
Şekil 13.5: Hugging Face modelleri 
Bu sayfada, https://huggingface.co/models , bir T5 modeli arayabiliriz. Bizim durumumuzda, Google Colaboratory'de sorunsuz bir şekilde çalıştırabileceğimiz bir model olan t5-large modelini arıyoruz. Öncelikle bir T5 modeli aramak için T5 yazarız ve seçebileceğimiz bir T5 modelleri listesi elde ederiz: 
Şekil 13.6: T5 modeli arama 
Siteyi aradığımızda, birkaç T5 transformer'ın mevcut olduğunu görebiliriz, bunlar arasında:
- base, temel modeldir. 12 katman ve yaklaşık 220 milyon parametre ile BERT BASE'e benzer şekilde tasarlanmıştır.
- small, 6 katman ve 60 milyon parametre ile daha küçük bir modeldir.
- large, 12 katman ve 770 milyon parametre ile BERT LARGE'e benzer şekilde tasarlanmıştır.
- 3B ve 11B, yaklaşık 2.8 milyar ve 11 milyar parametre ile 24 katmanlı kodlayıcı ve kod çözücü kullanır. 
BERT BASE ve BERT LARGE modellerinin açıklamaları hakkında daha fazla bilgi için, 5. Bölüm, BERT ile İnce Ayarlama'ya göz atabilirsiniz. 
T5 modelleri ve Google'ın T5 modelleri üzerine yaptığı araştırmalar hakkında daha fazla bilgi için: https://huggingface.co/docs/transformers/main/en/model_doc/t5#transformers.T5Model . 
Bizim durumumuzda, t5-large modelini seçiyoruz: 
Şekil 13.7: Hugging Face modeli nasıl kullanılır 
Şekil 8.7, modeli kodumuzda nasıl kullanacağımızı gösterir. Ayrıca modeldeki dosya listesine ve temel yapılandırma dosyasına da göz atabiliriz. Modeli bu bölümün T5-large transformer modelini başlatma kısmında başlattığımızda yapılandırma dosyasına bakacağız. T5 transformer modelini başlatarak başlayalım.

Python kodları bulunmamaktadır, eğer kodları açıklama isterseniz lütfen belirtiniz. 

Eğer Başka bir işlem yapmamı istersen lütfen belirt.

---

