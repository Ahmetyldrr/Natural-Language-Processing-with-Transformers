# Hugging Face Platformunun Kullanımı

Hugging Face platformu, yapay zeka pazarına uyum sağlamak için sürekli olarak güncellenmekte ve değiştirilmektedir. Arayüzler, rekabet ve kullanıcı geri bildirimleri aracılığıyla sürekli olarak gelişmektedir. Bu bölüm, süreci tanımlar ve işi halletmek için bağlantılar sağlar. Süreçlere odaklanın. Arayüz sürekli olarak gelişecektir. Modern yapay zeka, uyum sağlama ve sürekli öğrenme gerektirir. Platformda herhangi bir şeyi etkinleştirmeye başlamadan önce Hugging Face'in otomatik eğitim koşullarını ve bu hizmetin maliyetini okuduğunuzdan emin olun.

## İlk Adımlar

Başlamak için önce Hugging Face'in AutoTrain platformuna gidin: https://huggingface.co/autotrain. Hugging Face'in "kod olmadan güçlü modeller oluşturma" konusunda ısrar ettiğini göreceksiniz. Talimatları takip ettiğinizden emin olun, bunlar da gelişecektir ancak zaman ayırmaya değer. Hugging Face tokeninizi elde ettiğinizden emin olun.

## Profesyoneller için Fırsatlar

Yapay zeka profesyoneli, zaman ve enerji tasarrufu fırsatını görür. Yapay zeka dışı profesyonel ise sevinir! Şimdi, herkes için ilk engel ortaya çıkıyor: hızlı bir şekilde yeni bir proje oluşturmak ve modeli eğitmeye başlamak. Ya da aşağıdakileri gerektiren gelişmiş bir proje seçmek:
- Bir Alan oluşturmak ve HF_TOKEN'unuzu tokeninizle ayarladığınızdan emin olmak: demo'yu barındıracak bir Git deposu.
- Alanınız için bir Yazılım Geliştirme Kiti (SDK) seçmek: Streamlit, Gradio, Static veya Docker, bir Docker şablonu ile birlikte.
- Donanım seçimi. CPU'lar ücretsizdir. Büyük bir veri kümeniz varsa saat başına ücretlendirilen bir GPU'ya ihtiyacınız olacaktır.
- Alanınızı oluştururken AutoTrain seçeneğini seçmek.
- Projenin herkese açık mı yoksa özel mi olacağına karar vermek.

## Yeni Proje Oluşturma

Ve işte! Kodlamayan bir yapay zeka dışı profesyonel, gelişmiş bir eğitim projesine başlamak için bir yapay zeka profesyonelinin yardımına ihtiyaç duyacaktır. Modeli eğitmek için bir Alan kullanmak istiyorsanız, Hugging Face tarafından sağlanan çok iyi ifade edilmiş talimatları takip edin.

Diyelim ki yapay zeka dışı profesyonel doğrudan yeni bir proje oluşturmaya gidiyor ve önce bir Alan oluşturuyor. Şekil 18.1'de gösterildiği gibi "Yeni proje oluştur" üzerine tıklıyoruz:

### Şekil 18.1: Yeni Proje Oluşturma

Süreç, diğer birçok yenilikçi bulut yapay zeka platformu gibi gelişebilir. Arayüz değişebilir, ancak yeni bir proje oluşturmanız gerekecektir. Geekler için eğlenceli görünebilir, ancak diğerleri için değil. Her durumda, bu hızlı hareket eden çağa uyum sağlamalıyız!

"Yeni Proje" üzerine tıkladığınızda, bir proje formu doldurmanız istenecektir. Talimatları dikkatlice takip edin. Proje adınızı girin ve bu proje için bir görüntü sınıflandırma görevi etkinleştirmek üzere "vision" seçeneğini seçin. Bir model seçebilir veya sistemin sizin için yapmasına izin verebilirsiniz. Hugging Face, sistemin karar vermesine izin vermenizi önerir. Projenizi oluşturmak için onay düğmesine tıklayın.

## Eğitim Süreci

Eğitim süreci iki ana adımdan oluşur:
1. Veri yönetimi
2. Eğitim aşaması

Veriyle başlayacağız.

Python kodları bulunmamaktadır, ancak ileride eğer eklenmesi gereken bir python kodu varsa satır satır açıklanacaktır. Şimdilik, metin sadece Hugging Face platformunun kullanımı hakkında bilgi vermektedir.

---

