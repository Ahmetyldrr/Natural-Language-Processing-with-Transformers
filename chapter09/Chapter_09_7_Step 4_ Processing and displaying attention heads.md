# İki Sütun Üzerindeki Renklerin Anlamı

İki token sütununun üzerindeki her renk, katman numarasının bir dikkat kafasını temsil eder. Bir katman numarası seçin ve bir dikkat kafasına (renge) tıklayın. Cümlelerdeki kelimeler dikkat içinde tokenlere ayrılır. Ancak bu bölümde, kelime tokenleri gevşek bir şekilde kelimelere atıfta bulunur, böylece transformatör kafalarının nasıl çalıştığını anlamamıza yardımcı olur.

# Katman ve Dikkat Kafalarının Seçilmesi

Şekil 9.2'de "animals" kelimesine odaklandım:
## Şekil 9.2: Bir Katman, Bir Dikkat Kafası ve Bir Token Seçme
BertViz, modelin "animals" ile birkaç kelime arasında bir bağlantı kurduğunu gösteriyor. Bu normaldir çünkü biz sadece katman 0'da bulunuyoruz.

## Katman 1'de İzole Edilen Kelimeler
Katman 1, "animals" ile ilgili kelimeleri izole etmeye başlar, Şekil 9.3'te gösterildiği gibi:
### Şekil 9.3: Katman 1'in Dikkat Kafası 11'inin Aktivitesini Görselleştirme
Dikkat kafası 11, "animals", "people" ve "adopt" arasında bir bağlantı kurar. 
Eğer "cats"e tıklayacak olursak, Şekil 9.4'te gösterildiği gibi bazı ilginç bağlantılar gösterilir:
#### Şekil 9.4: "cats" ile Diğer Tokenler Arasındaki Bağlantıları Görselleştirme
Şimdi "cats" kelimesi "animals" ile ilişkilendirilmiştir. Bu bağlantı, modelin "cats"in hayvan olduğunu öğrendiğini gösterir.

# Transformatörün Çalışmasını Anlamak
Cümleleri değiştirebilir ve ardından transformatörün bağlantıları nasıl kurduğunu görselleştirmek için katmanlara ve dikkat kafalarına tıklayabilirsiniz. Elbette, sınırlar bulacaksınız. Hem iyi hem de kötü bağlantılar, transformatörlerin nasıl çalıştığını ve neden başarısız olduklarını size gösterecektir. Her iki durum da transformatörlerin davranışını ve neden daha fazla katmana, parametreye ve veriye ihtiyaç duyduğunu açıklamak için değerlidir.

# Model Görünümünün Görselleştirilmesi
BertViz'in model görünümünü nasıl görüntülediğini görelim.

Python kodu bulunmamaktadır, sadece metin çevirisi yapılmıştır.

---

