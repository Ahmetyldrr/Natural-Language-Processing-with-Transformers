# Raffel ve Ekibi (2019): Transfer Öğrenmenin Sınırlarını Birleştirilmiş Bir Metin-Metin Dönüştürücü ile Keşfetmek

Raffel ve ark. (2019) öncü olarak bir yolculuğa çıktılar ve tek bir hedefi gerçekleştirmeye çalıştılar: **Birleştirilmiş Bir Metin-Metin Dönüştürücü ile Transfer Öğrenmenin Sınırlarını Keşfetmek**. Bu yaklaşım üzerinde çalışan Google ekibi, başlangıçtan itibaren Orijinal Dönüştürücü'nün temel mimarisini değiştirmeyeceklerini vurguladılar. O noktada, Raffel ve ark. (2019) teknikler yerine kavramlara odaklanmak istediler. Bu nedenle, genellikle n parametre ve katman içeren sözde bir gürz transformer modeli olarak gördüğümüz en yeni dönüştürücü modelini üretmeye ilgi göstermediler. Bu sefer, T5 ekibi, dönüştürücülerin bir dili ne kadar iyi anlayabileceğini keşfetmek istedi. İnsanlar bir dil öğrenir ve daha sonra bu bilgiyi geniş bir NLP görev yelpazesine transfer öğrenme yoluyla uygular. Bir T5 modelinin temel kavramı, bizim gibi şeyler yapabilen soyut bir model bulmaktır. Dönüştürücülerin, istatistiksel desen keşfi yoluyla insana benzer tepkileri yeniden üretmeyi öğrendiklerini hatırlayın. İletişim kurduğumuzda, her zaman bir dizi (A) ile başlarız, ardından başka bir dizi (B) gelir. B, sırasıyla, başka bir diziye yol açan başlangıç dizisi haline gelir, Şekil 13.1'de gösterildiği gibi:

## Şekil 13.1: İletişimin bir dizi-dizi gösterimi

Ayrıca, organize edilmiş seslerle müzik yoluyla iletişim kurarız. Organize edilmiş vücut hareketleriyle dans yoluyla iletişim kurarız. Koordineli şekil ve renklerle resim yaparak kendimizi ifade ederiz. Bir kelime veya "metin" dediğimiz bir kelime grubu ile dil yoluyla iletişim kurarız. Bir metni anlamaya çalıştığımızda, cümledeki tüm kelimelere her yönden dikkat ederiz. Her terimin önemini ölçmeye çalışırız. Bir cümleyi anlamadığımızda, bir kelimeye odaklanır ve cümledeki diğer anahtar kelimelere değerlerini ve onlara dikkat etmemiz gerektiğini sorgularız. Bu yaklaşım, dönüştürücülerin dikkat katmanlarının mekanizmasını tanımlar. Birkaç saniye ayırın ve bunun size yerleşmesini sağlayın. Aldatıcı bir şekilde basit görünüyor, değil mi? Yine de, RNN'lere, CNN'lere ve onlara eşlik eden düşünce sürecine ilişkin eski inançları yıkmak 35 yılı aşkın bir zaman aldı!

# Bölüm 1: Dönüştürücüler Nedir?, özellikle "Tekrarlayan'dan Dikkat'e kısa bir yolculuk" bölümünde gösterildiği gibi, Büyük Dil Modellerinin (LLM) inanılmaz evrimini gösterdi. T5'in öğrenmesini, ilerlemesini ve bazen daha iyi düşünmemize yardımcı olmasını izlemek oldukça büyüleyicidir! 

Bir dizideki tüm belirteçlere aynı anda dikkat eden dikkat katmanlarının teknik devrimi, T5 kavramsal devrimine yol açtı. T5 modeli, bir **Metin-Metin Transfer Dönüştürücü** olarak özetlenebilir. Böylece, her NLP görevi, çözülecek bir metin-metin problemi olarak ifade edilir. T5 modelleri, diğer birçok modelden farklı olarak, belirli bir görev için ince ayar yapılmasına ihtiyaç duymaz. Her NLP görevinin süreci bir metin-metin problemidir. Bu esnek metin-metin yaklaşımı, T5 modellerinde öneklerin kullanımını incelememize yol açar.

Python kodları bulunmamaktadır, ancak metinde geçen bazı kavramları açıklayan basit bir kod örneği vermek gerekirse:

```python
# Örnek bir diziden diğerine dikkat mekanizması
import numpy as np

# Dizi A ve Dizi B
A = np.array([1, 2, 3])
B = np.array([4, 5, 6])

# Dikkat ağırlıkları
attention_weights = np.array([[0.1, 0.2, 0.7], [0.3, 0.4, 0.3], [0.5, 0.4, 0.1]])

# Dikkat mekanizması
output = np.dot(attention_weights, B)

print("Dikkat mekanizması çıktısı:", output)
```

Bu kod, basit bir dikkat mekanizmasını gösterir. Dikkat ağırlıkları, her bir girdi öğesine ne kadar "dikkat" edileceğini belirler. Yukarıdaki kod örneği, basitçe `B` dizisinin ağırlıklı toplamını hesaplar. Gerçek uygulamalarda, bu ağırlıklar genellikle model tarafından öğrenilir.

---

