# BERT Modelinin Özellikleri ve Eğitimi

BERT modeli yalnızca kodlayıcı katmanlarına sahiptir ve kod çözücü yığını yoktur. Mimarisinde, her bir tokenin çevresindeki tüm tokenleri (maskeli veya değil) anlamayı öğrenmesini sağlayan çoklu-başlı öz-dikkat mekanizması bulunur. Bu çift yönlü yöntem, BERT'in her bir tokenin her iki tarafındaki bağlamı anlamasını sağlar. Maskeli çoklu-başlı dikkat katmanı, bazı tokenleri rastgele maskeler ve bu sistemi bağlamları öğrenmeye zorlar.

Örneğin, aşağıdaki cümleyi ele alalım: "The cat sat on it because it was a nice rug." Eğer "it" kelimesine ulaşmışsak, kodlayıcının girdisi şu şekilde olabilir: "The cat sat on it<masked sequence>" Rastgele maske dizinin herhangi bir yerinde olabilir, sonuna gelmek zorunda değildir. "it" kelimesinin neye atıfta bulunduğunu anlamak için, tüm cümleyi görmemiz ve "rug" kelimesine ulaşmamız gerekir ve "it" kelimesinin halının ("rug") yerine geçtiğini anlamamız gerekir.

Yazarlar, çift yönlü dikkat modelini geliştirdiler ve bir dikkat başının soldan sağa ve sağdan sola tüm kelimelere dikkat etmesini sağladılar. Başka bir deyişle, bir kodlayıcının öz-dikkat maskesi, kod çözücünün maskeli çoklu-başlı dikkat alt katmanı tarafından engellenmeden işi yapabilir.

Model, iki görevle eğitildi. İlk yöntem Maskeli Dil Modellemesi (MLM)'dir. İkinci yöntem ise Sonraki-Cümle Tahmini (NSP)'dir. MLM ile başlayalım.

## Maskeli Dil Modellemesi

Maskeli dil modellemesi, bir modelin görünür kelimelerin bir dizisiyle eğitilmesini ve ardından maskeli bir diziyi tahmin etmesini gerektirmez. BERT, bir cümleyi rastgele bir maskeyle çift yönlü analiz eder. BERT'in girdilere WordPiece, bir alt kelime segmentasyonu tokenleştirme yöntemi uyguladığını belirtmek önemlidir. Ayrıca, sinüs-kosinüs yaklaşımı yerine öğrenilmiş pozisyonel kodlama kullanır.

Potansiyel bir girdi dizisi şu şekilde olabilir: "The cat sat on it because it was a nice rug." Kod çözücü, model "it" kelimesine ulaştıktan sonra dikkat dizisini maskeleyebilir: "The cat sat on it <masked sequence>." Ancak BERT kodlayıcı, bir tahmini yapmak için rastgele bir tokeni maskeler ve bu da onu daha güçlü kılar: "The cat sat on it [MASK] it was a nice rug." Çoklu-dikkat alt katmanı, artık tüm diziyi görebilir, öz-dikkat sürecini çalıştırabilir ve maskeli tokeni tahmin edebilir.

Girdi tokenleri, modeli daha uzun süre eğitmeye ve daha iyi sonuçlar üretmeye zorlamak için üç yöntemle maskelendi:

*   Veri kümesinin %10'unda tek bir tokeni maskelemeyerek modeli şaşırtın; örneğin: "The cat sat on it [because] it was a nice rug."
*   Veri kümesinin %10'unda tokeni rastgele bir tokenle değiştirerek modeli şaşırtın; örneğin: "The cat sat on it [often] it was a nice rug."
*   Veri kümesinin %80'inde bir tokeni [MASK] tokeni ile değiştirin; örneğin: "The cat sat on it [MASK] it was a nice rug."

Yazarların cesur yaklaşımı, aşırı uyumu önler ve modelin verimli bir şekilde eğitilmesini sağlar.

BERT, sonraki-cümle tahmini yapmak üzere de eğitildi.

## Sonraki-Cümle Tahmini

BERT'i eğitmek için icat edilen ikinci yöntem NSP'dir. Girdi, iki cümle içerir. Vakaların %50'sinde ikinci cümle, bir belgenin gerçek ikinci cümlesiydi. Vakaların %50'sinde ikinci cümle rastgele seçildi ve birinci cümle ile ilgisi yoktu.

İki yeni token eklendi:

*   \[CLS], ikinci dizinin ilk diziyi takip edip etmediğini tahmin etmek için ilk dizinin başına eklenen bir ikili sınıflandırma tokenidir. Pozitif bir örnek, genellikle bir veri kümesinden alınan ardışık iki cümledir. Negatif bir örnek, farklı belgelerden diziler kullanılarak oluşturulur.
*   \[SEP], eldeki göreve bağlı olarak bir cümle, cümle bölümü veya soru gibi bir dizinin sonunu işaret eden bir ayırma tokenidir.

Örneğin, bir kitaptan alınan girdi cümleleri şu şekilde olabilir: "The cat slept on the rug. It likes sleeping all day." Bu iki cümle, bir tam girdi dizisi haline gelecektir: "\[CLS] the cat slept on the rug \[SEP] it likes sleep ##ing all day\[SEP]"

Bu yaklaşım, A dizisini B dizisinden ayırt etmek için ek kodlama bilgisi gerektirir. Çift kare (#\#) işareti, kullanılan WordPiece tokenleştirmesinden kaynaklanmaktadır. "sleep" kelimesi "ing" kelimesinden ayrı olarak tokenleştirildi. Bu, tokenleştiricinin daha küçük bir alt kelime sözlüğü, WordPiece üzerinde çalışmasını ve ardından bunları eğitim süreci boyunca birleştirmesini sağlar.

Tüm gömme işlemini bir araya getirirsek, aşağıdaki sonucu elde ederiz:

### Şekil 5.3: Girdi Gömme İşlemi

Girdi gömmeleri, token gömmelerinin, segment (cümle, ifade, kelime) gömmelerinin ve pozisyonel kodlama gömmelerinin toplanmasıyla elde edilir.

BERT modelinin girdi gömme ve pozisyonel kodlama alt katmanı aşağıdaki gibi özetlenebilir:

*   Bir kelime dizisi WordPiece tokenlerine ayrılır.
*   MLM eğitimi için ilk kelime tokenleri rastgele bir \[MASK] tokeni ile değiştirilir.
*   Sınıflandırma amacıyla bir dizinin başına bir \[CLS] sınıflandırma tokeni eklenir.
*   NSP eğitimi için iki cümleyi (segmentleri, ifadeleri) ayırmak üzere bir \[SEP] tokeni kullanılır.
*   Cümle A ile cümle B'yi ayırt etmek için cümle gömmesi token gömmesine eklenir.
*   Pozisyonel kodlama öğrenilir. Orijinal Transformer'ın sinüs-kosinüs pozisyonel kodlama yöntemi uygulanmaz.

BERT'in diğer bazı önemli özellikleri şunlardır:

*   Çoklu-başlı dikkat alt katmanlarında çift yönlü dikkat kullanır, tokenler arasındaki ilişkileri öğrenme ve anlama ufkunu genişletir.
*   Etiketlenmemiş metinlerle eğitilmemiş gömme ve ön eğitim modelleri senaryolarını tanıtır. Denetimsiz yöntemler, modelin çoklu-başlı dikkat öğrenme süreci sırasında daha fazla düşünmesini sağlar. Bu, BERT'in dillerin nasıl oluşturulduğunu öğrenmesini ve bu bilgiyi her seferinde ön eğitim yapmadan aşağı akış görevlerine uygulamayı sağlar.
*   Ön eğitim sürecinde tüm temelleri kapsayarak denetimli öğrenmeyi de kullanır.

BERT, transformerların eğitim ortamını geliştirmiştir. Şimdi, ön eğitimin motivasyonunu ve ince ayar sürecine nasıl yardımcı olduğunu görelim.

Bu metin, herhangi bir Python kodu içermemektedir.

---

