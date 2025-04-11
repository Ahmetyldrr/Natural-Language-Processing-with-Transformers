# Üretken Modelin Tanımı
Üretken bir model, t = f(n) olarak özetlenebilir. Model, n'yi işler ve bir seferde bir token olmak üzere t üretir. Genel olarak "kelime" deriz, ancak aslında bir transformatör alt kelime veya token (bir kelimenin parçası) düzeyinde çalışır. Bu bir-token-bir-anda yaklaşımın yarattığı olasılıklar akıl almaz ve muazzamdır.

# Transformatör Modelinin Dinamik Yapısı
Bir-token yaklaşımının t = f(n) olarak özetlendiğini görebiliriz ve bu sonuçlar:
- Transformatör modelinin dinamik yapısı. Çıktısını, t_i = f(t_1, t_2, ..., t_{i-1}) tarafından temsil edilen artımlı girdilerine göre uyarlar. 
- Model, tamamen yeni girdiler üzerinde uyum sağlar ve çıktı üretir!

# Transformatör Modelinin Kapalı Doğası
Model, tokenler arasındaki ilişkileri ağırlıklar ve biaslarda kodlar ve depolar. Açık bir kılavuz yoktur. Sadece milyonlarca metin, resim ve ses verisine dayalı dinamik girdilerine göre tokenler üretmeye devam eder!

# Sistemin Esnekliği
Sistemin inanılmaz esnekliği, dinamik ve kapalı özelliklerinden miras alınır. GPT benzeri bir transformatör modeli, geniş bir bağlam yelpazesine sahip girdiler için anlamlı çıktılar çıkarabilir.

# Farklı Perspektiflerden Modelin Bir-Token Yaklaşımı
Şimdi, modelin bir-token yaklaşımının farklı perspektiflerden sonuçlarını göreceğiz; bu perspektifler bir modelden diğerine ve görevden göreve değişebilir:
- **Gözetimli ve Gözetimsiz**
Bazılarına göre, ChatGPT gibi bir GPT serisi modeli gözetimsiz eğitimden geçer. Bu ifade ancak belli bir dereceye kadar doğrudur. Token token, GPT benzeri bir model, kendi kendini denetleyerek öğrenme yoluyla doğruluk yolunu bulur, dizideki önceki tokenlere dayanarak her bir sonraki tokeni tahmin eder. Bunu, bir dizideki diğer tüm tokenlerin temsillerinin etkisiyle başarır. 
Ayrıca, bir GPT modelini bir girdi (prompt) ve çıktı (tamamlama) ile etiketlerle ince ayar yapabiliriz! Binlerce girdi (prompt) sağlayabiliriz ve çıktı olarak bir token (tamamlama) olabilir. Örneğin, binlerce soruyu girdi olarak oluşturabiliriz ve sadece "doğru" ve "yanlış" çıktı olarak sağlayabiliriz. Bu, örtük gözetimli öğrenmedir. Ayrıca, model doğru tahminleri açıkça ezberlemez. Sadece tokenlerin desenlerini öğrenir.

- **Ayırt Edici ve Üretken**
ChatGPT'nin ortaya çıkışından bu yana, "Üretken Yapay Zeka" terimi genellikle GPT benzeri modelleri tanımlamak için kullanılmıştır. İlk olarak, GPT modellerinin Üretken Yapay Zeka üreten ilk modeller olmadığını belirtmeliyiz; RNN'ler de üretkendir. Ayrıca, bilimi takip edersek, GPT benzeri modellerin Üretken Yapay Zeka görevleri gerçekleştirdiğini söylemek tamamen doğru değildir. 
Önceki Gözetimli ve Gözetimsiz madde noktasında, "üretken" bir modelin, girdi bir ifade veya soru olduğunda "doğru" veya "yanlış" gibi bir çıktı çıkararak gözetimli görevler gerçekleştirebildiğini belirtmiştik. Bu bir Üretken Yapay Zeka görevi değildir; bu bir ayırt edici Yapay Zeka görevidir. 
Başka bir durum, özetleme ile ortaya çıkabilir. Özetlemenin bir kısmı anahtar kelimeleri, konuları ve isimleri bulmak için ayırtedicidir. Diğer bir kısmı, sistem yeni tokenler üreterek bir metni özetlerken üretkendir. 
Son olarak, bir token üreterek ve girdiye ekleyerek otoregresif yapının tam gücü, modeli inanılmaz derecede esnek kılar. 
Bir LLM, Üretken Yapay Zeka ile bir hikaye uydurduğunda, daha önce yazdıklarına dayanarak çıktılarını token token olarak uyarlar. 
GPT benzeri bir model, yerine getirilmesi gereken göreve bağlı olarak ayırt edici, üretken veya her ikisi olabilir.

- **Görev Özel ve Özel Görev Modelleri**
Görev özel modeller, genellikle GPT benzeri LLM'ler gibi genel amaçlı modellere karşıttır. Görev özel modeller, belirli görevlerde çok iyi performans göstermek üzere eğitilir. 
Bu, bazı görevler için belli bir dereceye kadar doğrudur. Ancak, genel amaçlı sistemler olmak üzere eğitilen LLM'ler, çeşitli sınavların (hukuk, tıbbi) değerlendirmeleri aracılığıyla kanıtlandığı üzere, belirli görevlerde şaşırtıcı derecede iyi performans gösterebilir. 
Ayrıca, LLM transformatör modelleri, görüntü tanıma gerçekleştirebilecek şekilde geliştirilmiştir.

- **Etkileşim ve Otomasyon**
İnsanlar ve LLM'ler arasındaki ilişkinin analizinde kilit bir nokta otomasyondur. Görevlerimizi ne dereceye kadar otomatize etmeliyiz? 
Bazı görevler LLM'ler tarafından otomatize edilemez. ChatGPT ve diğer asistanlar, hayat memat, ahlaki, etik ve iş kararları vermemelidir. 
Bir sisteme bunu yapmasını söylemek, bir organizasyonu ve insan hayatını tehlikeye atacaktır. Otomasyon, LLM'leri uygulamadan önce iyice analiz edilmelidir.

# Sonuç
Bu kitabın aşağıdaki bölümlerinde, gözetimli, kendi kendini denetleyerek öğrenme, gözetimsiz, ayırt edici, üretken ve görev özel modellerle karşılaşacak ve gelişmiş Yapay Zeka ve otomatik sistemlerle etkileşimler göreceksiniz. 
Bazen tüm bunları genel amaçlı bir LLM'in mimarisinde bulacaksınız! Hazır olun ve esnek kalın! 
Yapay Zeka profesyonelleri olarak sorumluluğumuz, transformatörlerin ve işlevlerinin kapsamlı bir şekilde anlaşılmasını, sınırlamalarının değerlendirilmesini ve beceri setimizin geliştirilmesini içerir. 
Görelim bakalım. 

Python kodları bulunmamaktadır, bu nedenle satır satır açıklama verilmemiştir.

---

