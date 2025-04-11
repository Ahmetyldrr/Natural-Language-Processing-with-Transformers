# Makine Öğrenimi Modeli Eğitmek
Makine öğrenimi modeli eğitmek artık üniversite diploması gerektirmiyor. Yapay zeka veya programlama bilgisi olmayan biri bir transformatör modeli eğitebilir. Hugging Face'in AutoTrain'i kodlama gerektirmez. Sadece verilerinizi yüklemeniz gerekir. AutoTrain daha sonra verileri otomatik olarak işler ve projeniz için bir veya birkaç model seçer ve eğitir. Daha sonra eğitilen modeli birkaç tıklamayla dağıtabilirsiniz. Google AI Platform AutoML, Amazon SageMaker Autopilot, Microsoft Azure Machine Learning, IBM Watson Studio ve diğer birçok platformda benzer hizmetler bulabilirsiniz. Birkaç yıldan daha kısa bir süre içinde, herkes yıllarca üniversitede AI alanında doktora yapmış biriyle rekabet edebilir. Otomatik makine öğrenimi platformları, ChatGPT gibi güçlü bir yardımcı pilot ve bir kredi kartı ile herkes bir AI mühendisiyle rekabet edebilir.

# Bu Bölümün Amacı
Bu bölüm, hiç makine öğrenimi bilgisi veya deneyimi olmayan herkesin bir görüntü transformatörünü nasıl eğitebileceğini gösterecektir. Ancak, sürecin her adımında, bir sorun ortaya çıktığında üniversite diplomasının gerekli içgörüyü sağlayacağını da görüyoruz. Ve AI gibi karmaşık bir alanda, işler genellikle yanlış gider! 

# Hugging Face AutoTrain ile Proje Oluşturma
CIFAR-10 ulaşım görüntüleri üzerinde bir görüntü sınıflandırma modeli eğitmek için Hugging Face'in AutoTrain'ini kullanarak bir proje oluşturarak başlayacağız. Verileri eğitim ve doğrulama veri kümelerine ayırdıktan sonra AutoTrain arayüzüne yükleyeceğiz. Daha sonra AutoTrain'in kabul edilebilir ila yüksek doğrulukla birkaç model eğitme yeteneğini etkinleştireceğiz. AutoTrain'in kapsamlı metrikleri eğitilen modelleri sıralayacaktır. Son olarak, modeli bazı görüntüleri test etmek için dağıtacağız ve çalıştıracağız.

# Otomatik Makine Öğrenimi Platformlarının Sınırları
Bir AI uzmanı gibi bir araba sigorta poliçesi gibidir. Çoğu zaman hiçbir şey için çok para ödediğimizi düşünürüz. Ancak kötü bir şey olduğunda, poliçemize güveniyoruz. Bu bölümde, AI projelerinin, otomatik olsun veya olmasın, her zaman AI uzmanlarının çözmesi gereken sorunları olduğunu göstereceğiz. Otomatik eğitim sürecinden geçeceğiz ve neden otomatik makine öğreniminin bile insan AI uzmanlığına ihtiyacı olduğunu gösteren öngörülemeyen sorunları keşfedeceğiz.

# Bu Bölümde İşlenecek Konular
* Hugging Face AutoTrain
* Yeni bir AutoTrain projesi oluşturma
* Bir Alan (Space) oluşturma
* Veri kümesi yükleme
* Bir eğitim stratejisi seçme
* AutoTrain'i çalıştırma
* Doğrulama görüntülerini alma
* Görüntü sınıflandırma ile çıkarım yapma
* Eğitilen modelleri keşfetme
* Eğitilen modellerin sınırlarını araştırma
* Eğitilen modellerin sınırlamalarını yönetme

# Kod Örnekleri ve Güncellemeler
Bu son teknoloji alanında birçok yenilik ve kütüphane güncellemesi ile paketler ve modeller düzenli olarak değişmektedir. Lütfen en son kurulum ve kod örnekleri için GitHub deposuna gidin: https://github.com/Denis2054/Transformers-for-NLP-and-Computer-Vision-3rd-Edition/tree/main/Chapter18 . Bu veya herhangi bir bölümdeki kodu çalıştırırken herhangi bir sorunuz varsa Discord topluluğumuza bir mesaj gönderin ( https://www.packt.link/Transformers ).

# İlk Adım
İlk adımımız, bu bölümde Hugging Face AutoTrain uygulamasının kapsamını ve amacını tanımlamak olacaktır.

Python kodları bulunmamaktadır, ancak ilgili GitHub deposu ve Discord topluluğu linkleri verilmiştir.

---

