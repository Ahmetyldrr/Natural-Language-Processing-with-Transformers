# Dizi Desenleri ve Dil Modellemesi

Birçok büyük zihin, dizi desenleri ve dil modelleme üzerinde çalışmıştır. Sonuç olarak makineler, kelimelerin olası dizilerini tahmin etmeyi giderek öğrenmiştir. Bunu başaran tüm devlerin adını anmak bir kitap alır. Bu bölüm, AI'nın bugün geldiği yere ve transformatörlerin ortaya çıkışına yol açan kilit figürlerden bazılarını vurgulamaktadır.

## Geçmişten Günümüze Dizi Desenleri ve Dil Modellemesi

19. yüzyılın sonlarında ve 20. yüzyılın başlarında, Andrey Markov, rastgele değerler kavramını tanıttı ve stokastik süreçler teorisini oluşturdu (Daha fazla okuma bölümüne bakınız). Bunları AI'da Markov Karar Süreci (MDP), Markov Zincirleri ve Markov Süreçleri olarak biliyoruz. 20. yüzyılın başlarında, Markov, bir zincirin bir sonraki elemanını, o zincirin yalnızca son geçmiş elemanını kullanarak tahmin edebileceğimizi gösterdi. Birçok deney yaptı. Unutmayın ki onun elinde bilgisayar yoktu, ancak günümüzde AI'da hala kullanılan bir teoriyi kanıtladı.

1948'de Claude Shannon'ın "The Mathematical Theory of Communication" adlı kitabı yayınlandı. Claude Shannon, bir kaynak kodlayıcı, verici ve alıcı veya anlamsal kod çözücüye dayanan bir iletişim modeli için zemin hazırladı. Bilgi teorisini bugün bildiğimiz şekliyle yarattı. Claude Shannon, elbette, Markov'un teorilerini dikkate aldı.

1950'de Alan Turing, önemli makalesini yayınladı: "Computing Machinery and Intelligence". Alan Turing, bu makaleyi, II. Dünya Savaşı sırasında Alman mesajlarını şifreleyen başarılı Turing makinesine dayandırdı. Mesajlar, kelimelerin ve sayıların dizilerinden oluşuyordu.

1954'te Georgetown-IBM deneyi, bir kural sistemi kullanarak Rusça cümleleri İngilizceye çevirmek için bilgisayarları kullandı. Bir kural sistemi, veri yapılarını analiz edecek bir dizi kuralı çalıştıran bir programdır. Kural sistemleri hala var ve her yerde bulunuyor. Ancak bazı durumlarda, makine zekası, milyarlarca dil kombinasyonu için kural listelerini otomatik olarak öğrenerek değiştirebilir.

"AI" ifadesi ilk olarak 1956'da John McCarthy tarafından makinelerin öğrenebilme olasılıklarını araştırırken kullanıldı.

1982'de John Hopfield, Hopfield ağları veya "ilişkisel" sinir ağları olarak bilinen bir RNN tanıttı. John Hopfield, 1974'te "The Existence of Persistent States in the Brain" adlı makaleyi yazan WA Little'dan esinlendi, bu makale on yıllarca öğrenme süreçleri için teorik zemin hazırladı. RNN'ler evrim geçirdi ve bugün bildiğimiz gibi LSTM'ler ortaya çıktı.

## RNN ve CNN'lerin Evrimi

Bir RNN, bir dizinin kalıcı durumlarını verimli bir şekilde hatırlar, Şekil 1.4'te gösterildiği gibi:

Şekil 1.4: RNN süreci

Her durum S_n, S_(n-1)'in bilgisini yakalar. Ağın sonuna ulaşıldığında, F işlevi bir eylem gerçekleştirecektir: transdüksiyon, modelleme veya başka bir dizi tabanlı görev.

1980'lerde, Yann LeCun, çok amaçlı Evrişimli Sinir Ağı'nı (CNN) tasarladı. CNN'leri metin dizilerine uyguladı ve bunlar aynı zamanda dizi transdüksiyonu ve modellemesi için de uygulanabilir. Bunlar da WA Little'ın katman katman bilgi işleyen kalıcı durumlarına dayanmaktadır.

1990'larda, Yann LeCun, birkaç yıllık çalışmasını özetleyerek, bugün bildiğimiz birçok CNN modeline yol açan LeNet-5'i üretti. Ancak, bir CNN'nin aksi takdirde verimli mimarisi, uzun ve karmaşık dizilerdeki uzun vadeli bağımlılıklarla başa çıkarken sorunlarla karşılaşır.

## Transformatörlerin Ortaya Çıkışı

Dikkat kavramı ortaya çıktı: bir dizideki diğer tokenlere, sadece sonuncuya değil, göz atma. RNN ve CNN modellerine eklendi. Bundan sonra, AI modelleri daha uzun dizileri analiz etmek için artan bilgisayar gücüne ihtiyaç duyduğunda, AI geliştiricileri daha güçlü makineler kullandılar ve gradyanları optimize etmenin yollarını buldular.

Dizi-dizisi modelleri üzerine bazı araştırmalar yapıldı, ancak beklentileri karşılamadılar. Sanki daha fazla ilerleme kaydedilemiyordu ve otuz yıl bu şekilde geçti. Dikkat tanıtıldı, ancak modeller hala yinelemeye güveniyordu.

Ve sonra, 2017'nin sonlarından itibaren, endüstriyel state-of-the-art transformatör, dikkat başlığı alt katmanları ve daha fazlasıyla geldi. RNN'ler artık dizi modelleme için bir ön koşul gibi görünmüyordu.

Transformatör modeli, bir dizi kelime arasındaki ilişkileri, eş zamanlı olarak her bir kelime çifti arasındaki etkileşimleri hesaplayarak verimli bir şekilde yöneten bir dikkat katmanı tanıttı. Bu mekanizma, tüm kelimeleri aynı anda işler.

## Hesaplamalı Karmaşıklık

Big O gösterimini şimdi kullanıyoruz. Big O, bir algoritmanın yürütme süresi veya işlem sayısıın girdi boyutuna nasıl değiştiğini tanımlar. O, "mertebesi" anlamına gelir. "Mertebesi", girdi boyutu büyüdükçe gereken işlem sayısının nasıl büyüdüğünü temel olarak tanımlar.

RNN'ler, kelimeleri tek tek işledikleri için doğrusal zaman karmaşıklığına O(n) sahiptir, tıpkı bir kitabı sayfa sayfa okumak gibi. Bu, basit ama uzun bir kitap ise yavaş olur.

Transformatörler, tüm kelimeler arasındaki ilişkileri aynı anda analiz ettikleri için kuadratik zaman karmaşıklığına O(n^2) sahiptir, paralel işleme kullanarak, tüm "kitabı" veya veri dizisini daha kapsamlı ve hızlı bir şekilde anlamayı amaçlar.

Bu kavramları daha fazla keşfetmek isterseniz, bu bölüm için GitHub deposunda bulunan O-1_and_Accelerators.ipynb not defterini çalıştırabilirsiniz. Bu not defteri, transformatörlerdeki öz-dikkat katmanlarının hesaplama verimliliklerini RNN'lerdeki yinelemeli katmanlarla karşılaştıran simülasyonlar sağlar. Simülasyonlar, CPU'lar, GPU'lar ve TPU'lar dahil olmak üzere çeşitli donanım platformlarında gerçekleştirilir ve öz-dikkat mekanizmalarının daha etkili bir şekilde paralelleştirilebileceğini ve ölçeklenebileceğini gösterir.

Bu simülasyonlar, özellikle donanım hızlandırıcılarından yararlanırken, öz-dikkat mekanizmalarının pratik faydalarını gösterir. AI modellerinde hesaplama verimliliğini optimize etmeye yönelik ayrıntılı açıklamalar ve ek bilgiler Ek A, "AI'yı Devrimleştirmek: Transformatör Modellerinde Optimize Edilmiş Zaman Karmaşıklığının Gücü" bölümünde sağlanmaktadır.

Şimdi, bu token-token yaklaşımının AI'yı nasıl değiştirdiğini göreceğiz.

Python kodları bulunmamaktadır, eğer bir kod örneği isterseniz, örneğin RNN ve Transformer modellerinin karşılaştırılması için bir kod örneği verebilirim. 

Örneğin:
```python
import numpy as np

def rnn_time_complexity(n):
    return n

def transformer_time_complexity(n):
    return n**2

n = 100
print("RNN time complexity:", rnn_time_complexity(n))
print("Transformer time complexity:", transformer_time_complexity(n))
```
Bu kod, RNN ve Transformer modellerinin zaman karmaşıklığını karşılaştırmak için basit bir örnektir. 

1. `rnn_time_complexity` fonksiyonu, RNN modelinin zaman karmaşıklığını hesaplar, ki bu doğrusal zaman karmaşıklığı O(n) sahiptir.
2. `transformer_time_complexity` fonksiyonu, Transformer modelinin zaman karmaşıklığını hesaplar, ki bu kuadratik zaman karmaşıklığı O(n^2) sahiptir.
3. `n` değişkeni, girdi boyutunu temsil eder.
4. Fonksiyonları `n = 100` için çağırarak, her iki modelin zaman karmaşıklığını hesaplarız ve yazdırırız.

Bu kod, Transformer modelinin daha büyük girdi boyutları için daha yüksek zaman karmaşıklığına sahip olduğunu gösterir.

---

