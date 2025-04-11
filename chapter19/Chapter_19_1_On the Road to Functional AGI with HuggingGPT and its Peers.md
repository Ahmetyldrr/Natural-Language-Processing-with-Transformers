# Fonksiyonel Genel Yapay Zeka (F-AGI)

Fonksiyonel Genel Yapay Zeka (F-AGI), kapalı bir ortamda insanları işyerinde geride bırakabilecek yeterli kapsamdaki görevlerin otomasyonudur. F-AGI terimini, bir yapay zeka sisteminin yeteneklerini ve iş kayıpları ile ilgili riskleri tanımlamak için kullanıyoruz. Risklerin ötesinde, bir başka faktör kritik hale geldi: hacim. İnsan faaliyetleri, hizmetler, ürünler ve iletişim kaynakları üretmek için milyonlarca mikro-karar gerektirir. F-AGI, gereklilikten doğmuştur. F-AGI terimi, duyusal, bilinçli, insansı bir yapay zeka ajanı mitiyle karıştırılmaktan kaçınır. F-AGI, kapsamını bir işyerindeki kapalı bir alanla sınırlar. Bir F-AGI, 24/7 çalışabilir. Günde milyonlarca görevi çözebilir. Yangın önleme, karbon emisyonlarını azaltmak için uçuş planlaması ve sınırsız bir çeşitlilikteki üretken faaliyetler gibi kritik durumlarda paha biçilmez olduğunu kanıtlayacaktır.

Microsoft, Google, OpenAI, Hugging Face ve diğerleri, AGI'ye doğru yolculuklarında Temel Modellerin kapsamını genişlettiler. ChatGPT gibi bir Temel Model, yüzlerce görevi yerine getirebilir, bazıları henüz yaratıcı kullanıcılar tarafından keşfedilmeyi bekliyor. Ancak, yükü neden tek bir modele bırakalım? Neden bir bilim kurgu filmindeki gibi bir süper "zeki" yapay zeka ajanına odaklanalım? Neden bir modelden muazzam veri ve donanım kaynakları gerektiren her şeyi yapmasını bekleyelim? Neden belirli bir görev için en iyi dönüştürücü modelini etkinleştiren merkezi bir denetleyici oluşturmayalım? Shen ve diğerleri (2023), tam olarak böyle bir sistem tasarladılar ve buna HuggingGPT adını verdiler. Hugging Face, iyi tanımlanmış model kartlarına sahip sayısız model barındırır. ChatGPT, dil anlama, model kartlarını okuma ve diğer parametrelerin yanı sıra belirli bir görev için en iyi modelleri seçme konusunda tuhaf bir yeteneğe sahiptir. HuggingGPT'nin yazarları, HuggingFace ChatGPT'yi barındırdıkları modellerle birleştirerek AGI'ye verimli bir yol icat ettiler.

Bu bölüm, bilgisayarlı görüdeki bazı örneklerle net F-AGI faaliyetlerini tanımlayarak başlar. Bu bölüm, karmaşık problemleri çözmek için birkaç yapay zeka modeliyle çalışmanın benzersiz üretkenliğini anlamayı amaçlar. Daha sonra, 18. Bölüm'de çalıştırdığımız doğrulama veri setini indireceğiz, Hugging Face AutoTrain: Kodlama olmadan Vizyon Modelleri Eğitimi. 18. Bölüm'de, modeller sis içindeki bir aracın çok zor görüntüsünü tanımlayamadı. Ancak, sürüş asistanları kesinlikle bilgisayarlı görmenin sınırlarını zorlamayı ve bu sorunu çözmeyi öğrenmelidir. Bu bölüm, bu hedefe başarıyla ulaşmak için yenilikçi yollar açacaktır.

HuggingGPT, önce bir modeli veya zor, kolay ve çok zor görüntüleri tanımlayabilen modelleri bulacaktır. Sis içindeki bir arabanın çok zor görüntüsüne de denk gelebilir. Ancak, HuggingGPT'nin yaklaşımı bölümün geri kalanını ilham verecektir. Daha sonra, kolay, zor ve çok zor görüntüleri tanımlamak için Google Cloud Vision'ı çalıştıracağız. Zor görüntü zorluğunu koruyacak, ancak bu bölümde sorunu çözeceğiz. Klasik yaklaşımların dışına çıkmaya devam edeceğiz. Her rekabetçi platformun kendi kapsamı vardır. Peki ya bir sistemi daha da ileri götürüp, rekabeti görmezden gelip, rakip modelleri birlikte çalışmaya zorlasak? Böylece, klasik ardışık düzenlerin ötesine geçip, heterojen rekabetçi modelleri zincirleme konusunda nasıl ilerleyeceğimizi keşfedeceğiz. Bir yapay zeka bilgisayarlı görme çıktısının, Google Cloud Vision gibi, HuggingGPT veya hatta OpenAI'ın ChatGPT'sinin girdisi olabileceğini göstereceğiz. Sonunda, sis içindeki araba zorluklarımız, çapraz platform, zincirleme model ardışık düzeni sayesinde çözülecek!

Tabii ki, sonuç, tüm çok zor görüntülerin tanımlanabileceği anlamına gelmeyecek. Ancak bu bölümün sonunda, karmaşık sorunlarla karşı karşıya kaldığında bir modelin sınırlarını nasıl genişleteceğinizi öğreneceksiniz. Bu bölüm aşağıdaki konuları kapsar:

*   F-AGI Tanımlama
*   F-AGI'nin net durumlarının kullanımını tanımlama
*   Otonom bir araç için vizyon modelleri için bir doğrulama seti test etme
*   Doğrulama görüntülerini alma
*   HuggingGPT'nin zor görüntüler için potansiyelini keşfetme
*   Nesne tespiti ile çıkarım yapma
*   Google Cloud Vision'ın zor görüntüler için potansiyelini keşfetme
*   ChatGPT'nin anlamsal analiz gücünü kullanarak karmaşık nesne tespiti sorunlarını çözme
*   Model zincirleme ile çözüm sağlama
*   Model zincirlemeyi Midjourney ve Gen-2 ile örnekleme

Bu son teknoloji alanındaki tüm yenilikler ve kütüphane güncellemeleri ile paketler ve modeller düzenli olarak değişmektedir. Lütfen en son kurulum ve kod örnekleri için GitHub deposuna gidin: https://github.com/Denis2054/Transformers-for-NLP-and-Computer-Vision-3rd-Edition/tree/main/Chapter19 . Ayrıca, bu veya herhangi bir bölümdeki kodu çalıştırırken herhangi bir sorun yaşarsanız Discord topluluğumuza bir mesaj gönderin ( https://discord.com/invite/Fp4XXhECdh ).

İlk adımımız, F-AGI'nin kapsamını tanımlamak olacaktır.

Bu çeviride python kodları bulunmamaktadır.

---

