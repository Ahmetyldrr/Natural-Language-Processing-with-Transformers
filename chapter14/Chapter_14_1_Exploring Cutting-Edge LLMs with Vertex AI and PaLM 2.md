# Belki 7. Bölüm, ChatGPT ile Üretken Yapay Zeka Devrimi, Büyük Dil Modelleri (LLM'ler) ve Üretken Yapay Zeka'nın muazzam ilerlemesinin sonunun geldiğini düşündürdü.
Belki de GitHub Copilot, GPT-4 ve OpenAI'ın embedding modelleri gibi inanılmaz araçlar, bir sınıra ulaştığımıza inanmamıza neden oldu. Ardından, 23 Mayıs 2023'te Google, önceki PaLM ve Pathways makalelerine dayanan PaLM 2 Teknik Raporu'nu yayınladı. Bu makalelerin içeriği akıllara durgunluk veriyor! PaLM'in mimarisi, dahiyane yeniliklerle hem yazılım hem de donanım performansını geliştirdi.

## Bu Bölümde Neler Öğreneceğiz?
Bu bölüme, PaLM'i anlamak için Pathways'i inceleyerek başlayacağız. Daha sonra, 540 milyar parametre ile eğitilmiş, Google'ın Pathways sistemi üzerinde eğitilmiş, yalnızca kod çözücü, yoğun olarak etkinleştirilmiş ve otoregresif model transformatör modeli olan PaLM'in (Pathways Dil Modeli anlamına gelir) ana özelliklerine bakacağız. PaLM, 780 milyar token üzerinde eğitildi.

### PaLM 2
Bir sonraki adım, ölçeklendirme yasalarını tanıtarak ve model boyutunu ve parametre sayısını optimize ederek daha fazla makine verimliliği nasıl sağladığını keşfetmek olacak. PaLM 2 performansları, OpenAI GPT-4'e benzer sonuçlar elde ediyor. Bir proje için hangisinin daha iyi olduğunu belirlemeye çalışmayacağız çünkü her model bir NLP görevi için daha iyi performans gösterebilirken diğerinde gösteremeyebilir. PALM 2'nin performansları etkileyici! PaLM 2'nin daha iyi versiyonlara yol açacağı kesin.

#### Pathways, PaLM ve PaLM 2 Mimarisi
Pathways, PaLM ve PaLM 2 mimarisini anladığınızda, bir sonraki gelişmelere hazır olacaksınız. Daha sonra, Google'ın son teknoloji transformatörleri tarafından desteklenen harika ve etkili yeni asistanları inceleyeceğiz. Gemini, Google Workspace'te Google Dokümanlar, Google Colab Copilot ve AI PaLM 2 çevrimiçi ortamında Üretken Yapay Zeka tarafından desteklenen asistanları çalıştıracağız.

##### Google'ın Üretken Yapay Zeka Asistanları
Gemini API'sini kendisi hakkında sorular soracağız. Google PaLM 2'nin bir sohbet görevi, bir ayırt edici görev (sınıflandırma gibi), bir tamamlama görevi (üretken görev olarak da bilinir) ve daha fazlasını nasıl gerçekleştirebileceğini göreceğiz. Daha sonra, Vertex AI PaLM 2 API'sini birkaç NLP görevi için uygulayacağız, bunlar arasında Soru-Cevap, özetleme ve daha fazlası var.

###### Vertex AI PaLM 2 API'si
Son olarak, Google Cloud'un ince ayar sürecini inceleyeceğiz. Bu bölümün sonunda, transformatör tarafından desteklenen Üretken Yapay Zeka asistanlarına ve API'lerine bağımlı hale geleceksiniz!

### Bu Bölümde İşlenen Konular
- Pathways mimarisi
- PaLM mimarisi
- PaLM 2 mimarisi
- Google'ın transformatör tarafından desteklenen Üretken Yapay Zeka asistanları
- Gemini
- Google Workspace asistanı for Google Dokümanlar
- Google Colab Copilot
- Vertex AI PaLM 2 çevrimiçi sohbet ve kod botları
- Vertex AI PaLM 2 ile ayırt edici ve üretken görevler
- Vertex AI PaLM 2 API'sini uygulamak
- Soru-Cevap, özetleme, duygu analizi ve Bison ile çoklu seçim görevleri
- Kod oluşturma PaLM 2
- Bir Google LLM'sini ince ayarlamak

Bu alandaki tüm yenilikler ve kütüphane güncellemeleri ile paketler ve modeller düzenli olarak değişmektedir. Lütfen en son kurulum ve kod örnekleri için GitHub deposuna gidiniz: https://github.com/Denis2054/Transformers-for-NLP-and-Computer-Vision-3rd-Edition/tree/main/Chapter14 . Bu veya herhangi bir bölümdeki kodu çalıştırırken sorun yaşarsanız, Discord topluluğumuza bir mesaj gönderin ( https://www.packt.link/Transformers ).

## Yolculuğumuza Başlamak
PaLM tarafından elde edilen yenilikçi adımları keşfederek yolculuğumuza başlayacağız, ki bu da Pathways üzerine kuruludur.

Bu metinde Python kodları bulunmamaktadır.

---

