# Vertex AI PaLM 2
Vertex AI PaLM 2, OpenAI GPT-4'ün SOA eşdeğeridir. Bu bölüm, çevrimiçi arayüzü ve ana parametreleri ele alacaktır. Parametrelerini açıklamak için PaLM 2'nin bilgisini kullanacağız. Vertex AI'ya erişmek için bir hesaba ihtiyacınız olacak. Kaydolduktan sonra, kaydolmak istemiyorsanız bu kendi kendine yeterli bölümü okuyabilirsiniz. Ardından, dil modeli ortamına gidin. Çevrimiçi PaLM 2 asistanını keşfederek başlayacağız:

## Vertex AI Arayüzü
Vertex AI arayüzü, OpenAI Playground'a benzer bir istem metin kutusuyla birlikte gelir. Şekil 14.11'de gösterildiği gibi değiştirebileceğimiz bir parametre listesi de vardır:

## Ana Örnekleme Parametreleri
Parametreler, 7. Bölüm, ChatGPT ile Üretken Yapay Zeka Devrimi'nde gördüğümüz Open AI GPT modelleriyle aynıdır. Şekil 14.11'de görünen dört ana örnekleme parametresi kritik bir teknik sırayla görünür:
### Sıcaklık (Temperature)
Bu hiperparametre, çıkarım yaparken modelin ham çıktı logitlerine softmax'tan önce uygulanır. 0.2 gibi küçük bir değer, softmax uygulandığında en olası çıktının seçilmesini teşvik eder. Daha yüksek olasılıklar softmax'tan sonra daha yüksek görünür. Bu durumda, model daha deterministik çıktılar üretecektir. Ancak, sıcaklık değeri 1'e yaklaşır veya aşarsa, model softmax'tan sonra daha az güvenilir olur, çıktının rastgeleliği artar ve tahminler daha değişken olur. Seçim, çeşitlilik ve tahminlerin kalitesi arasında bir dengeyi temsil eder.

### Token Limiti (Token Limit)
Bu hiperparametre, modelin üreteceği maksimum dizi uzunluğunu belirler. Üretim işlemi, bu limite ulaşıldığında veya model bir dizinin sonunu belirten bir token ürettiğinde durur. Token limiti, diğer hiperparametrelerden bağımsız olarak çalışır ve uygulanması modelin özel mimarisine bağlı olarak değişebilir.

### Softmax
Softmax, görüntülenmez ancak çoğu durumda uygulanır. Bu, bir olasılık normalleştirme işlevidir. Hem eğitim sırasında hem de çıkarım için modelin çıktı logitlerine uygulanır. Çıkarım sırasında, softmax, sıcaklık işleminden sonra uygulanır. Logitleri, 0 ile 1 arasında bir aralıkta bulunacak şekilde dönüştürür, olasılıklar olarak yorumlanabilir ve toplamları 1'e eşittir.

### Top-K
Top-K hiperparametresi, bir sonraki token için olasılık kümesini K değerine sınırlar. Top-K, softmax'tan sonra uygulanır. Örneğin, hiperparametre 40 olarak ayarlanırsa, softmax işlevinden sonra en üstteki 40 olasılık seçilir.

### Top-P veya Nucleus Örneklemesi (Top-P or Nucleus Sampling)
Top-P veya nucleus örneklemesi, olasılıkları azalan sırada sıralar. Ardından, Top-P hiperparametresine ulaşana kadar (örneğin, 0.8) olasılıkları yukarıdan aşağıya doğru toplar. Olasılıklar örneklendikten sonra, bir sonraki token olarak rastgele biri seçilir. Bu token daha sonra bir sonraki token tahmini için girdi token dizisine eklenir. Bu yöntem, Top-K'dan daha çeşitli ve yaratıcı yanıtlar üretme eğilimindedir. Top-K ve Top-P ayrı veya birlikte kullanılabilir. Birlikte kullanılmaları durumunda, Top-K önce olasılık sayısını azaltmak için uygulanır ve ardından Top-P elde edilen kümeye uygulanır.

Eğer sıcaklık, softmax, Top-K ve Top-P birlikte uygulanırsa, bir sonraki token'ı seçmek için örnekleme işlevini bileşik bir işlev olarak temsil edebiliriz:
`Sampler= Top-P(Top-K(softmax(sıcaklık(çıktı logitleri))))`

PaLM veya GPT modelleri ham logitler üretir. Ardından, bir Sampler işlevi devreye girer, bir sonraki token'ı üretir ve modelin devam eden token tahminleri için tokenleştirilmiş girdi dizisine ekler.

## Güvenlik Filtresi Eşiği (Safety Filter Threshold)
Güvenlik filtresi eşiği, potansiyel olarak zararlı içerikleri sınırlamada ilginçtir. Değeri, her projenin amacına bağlıdır. Daha fazla bilgi için Google'ın Üretken Yapay Zeka belgelerine başvurabilirsiniz: https://cloud.google.com/vertex-ai/docs/generative-ai/learn/models?_ga=2.96585695.-1947292201.1682929481

## Vertex AI PaLM İstekleri
Vertex AI PaLM'ye yapılan istekler bazen modele bağlı olarak farklı parametre konfigürasyonları gerektirecektir. Vertex AI, OpenAI gibi model adlandırma şemalarıyla düzenlenmiştir. Vertex AI'deki Temel Modeller için biçim, model boyutuna bir önek olarak kullanım durumudur. Model boyutu, sürümün adının anahtar kısmıdır:
- Bison: En iyi yetenek ve daha yüksek maliyet.
- Gecko: En küçük ve daha düşük maliyet.

Google AI, OpenAI gibi, kararlı veya daha yeni sürümlere ve yaşam döngülerine sahiptir. Bu da normaldir, tıpkı arabalar, akıllı telefonlar, bilgisayarlar ve her ürün ve hizmet için olduğu gibi. Buna alışmalı ve üretimde son derece dikkatli olmalıyız, 15. Bölüm, Devleri Korumak: Büyük Dil Modellerinde Riskleri Azaltma'da göreceğimiz gibi.

## Ana Önekler
Ana önekler `text`, `text-embedding`, `chat` ve `codechat`'dir. Örneğin:
- `text-bison` sınıflandırma, varlık çıkarma, Soru-Cevap, özetleme, duygu analizi ve diğer metin odaklı görevler için.
- `textembedding-gecko` metin girdilerini gömmek için, 11. Bölüm, İnce Ayarlama Alternatifi Olarak LLM Gömme'leri Kullanma'da gördüğümüz gibi.
- `code-bison` kod istekleri için.

Google'ın Üretken Yapay Zeka belgelerinde birkaç başka model bulacaksınız. Gemini gibi yeni modeller mevcuttur, GPT-4V'ye benzer bir multimodal model. Ve daha fazlası geliyor! Modellerin kararlılığını ve yaşam döngüsünü üretimde dağıtmadan önce aklınızda bulundurun.

## Vertex AI API'sini Uygulamadan Önce
Çevrimiçi asistan ile birkaç görev çalıştırmadan önce. Ana akım kullanıcıların giderek daha fazla yapay zeka destekli asistanları günlük çalışma hayatlarına entegre edeceklerini unutmamalıyız.

---

