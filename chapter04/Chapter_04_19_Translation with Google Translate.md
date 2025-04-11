# Google Çeviri ve Yapay Zeka Uygulamaları

Google Çeviri (https://translate.google.com/), çeviriler için kullanıma hazır resmi bir arayüz sağlar. Google, çeviri algoritmalarında dönüştürücü teknolojisine de sahiptir. Ancak, bir Yapay Zeka uzmanına hiç gerek olmayabilir. Önceki bölümde analiz edilen cümleyi Google Çeviri'ye girersek, "Levez-vous svp pour cette minute de silence", gerçek zamanlı olarak İngilizce çevirisini elde ederiz: 

## Şekil 4.2: Google Çeviri

Çeviri doğru. Yapay Zeka endüstrisi hala çeviri görevleri için Yapay Zeka uzmanlarına mı ihtiyaç duyuyor yoksa sadece bir web arayüzü geliştiricisine mi? Google, Google Çeviri platformunda çeviriler için gerekli her hizmeti sağlar: https://cloud.google.com/translate 
- Bir çeviri API'si: Bir web geliştiricisi bir müşteri için arayüz oluşturabilir.
- Akış içeriğinizi çevirebilen bir medya çeviri API'si.
- Belirli bir alan için özel bir model eğitecek bir AutoML çeviri hizmeti.

Bir Google Çeviri projesi, arayüzler için bir web geliştiricisi, bir Konu Uzmanı (SME) ve belki bir dilbilimci gerektirir. Ancak, Yapay Zeka uzmanı olmak ön koşul değildir.

Büyük Dil Modelleri (LLM), Yapay Zeka'yı bir hizmet olarak Yapay Zeka'ya doğru yönlendiriyor. Peki neden dönüştürücülerle Yapay Zeka geliştirme çalışalım? 

Yapay Zeka profesyoneli olmanın iki önemli nedeni vardır:
- Gerçek hayatta, Yapay Zeka projeleri genellikle beklenmedik sorunlarla karşılaşır. Örneğin, Google Çeviri belirli bir ihtiyacı karşılamayabilir, projeye ne kadar iyi niyet konulursa konulsun. Bu durumda, API'ler kullanışlı olur! 
- Google Trax for AI veya Google Cloud AI API'lerini kullanmak için bir Yapay Zeka geliştiricisi olmalısınız!

Asla bilemezsiniz! Büyük Dil Modelleri her şeyi her şeye bağlıyor; bazı Yapay Zeka projeleri sorunsuz çalışabilir ve bazıları karmaşık sorunları çözmek için Yapay Zeka uzmanlığı gerektirebilir.

Google Cloud AI, API'lerinin kullanımı için ücret alır. Eğitim amaçlı olarak, ücretsiz bir Google Çeviri AJAX API wrapper'ı uygulayacağız.

Python kodları bulunmamaktadır, bu nedenle satır satır açıklama gerekmemektedir. Yukarıdaki metin, verilen İngilizce paragrafın birebir Türkçe çevirisidir.

---

