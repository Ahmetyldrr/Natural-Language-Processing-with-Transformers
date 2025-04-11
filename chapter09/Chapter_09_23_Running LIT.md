# LIT'in Çevrimiçi Kullanımı ve Duygu Analizi Sınıflandırıcısı

LIT'i çevrimiçi olarak çalıştırabilir veya bir Google Colaboratory not defterinde açabilirsiniz. Her iki seçeneğe de erişmek için aşağıdaki bağlantıya tıklayın: https://pair-code.github.io/lit/. Öğretici sayfası analiz edilecek birkaç NLP görevi içerir: https://pair-code.github.io/lit/tutorials/. Bu bölümde, LIT'i çevrimiçi olarak çalıştıracağız ve bir duygu analizi sınıflandırıcısı keşfedeceğiz: https://pair-code.github.io/lit/tutorials/sentiment/. "Explore this demo yourself" (Bu gösteriyi kendiniz keşfedin) üzerine tıkladığınızda sezgisel LIT arayüzüne gireceksiniz.

## Model Seçimi
Dönüştürücü model küçüktür: 
Şekil 9.17: Model seçme 
Modele tıklayarak modeli değiştirebilirsiniz. Bu tür modelleri ve benzerlerini doğrudan Hugging Face'in barındırdığı API sayfasında test edebilirsiniz: https://huggingface.co/sshleifer/tiny-distilbert-base-uncased-finetuned-sst-2-english. LIT'in çevrimiçi sürümündeki NLP modelleri sonraki güncelleştirmelere bağlı olarak değişebilir. Kavramlar aynı kalır, sadece modeller değişir.

## PCA Projektörünün Seçilmesi
PCA projektörünü seçerek başlayalım. Projektör, her örneğin duygu analizinin ikili 0 veya 1 sınıflandırma etiketini görüntüler: 
Şekil 9.18: Projektör ve etiket türünü seçme 
Daha sonra veri tablosuna gidip bir cümle ve sınıflandırma etiketi üzerine tıklıyoruz: 
Şekil 9.19: Cümle seçme 
Algoritma stokastiktir, bu nedenle çıktı bir çalışmadan diğerine değişebilir. Cümle, Veri Noktası Düzenleyicide de görünecektir: 
Şekil 9.20: Veri Noktası Düzenleyicisi 
Veri Noktası Düzenleyicisi, cümlenin bağlamını değiştirmenize olanak tanır. Örneğin, bir karşı olgusal sınıflandırma ile ilgili yanlış giden şeyin ne olduğunu bulmak isteyebilirsiniz. Cümlenin bağlamını, doğru sınıfta görünene kadar değiştirebilir ve modelin nasıl çalıştığını ve neden hata yaptığını anlayabilirsiniz. Cümle, sınıflandırma ile birlikte PCA projektöründe görünecektir: 
Şekil 9.21: Pozitif bir kümede PCA projektörü 
PCA projektöründeki veri noktalarına tıklayabilirsiniz ve cümleler, seçtiğiniz cümlenin altındaki veri noktası düzenleyicide görünecektir. Bu şekilde sonuçları karşılaştırabilirsiniz.

LIT, keşfedebileceğiniz ve kullanabileceğiniz geniş bir etkileşimli işlevsellik yelpazesi içerir. LIT'te elde edilen sonuçlar her zaman inandırıcı değildir. Ancak LIT, birçok durumda değerli bilgiler sağlar. Ayrıca, bu ortaya çıkan araçları ve teknikleri deneyimlemek esastır. Şimdi GPT-4'ün bir LLM'deki nöronların aktivitesini nasıl açıklayabileceğini keşfedeceğiz.

Bu metinde Python kodları bulunmamaktadır, sadece bir İngilizce metnin birebir Türkçe çevirisi yapılmıştır.

---

