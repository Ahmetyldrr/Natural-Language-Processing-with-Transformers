# HuggingGPT Doğrulama İşlemi

HuggingGPT için doğrulama işlemi Hugging Face'in platformunda çalışacaktır: https://huggingface.co/spaces/microsoft/HuggingGPT . Sunucu kapalıysa veya bazen olduğu gibi HuggingGPT ile ilgili bir sorun varsa, depoyu klonlamayı, Docker ile çalıştırmayı veya Hugging Face desteğine başvurmayı deneyebilirsiniz. Hugging Face forumları da yardım için vardır. Hugging Face, tüm keskin kenarlı AI platformları gibi, tam hızda gelişiyor. Yapıcı kalmalıyız.

Shen ve diğerleri. (2023) bir LLM için AI modellerini bağlama yöntemi tasarladı. Makalelerinin başlığı ve Şekil 1, süreci özetliyor: HuggingGPT: Yapay Zeka Görevlerini ChatGPT ve Hugging Face'deki Arkadaşları ile Çözme “Şekil 1: Dil, LLMs (örneğin, ChatGPT) için çok sayıda AI modelini (örneğin, Hugging Face'dekiler) karmaşık AI görevlerini çözmek için bağlamak için bir arayüz olarak hizmet eder.” Bu bölümde, HuggingGPT'den, uyguladığımız notebook'un HuggingGPT bölümünde gösterildiği gibi, yardımlı sürüş bağlamında bir görüntüdeki bir arabayı tespit etmesini isteyeceğiz, Computer_Vision_Analysis.ipynb ve Şekil 19.4'te gösterildiği gibi:

# Şekil 19.4: HuggingGPT'nin Dört Adımlı Yapay Zeka Sistemi

Notebook şekli, doğrulama resimlerimiz için çalıştıracağımız HuggingGPT işlemini içerir: HuggingGPT, girdiğimiz istemi ve gönderdiğimiz görüntüyü işler. Şekil 19.4'te, analiz edilmesi kolay görüntü gösterilmektedir. HuggingGPT girişi işledikten sonra, bir model seçimi yapar. Ardından HuggingGPT, alt görevleri yürütür: görsel yanıtlama, algılama ve görüntüden metne. Son olarak, HuggingGPT, arayüzün sol tarafında görüntülenen yanıt oluşturmayı gerçekleştirir. Şekilde, çıktı, sistemin JSON çıktısının bir özetidir. Bu işlemi doğrulama veri kümesinin üç görüntüsü için çalıştıracağız.

İlk olarak, bu çapraz platform uygulamasında OpenAI API anahtarımızı ve HuggingFace tokenimizi girmeliyiz, Şekil 19.5'te gösterildiği gibi:

# Şekil 19.5: HuggingGPT'yi Çalıştırma

HuggingGPT'yi doğrudan OpenAI API anahtarımız ve Hugging Face tokenimiz ile çalıştırabiliriz. Ayrıca Space'i kopyalayabilir ve kişisel bir ortamda çalıştırabiliriz. Sadece sınırlı sayıda model şu anda mevcuttur, böyle bir sistemi dağıtmak için gereken işi göz önünde bulundurarak. Şimdi HuggingGPT'yi kolay görüntü ile çalıştıracağız.

Python kodları bulunmamaktadır, sadece metin çevirisi yapılmıştır.

---

