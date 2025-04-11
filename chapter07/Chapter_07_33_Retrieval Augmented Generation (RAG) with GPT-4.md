# RAG ile Geliştirilmiş Üretken Yapay Zeka Uygulaması Oluşturma

Bu bölümde, RAG'ı uygulayan giriş niteliğinde bir program oluşturacağız. Belge erişimi yeni bir kavram değildir. Bilgi tabanları, on yıllar önce veritabanlarındaki sorguların ortaya çıkmasıyla birlikte var olmuştur. Üretken Yapay Zeka da yeni değil. RNN'ler yıllar önce yapay zeka destekli metin üreteçleriydi. Bu faktörleri dikkate alarak, RAG'ın bir yenilik değil, Üretken Yapay Zeka modellerinin kesinlik, eğitim verileri ve oluşturulan çıktıların kalitesi eksikliğini telafi eden bir iyileştirme olduğunu söyleyebiliriz. Ayrıca bazı durumlarda bir modelin ince ayarını yapmaktan kaçınabilir. Geliştirilmiş üretim gerçekleştirmenin farklı yolları da vardır, ilerleyen bölümlerde göreceğimiz gibi: Bölüm 11, İnce Ayar Yapmak Yerine LLM Gömme Kullanma, gömülü verileri uygulayacağımız yerdir. Bölüm 15, Devleri Korumak: Büyük Dil Modellerinde Riskleri Azaltma, burada riskleri azaltma çözümlerinden biri bilgi tabanları uygulamaktır. OpenAI, belge erişimini sonuçların iyileştirilmesi için yöntemlerden biri olarak belgelerinde belirtmektedir: https://platform.openai.com/docs/guides/prompt-engineering/six-strategies-for-getting-better-results. Bu bölümde, GPT'nin Üretken Yapay Zeka GPT-4 işlevselliğini RAG ile geliştireceğiz. Bu bölümün dizinindeki Open GPT_4_RAG.ipynb dosyasını açın. Not defteri üç bölüme ayrılmıştır: Kurulum, Belge Erişimi ve Erişim Geliştirilmiş Üretim.

İlgili python kodları bulunmamaktadır, ancak `Open GPT_4_RAG.ipynb` adlı Jupyter Notebook dosyası hakkında bilgi verilmektedir. Bu dosya aşağıdaki üç ana bölüme ayrılmıştır:

1. **Kurulum (Installation)**: Bu bölümde, gerekli kütüphanelerin ve bağımlılıkların kurulumu yapılmaktadır. 
2. **Belge Erişimi (Document retrieval)**: Bu bölümde, ilgili belgelerin nasıl erişileceği ve işleneceği anlatılmaktadır.
3. **Erişim Geliştirilmiş Üretim (Retrieval augmented generation)**: Bu bölümde, erişilen belgelerin üretim aşamasında nasıl kullanıldığı ve geliştirilmiş üretim teknikleri anlatılmaktadır.

Eğer `Open GPT_4_RAG.ipynb` dosyasını açarsanız, bu üç bölüm hakkında daha detaylı bilgi edinebilir ve ilgili python kodlarını inceleyebilirsiniz.

---

