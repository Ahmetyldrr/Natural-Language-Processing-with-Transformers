# Bölüm 7: ChatGPT ile Üretken Yapay Zeka Devrimi

Bizi GPT asistanları ve API'leri dünyasına götürdü. Üretken Yapay Zeka dönüştürücüsünü, genel amaçlı teknolojiyi etkileşimler ve kod aracılığıyla inceledik. Keşfettiğimiz tüm teknoloji bu kadar etkili ise neden zahmet edelim ki? Neden hazır çözümleri kullanıp öğrenmeyi, veri hazırlamayı, parametreleri yapılandırmayı ve belge yazmayı unutmayalım? Cevap oldukça basit. GPT-3 veya GPT-4 gibi genel amaçlı bir model projemiz için ihtiyaç duyduğumuz doğruluk eşiğine ulaşmadığında ne yapabiliriz? Bir şeyler yapmalıyız. Ama ne? Bu bölümde, bir proje için bu yönde gitmeye karar verirken yapabileceğimiz seçimleri anlamak için ince ayar yapmayı keşfedeceğiz. Risk yönetimi perspektiflerini tanıtacağız. Bu bölümde, bu seçeneği keşfetmek için bir OpenAI GPT modelini ince ayar yapacağız. Bir tamamlama görevi için maliyet etkin Babbage-002 modelini ince ayar yapacağız. OpenAI tarafından gerekli olan formatta veri kümeleri hazırlayacağız. Bu adım aldatıcı bir şekilde kolay görünüyor. Ancak, veri kümeleri hazırlamak oldukça zor olabilir. Daha sonra OpenAI'nin ince ayar hizmetini başlatacağız. İnce ayar hizmeti birkaç dakika veya bir kuyrukta bekliyorsak daha uzun sürebilir. OpenAI'de depolanan ince ayarlı modellerimizi görüntüleyebiliriz. Son olarak, özel ince ayar işleriniz için bu seçeneği seçmeye karar verirseniz, Immanuel Kant'ın çalışmasıyla bir tamamlama görevi çalıştıracağız. Bölümün sonunda, eksiksiz bir ince ayar süreci oluşturmuş olacaksınız.

Bu bölüm aşağıdaki konuları kapsar:
- OpenAI'de ince ayar modellerinin iyileştirmeleri ve sınırlamaları
- Veri kümesi hazırlama
- OpenAI'nin dosya formatı
- JSON dosyalarını JSONL'ye dönüştürme
- OpenAI GPT modelini ince ayar yapma
- İnce ayarlı modeli çalıştırma
- Bir tamamlama görevi çalıştırma (üretken)
- Çıktıları karşılaştırmak için GPT-4'ü çalıştırma

Bu son teknoloji alanında yapılan tüm yenilikler ve kütüphane güncellemeleri ile paketler ve modeller düzenli olarak değişmektedir. Lütfen en son kurulum ve kod örnekleri için GitHub deposuna gidin: https://github.com/Denis2054/Transformers-for-NLP-and-Computer-Vision-3rd-Edition/tree/main/Chapter08 . Ayrıca, bu veya herhangi bir bölümdeki kodu çalıştırırken herhangi bir sorun yaşarsanız Discord topluluğumuza bir mesaj gönderebilirsiniz ( https://www.packt.link/Transformers ). Yolculuk, OpenAI'yi bir risk yönetimi perspektifinden incelemekle başlar.

Python kodları bulunmamaktadır, ancak ilerleyen kısımlarda kod örneği varsa satır satır açıklama yapılacaktır. Şimdilik, yukarıdaki metin verilen İngilizce paragrafın birebir Türkçe çevirisidir.

---

