# Dönüştürücülerle İlgili Performans Seviyelerini Değerlendirme

Dönüştürücülerin (transformers) son teknoloji performans seviyelerine ulaştığını kanıtlamak için üç ön koşul gereklidir: 
- Bir model 
- Veri seti güdümlü bir görev 
- Bu bölümün Değerlendirme modelleri metriklerle başlıklı bölümünde açıklandığı gibi bir metrik 
Piyasada Google'ın BIG-bench (https://github.com/google/BIG-bench) gibi birçok kıyaslama ölçütü vardır ve biz bunu 15. Bölümde, Devleri Korumak: Büyük Dil Modellerinde Riskleri Azaltma, Fonksiyonel YZ Ortaya Çıkışı bölümünde kendi kendini değerlendirme amacıyla kullanacağız. Ancak, tüm kıyaslama ölçütlerini uygulamak mantıklı değildir. Dönüştürücülerle NLP görevlerinin potansiyelini anlamak için yeterli görevleri çalıştırmak önemlidir. Oradan, herhangi bir kıyaslama sistemine hızla uyum sağlayacaksınız. 
Değerlendirme sürecini bazı temel NLP görevleri aracılığıyla bir dönüştürücü modelinin değerlendirilmesiyle göstermek için SuperGLUE kıyaslamasını keşfederek başlayacağız.

## GLUE'den SuperGLUE'ye

Bir modelin performansını ölçmek için GLUE, SuperGLUE ve WMT (Makine Çevirisi Çalıştayı) gibi birçok NLP kıyaslaması uygulanabilir. 
WMT'yi 4. Bölümde, Google Trax, Google Translate ve Gemini ile Çevirilerdeki Gelişmeler bölümünde kullanacağız. 
Bu bölüm, SuperGLUE kıyaslamasına odaklanmaktadır. 
SuperGLUE kıyaslaması Wang ve diğerleri (2019) tarafından tasarlandı ve halka açıklandı. 
Wang ve diğerleri (2019) ilk olarak Genel Dil Anlama Değerlendirmesi (GLUE) kıyaslamasını tasarladılar. 
SuperGLUE'ye bakmadan önce, GLUE'yi kısaca keşfetmek faydalıdır.

### GLUE Kıyaslamasının Motivasyonu

GLUE kıyaslamasının motivasyonu, yararlı olmak için, NLU'nun geniş bir görev yelpazesine uygulanabilir olması gerektiğini göstermektir. 
Nispeten küçük GLUE veri setleri, bir NLU modelini bir dizi görevi çözmeye teşvik etmek için tasarlandı. 
Ancak, dönüştürücülerin ortaya çıkmasıyla NLU modellerinin performansı ortalama seviyeyi aşmaya başladı. 
https://gluebenchmark.com/leaderboard adresinde bulunan GLUE liderler tablosu, esas olarak çığır açan dönüştürücü modellerine odaklanan dikkate değer bir NLU yeteneği sergilemektedir. 
Liderler tablosu, bir modelin ihtiyaçlarımıza uygun olup olmadığını görmek için kıyaslama görevlerini anlamaktan ve uygulamaktan daha az anlam ifade etmektedir. 
Belirli projeler için veri setlerini geliştirebiliriz. 
İnsan taban çizgileri listenin oldukça aşağısındadır: 
Şekil 3.7: GLUE liderler tablosu Kasım 2023 
Yeni modeller ve İnsan Taban Çizgileri sıralaması sürekli değişecektir. 
İnsan Taban Çizgileri'nin konumu, Temel Modellerin ortaya çıkmasından bu yana artık pek bir şey ifade etmemektedir. 
Bu sıralamalar sadece klasik NLP ve dönüştürücülerin bizi ne kadar ileri götürdüğünü göstermektedir! 
GLUE İnsan Taban Çizgileri ilk sıralarda değildir, bu da NLU modellerinin GLUE görevlerinde uzman olmayan insanları aştığını gösterir. 
İnsan Taban Çizgileri, bizim insanların ulaşabileceği performansı temsil eder. 
Yapay zeka artık insanları geçebilir. 
Ancak, başvuracak bir standart olmadan modelimizi geliştirmek için kıyaslama veri setlerinde körü körüne gezinmek zordur. 
Ayrıca, 2020'lerden itibaren dönüştürücü modellerinin liderliği ele geçirdiğini fark ediyoruz. 
Bu eğilim devam edecektir, ancak yaratıcı yenilikçilerin ne bulacağını asla bilemeyiz! 
GLUE ve SuperGLUE'yi, kelimelerin kaostan düzene geçtiği ve dilin anlaşılmasıyla ilgili bir nokta olarak düşünmeyi seviyorum. 
Anlama, kelimeleri birbirine uyumlu hale getiren ve bir dil haline getiren "tutkal"dır. 
Şimdi, İnsan Taban Çizgileri için daha yüksek bir standart belirleyen SuperGLUE'ye bakalım.

### Daha Yüksek İnsan Taban Çizgileri Standartları Sunmak

Wang ve diğerleri (2019), GLUE'nin sınırlarını fark ettiler. 
Daha zor NLU görevleri için SuperGLUE'yi tasarladılar. 
SuperGLUE, İnsan Taban Çizgileri'nin konumunu iyileştirmeye yardımcı oldu; liderler tablosunun aşağıdaki alıntısında gösterildiği gibi (https://super.gluebenchmark.com/leaderboard): 
Şekil 3.8: SuperGLUE liderler tablosu 2.0 – Kasım 2023 
SuperGLUE liderler tablosu gelişmeye devam ediyor ve yapay zeka, temel NLP görevlerinin insan taban çizgilerini aşağıya doğru itmeye devam edecektir. 
İlk iki sıradaki modeller Şekil 3.5'te gösterilmemiştir; bunun iki nedeni vardır: 
- Şekil, en üstteki bazı özel Temel Modelleri içermemektedir. 
- Sıralama, SuperGLUE görevlerinde uzmanlaşmış modellerle sürekli olarak değişmektedir; bu görevler bir modelin ilk düzey değerlendirmesi için mükemmeldir. 
Ancak, bir seçim yapmak için modellere ihtiyaçlarınıza göre değerlendirme yapmanız gerekecektir. 
Evet, yeni yenilikçi modeller geldiğinde yapay zeka algoritması sıralamaları sürekli olarak değişecektir. 
Ancak, bu sıralamalar sadece NLP üstünlüğü için yapılan mücadelenin ne kadar zorlu olduğunu göstermektedir! 
SuperGLUE değerlendirme süreci, değişmeye devam edecek sıralamalardan daha önemlidir. 
Sizin için en iyi model, bir liderler tablosunda en iyi model olmak zorunda değildir. 
Bir NLP değerlendirme süreci öğrenmeniz ve bunu uygulayacağınız model(ler)e uygulammanız gerekir. 
Şimdi, değerlendirme sürecinin nasıl çalıştığını görelim.

## SuperGLUE Değerlendirme Süreci

Wang ve diğerleri (2019), SuperGLUE kıyaslamaları için NLP'nin pratik temsilci görevlerini seçtiler. 
Bu görevler için seçim kriterleri GLUE'ye göre daha katıydı; sadece metin anlama değil, aynı zamanda akıl yürütme yeteneklerini de vurguluyordu. 
Modeller için gerekli akıl yürütme seviyesi, üst düzey bir insan uzmanınınki değildir. 
Ancak, performans seviyesi birçok görevde insanları değiştirmeye yeterlidir. 
Ana SuperGLUE görevleri kullanıma hazır bir listede sunulmaktadır: 
Şekil 3.9: SuperGLUE görevleri 
Görev listesi etkileşimlidir: https://super.gluebenchmark.com/tasks . 
Her görev, o görevi gerçekleştirmek için gerekli bilgilere bağlantılar içerir: 
- Ad, ince ayarlı, önceden eğitilmiş bir modelin aşağı akış görevinin adıdır. 
- Tanımlayıcı, adın kısaltması veya kısa versiyonudur. 
- İndir, veri setlerine indirme bağlantısıdır. 
- Daha Fazla Bilgi, veri seti güdümlü görev(ler)i tasarlayan ekibin kağıt veya web sitesine bağlantı yoluyla daha fazla ayrıntı sunar. 
- Metrik, modeli değerlendirmek için kullanılan ölçüm skorudur. 
SuperGLUE, görev talimatlarını, yazılımı, veri setlerini ve çözülecek problemleri açıklayan makaleleri veya web sitelerini sağlar. 
Bir ekip, kıyaslama görevlerini çalıştırıp liderler tablosuna ulaştığında, sonuçlar görüntülenir: 
Şekil 3.10: SuperGLUE görev puanları 
SuperGLUE, genel puanı ve her görev için puanı gösterir. 
Örneğin, Wang ve diğerleri (2019) tarafından COPA (İnandırıcı Cevapların Seçimi) görevi için sağlanan talimatları ele alalım. 
İlk adım, Roemmele ve diğerleri (2011) tarafından yazılan dikkate değer makaleyi okumaktır. 
Kısacası, amaç NLU modelinin makine düşüncesi (insan düşüncesi değil, elbette) potansiyelini göstermesidir. 
Bizim durumumuzda, Dönüştürücü en makul cevabı seçmelidir. 
Veri seti bir önerme sağlar ve dönüştürücü model en makul cevabı bulmalıdır. 
Örneğin: 
Önerme: Komşumun kapısını çaldım. 
Sonuç olarak ne oldu? 
Alternatif 1: Komşum beni içeri davet etti. 
Alternatif 2: Komşum evinden ayrıldı. 
Bu soruyu cevaplamak bir insan için bir veya iki saniye sürer, bu da bir miktar makine düşüncesi gerektirdiğini gösterir. 
Hazır kullanıma uygun bir veri seti olan COPA.zip, doğrudan SuperGLUE görev sayfasından indirilebilir. 
Sağlanan metrik, kıyaslama yarışındaki tüm katılımcılar için süreci eşit ve güvenilir kılar. 
COPA testi, gelişmiş soru-cevap görevlerinin kapısını açar; 12. Bölümde göreceğiz. 
COPA'yı tanıttık. 
Şimdi diğer SuperGLUE kıyaslama görevlerinden bazılarını tanımlayalım. 

Bu metin python kodları içermemektedir.

---

