# Metin Birebir Çevirisi
İlk yedi bölüm boyunca, çeşitli transformer ekosistemlerinin mimarisi, eğitimi, ince ayarları ve kullanımı hakkında bilgi edindik. 7. Bölüm'de, yani "ChatGPT ile Üretken Yapay Zeka Devrimi"nde, OpenAI'ın ince ayar veya geliştirme gerektirmeyen ve birkaç satır kodla uygulanabilen sıfır-shot modelleriyle deneyler yapmaya başladığını keşfettik. Bu tür bir evrimin altında yatan kavram, transformerların bir makineye dili anlamayı ve kendini insan gibi ifade etmeyi öğretmeye nasıl çalıştığına dayanmaktadır. Böylece, bir modeli eğitmekten makinelere dil öğretmeye geçtik. ChatGPT, New Bing, Gemini ve diğer son kullanıcı yazılımları özetleyebilir, peki neden T5 ile uğraşalım? Çünkü Hugging Face T5, projeniz için doğru çözüm olabilir, göreceğimiz gibi. Özetleme için görev spesifik parametreler gibi benzersiz özelliklere sahiptir. Raffel ve ekibi (2019), basit bir iddia üzerine dayanan bir transformer meta-modeli tasarladılar: her NLP problemi metin-den-metne bir fonksiyon olarak temsil edilebilir. Her tür NLP görevi, bir tür metin yanıtı üreten bazı metin bağlamları gerektirir. Herhangi bir NLP görevinin metin-den-metne temsili, bir transformerın metodolojisini ve pratiğini analiz etmek için benzersiz bir çerçeve sağlar. Fikir, bir transformerın dil öğrenmesi için, eğitim ve ince ayar aşamalarında metin-den-metne yaklaşımıyla transfer öğrenme yoluyla olmasıdır. Raffel ve ekibi (2019), bu yaklaşımı bir Metin-Den-Metin-Transfer-Transformerı olarak adlandırdı. 5 T, T5 oldu ve yeni bir model doğdu. Bu bölüme, T5 transformer modelinin kavramlarını ve mimarisini inceleyerek başlayacağız. Daha sonra T5'i Hugging Face modelleriyle belgeleri özetlemek için uygulayacağız. Bu bölümdeki örnekler, basit metinlerin ötesinde alan-specifik özetlemeyi keşfetmek için yasal ve tıbbi olacaktır. NLP'yi uygulamanın kolay bir yolunu aramıyoruz, kendimizi gerçek hayat projelerinin gerçekliği için hazırlıyoruz. Daha sonra T5 ve ChatGPT yaklaşımlarını özetleme konusunda karşılaştıracağız. Amaç, her modelin özetlemeyi nasıl öğrendiğini anlamak, bir modelin diğerinin performansını aşığını iddia etmek değil. Seçim, NLP projesi gereksinimlerine bağlı olacaktır. Son olarak, OpenAI ChatGPT GPT-4 API'si ile özetlemek için bir not defteri oluşturacağız. Örnek, insan uzmanlığının kritik rolünü gösterecektir.

# Bu Bölümde İşlenecek Konular:
- Metin-den-Metin transformer modelleri
- T5 modellerinin mimarisi
- T5 metodolojisi
- Transformer modellerinin eğitimden öğrenmeye evrimi
- Hugging Face transformer modelleri
- T5 modelini uygulamak
- Yasal bir metni özetlemek
- Finansal bir metni özetlemek
- T5 ve ChatGPT modellerini karşılaştırmak
- OpenAI ChatGPT GPT-4 API'si ile özetlemeyi uygulamak

Bu son teknoloji alanında yapılan tüm yenilikler ve kütüphane güncellemeleri nedeniyle, paketler ve modeller düzenli olarak değişmektedir. Lütfen en son kurulum ve kod örnekleri için GitHub deposuna gidin: https://github.com/Denis2054/Transformers-for-NLP-and-Computer-Vision-3rd-Edition/tree/main/Chapter13 . Bu veya herhangi bir bölümdeki kodu çalıştırırken herhangi bir sorunuz varsa, Discord topluluğumuza bir mesaj göndermekten çekinmeyin ( https://www.packt.link/Transformers ). İlk adımımız, Raffel ve ekibi (2019) tarafından tanımlanan metin-den-metin metodolojisini keşfetmek olacaktır.

## Python Kodları İçin Satır Satır Açıklama Bulunmamaktadır, Çeviride Kod Geçmemektedir.

---

