# Orijinal Transformer Modelinin Mimarisini Keşfetmek
Daha önce de belirtildiği gibi, Aralık 2017'de Vaswani ve diğerleri (2017) seminal makalelerini, "Attention Is All You Need" (İhtiyacınız olan tek şey dikkat) başlığı altında yayınladılar. Çalışmalarını Google Research ve Google Brain'de gerçekleştirdiler. Bu bölüm ve kitap boyunca, "Attention Is All You Need" makalesinde açıklanan modele "orijinal Transformer modeli" olarak atıfta bulunacağım. Transformer mimarisini keşfetmek aşağıdaki nedenlerden dolayı önemlidir:

Herhangi bir makine öğrenimi veya derin öğrenme modelinin kaynak kodu klasik matematiğin bir ürünüdür. Sadece sistem çalıştırıldığında yapay zeka haline gelir. Yapay zeka, klasik matematikle inşa edilmiş bir modelin işlevidir. Transformer de bir istisna değildir. Algoritmanın içine bakarsanız, klasik matematik keşfedeceksiniz. Yapay zekanın büyüsü matematikte değil, sistemin aslında çalışırken ve görevleri yerine getirirken sergilediği davranıştadır.

Bazen, yapay zeka (veya başka bir yazılım) içinde uygulanan işlevleri optimize etmenin yollarını bulmak için ellerimizi kirletmeliyiz. Bu bölümde, inşa ettikleri Transformer modelinin yapısını inceleyeceğiz. Sonraki bölümlerde, modelin her bir bileşeninin içinde ne olduğunu keşfedeceğiz.

# Orijinal Transformer Modelinin Yapısı
Orijinal Transformer modeli altı katmandan oluşan bir yapıdır. Her katman alt katmanlar içerir. l katmanının çıktısı, nihai tahmin elde edilene kadar l + 1 katmanının girdisidir. Sol tarafta altı katmanlı bir kodlayıcı yığını ve sağ tarafta altı katmanlı bir kod çözücü yığını vardır. Aşağıdaki şekil, her bir kodlayıcı (sol) ve kod çözücü katmanının (sağ) yapısını gösterir:

## Şekil 2.1: Transformer Mimarisi
Soldaki girdiler, Transformer'ın kodlayıcı tarafına bir dikkat alt katmanı ve bir ileri beslemeli alt katman aracılığıyla girer. Sağdaki hedef çıktılar, Transformer'ın kod çözücü tarafına iki dikkat alt katmanı ve bir ileri beslemeli ağ alt katmanı aracılığıyla girer.

Hemen RNN, LSTM veya CNN olmadığını fark ettik. Bunun nedeni, bu mimaride tekrarın terk edilmiş olmasıdır. Dikkat, iki kelime arasındaki mesafe arttıkça parametre sayısının artmasını gerektiren tekrar işlevlerinin yerini almıştır.

Dikkat mekanizması, "kelime-kelime" işlemidir. Aslında bir jeton-jeton işlemidir, ancak açıklamayı basit tutmak için kelime düzeyinde tutacağız. Dikkat mekanizması, bir dizideki her kelimenin diğer tüm kelimelerle, analiz edilen kelimenin kendisi de dahil olmak üzere, nasıl ilişkili olduğunu belirler.

Örneğin, aşağıdaki diziyi inceleyelim:
"The cat sat on the mat."
Dikkat, kelime vektörleri arasında nokta ürünleri çalıştıracak ve belirli bir kelime ile diğer tüm kelimeler (kendisi de dahil) arasındaki en güçlü ilişkileri belirleyecektir ("kedi" ve "kedi" gibi):

## Şekil 2.2: Tüm kelimelere dikkat etmek
Dikkat mekanizması, kelimeler arasında daha derin bir ilişki sağlayacak ve daha iyi sonuçlar üretecektir. Her dikkat alt katmanı için, Orijinal Transformer modeli hesaplamaları hızlandırmak için paralel olarak sekiz dikkat mekanizması çalıştırır. Bu mimariyi sonraki bölümde, Kodlayıcı Yığını'nda keşfedeceğiz.

Bu süreç "çoklu başlık dikkati" olarak adlandırılır ve şunları sağlar:
- Dizilerin daha derinlemesine analizi
- Tekrarın önlenmesi, hesaplama işlemlerinin azaltılması
- Paralelizasyonun uygulanması, eğitim süresinin azaltılması
- Her dikkat mekanizması, aynı girdi dizisinin farklı perspektiflerini öğrenir

Dikkat, tekrarın yerini aldı. Ancak, Transformer'ın diğer birkaç yaratıcı yönü de dikkat mekanizması kadar kritiktir, mimarinin içine baktığımızda göreceksiniz. Transformer yapısını dışarıdan inceledik. Şimdi Transformer'ın her bir bileşenine girelim. Kodlayıcı ile başlayacağız.

Python kodları bulunmamaktadır, ancak Transformer modelinin yapısı ve dikkat mekanizması hakkında detaylı bir açıklama yapılmıştır.

---

