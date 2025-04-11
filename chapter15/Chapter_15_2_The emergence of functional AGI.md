# Dönüştürücü Tabanlı Yapay Zekanın Yaygınlaşması ve Geleceği

Her alanda entelektüel görevler için dönüştürücü tabanlı yapay zekanın artan yaygınlığı, kaçınılmaz olarak Temel Modellerin büyük bir evrimine yol açacaktır. Massive Multitask Language Understanding (MMLU) modelleri yakında LLMs'i geride bırakacaktır. Fonksiyonel Yapay Genel Zeka (AGI) muhtemelen gelecekte zorunluluktan ortaya çıkacaktır. Yapay zeka hiçbir anlamda bilinçli, duyumsal veya insan değildir. Ancak, birkaç NLP kıyaslaması tarafından gösterildiği gibi, yapay zeka birçok alanda insanları geride bırakmak için bilinçli olmak zorunda değildir. Bu bölümde fonksiyonel AGI'nin ortaya çıkışını göstermek için, LLM değerlendirmeleri ve kontrollerinin geleceği hakkında spekülasyon yapacağız ve bunun nasıl yapay zeka kopyalarına yol açabileceğini göstereceğiz.

## Matematiksel Analiz

Hesapları yapalım: BIG-bench bir LLM değerlendirme platformudur: https://github.com/google/BIG-bench/blob/main/bigbench/benchmark_tasks/README.md. Platform 200'den fazla NLP görevi içermektedir. Stanford Institute for Human-Centered Artificial Intelligence (HAI) içindeki Center for Research on Foundation Models (CRFM), Bommasani ve ark. (2023) tarafından bahsedilen 100'den fazla ChatGPT düzeyinde Temel Modeli ve kaynakları takip etmeye çalışarak Ekosistem Grafikleri (envanter tabloları ve grafikleri) oluşturdu. Grafiğe bir göz atmak, bunun ne kadar zorlu bir görev olduğunu gösterir: https://crfm.stanford.edu/ecosystem-graphs/index.html?mode=graph. Örneğin, Hugging Face Hub, 120.000 model, 20.000 veri kümesi ve 50.000 demo barındırmaktadır: https://huggingface.co/docs/hub/index#hugging-face-hub-documentation. Hugging Face ayrıca LLMs'i takip etmek için bir LLM lider tablosu barındırmakta ve bunları değerlendirmek için kullanılan birkaç kıyaslamayı özetlemektedir. Her kıyaslama, Meta'nın LlaMA'sı ve LLaMA'nın 500'den fazla (Ağustos 2023) varyasyonu gibi aynı model için farklı sonuçlar üretmektedir: https://huggingface.co/spaces/HuggingFaceH4/open_llm_leaderboard.

Bu rakamları eklediğimizde, belirli bir proje için bir model seçmenin neredeyse imkansız bir zorluk olduğunu görürüz. Önceden tanımlanmış kıyaslama görevlerinde iyi performans gösteren bir model, belirli bir alanda son kullanıcıları tatmin etmeyebilir. Üretken yapay zeka yüzlerce uygulamada kullanılmaktadır. Microsoft 365, Google Workspace, OpenAI ChatGPT Plus ve diğer üst düzey platformlar gibi iyi bilinenler, her ay milyonlarca son kullanıcı çekmektedir. Ayrıca, yüzlerce uygulama birden fazla kaynaktan Üretken yapay zekayı piyasaya sürmektedir. Sosyal medya günde milyarlarca mesaj üretmektedir. Bunların kaç tanesi zaten Üretken yapay zeka tarafından yazılmıştır? 100.000'den fazla model x 100'den fazla değerlendirme görevi nasıl kontrol edilebilir? Bir şirket içinde yapay zeka tarafından üretilen içerik nasıl kontrol edilebilir? Cevap basit: Bu kadar büyük bir yapay zeka dalgasını kontrol edemeyiz!

## Gelecekteki Eğilimler

Gelecekte ortaya çıkması ve büyümesi muhtemel olan kaçınılmaz bir eğilim vardır: Yapay zekanın kendini değerlendirme ve geliştirme otomatik işlevi. Bu bölümde üç not defteri aracılığıyla geleceğe göz atacağız: Auto-Big-bench.ipynb, OpenAI GPT-4'ün yalnızca BIG-bench örneklerini çözmekle kalmayıp aynı zamanda onları icat edebildiğini gösterecektir! WandB_Prompts_Quickstart.ipynb, yapay zeka izleme işlevinin derinliğini gösterecektir. GPT-4 tarafından tamamen tasarlanan, yazılan ve açıklanan Encoder_decoder_transformer.ipynb, yapay zeka kopyalarının potansiyelini gösterecektir. Auto-BIG-bench ile başlayacağız. Ancak öncesinde, son teknoloji platformların kurulum sorunlarını göz ardı etmeyelim. OpenAI'ın kurulumuna göz atacağız.

Python kodları bulunmamaktadır, ancak metinde bazı Python notebooklarından (.ipynb dosyaları) bahsedilmektedir. Bu notebooklar muhtemelen aşağıdaki gibi açıklanabilir:

*   Auto-Big-bench.ipynb: Bu not defteri, OpenAI GPT-4'ün BIG-bench örneklerini çözme ve icat etme yeteneğini göstermek için kullanılacaktır.
*   WandB_Prompts_Quickstart.ipynb: Bu not defteri, yapay zeka izleme işlevinin derinliğini göstermek için kullanılacaktır.
*   Encoder_decoder_transformer.ipynb: Bu not defteri, GPT-4 tarafından tamamen tasarlanmış, yazılmış ve açıklanmıştır. Yapay zeka kopyalarının potansiyelini göstermek için kullanılacaktır.

Bu notebooklar Python programlama dilinde yazılmıştır ve Jupyter Notebook formatında (.ipynb) kaydedilmiştir. Jupyter Notebook, etkileşimli hesaplamayı destekleyen bir web tabanlı uygulamadır. Kullanıcıların kod, metin, matematik denklemleri, grafikler ve diğer zengin içerikleri içeren belgeler oluşturmasına ve paylaşmasına olanak tanır.

---

