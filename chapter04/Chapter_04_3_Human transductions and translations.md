# İnsan Çevirisi ve Makine Çevirisi

Örnek olarak, Avrupa Parlamentosu'ndaki bir insan tercüman bir cümleyi kelime kelime çevirmez. Kelime kelime çeviriler genellikle anlamsızdır çünkü doğru dilbilgisel yapıdan yoksundurlar ve her kelimenin bağlamı göz ardı edildiğinden doğru çeviriyi üretemezler. İnsan transdüksiyonu, A dilindeki bir cümleyi alır ve cümlenin anlamının bilişsel bir temsilini oluşturur. Avrupa Parlamentosu'ndaki bir tercüman ( sözlü çeviriler) veya bir çevirmen ( yazılı çeviriler) yalnızca bu transdüksiyonu B dilindeki cümlenin bir yorumuna dönüştürür. Tercüman veya çevirmen tarafından B dilinde yapılan çeviriyi referans cümlesi olarak adlandıracağız. Şekil 4.1'de açıklanan Makine çevirisi sürecinde birkaç referans fark edeceksiniz. Bir insan çevirmen A cümlesini B cümlesine birkaç kez çevirmez, gerçek hayatta sadece bir kez çevirir. Ancak, gerçek hayatta birden fazla çevirmen A cümlesini çevirebilir. Örneğin, Montaigne'nin Les Essais'inin birkaç Fransızca-İngilizce çevirisini bulabilirsiniz. Orijinal Fransızca versiyonundan bir cümle, A, alırsanız, referans 1'den n'ye kadar not edilen B cümlesinin birkaç versiyonunu bulacaksınız. Avrupa Parlamentosu'na bir gün giderseniz, tercümanların örneğin sadece iki saatlik sınırlı bir süre boyunca çeviri yaptığını fark edebilirsiniz. Sonra, başka bir tercüman devreye girer. İki tercümanın da tarzı aynı değildir, tıpkı yazarların farklı stilleri olması gibi. Örneğin, kaynak dilindeki A cümlesi aynı kişi tarafından bir gün içinde birkaç kez tekrarlanabilir, ancak birkaç referans B cümlesi versiyonuna çevrilir: referans = { referans 1, referans 2, ... referans n }. Makinelerin insan çevirmenler gibi düşünmenin bir yolunu bulması gerekir.

Python kodları bulunmamaktadır, ancak metinde geçen bazı kavramları Python kodları ile örneklendirebiliriz.

Örneğin, bir cümlenin farklı çevirilerini bir liste olarak temsil edebiliriz:
```python
referanslar = ["referans 1", "referans 2", ..., "referans n"]
```
veya 
```python
referanslar = ["çeviri 1", "çeviri 2", "çeviri 3"]
cumle_A = "Kaynak dilindeki cümle"
cumle_B = referanslar
print(cumle_A, "cümlesinin farklı çevirileri:", cumle_B)
```
Bu kod, bir cümlenin farklı çevirilerini bir liste olarak temsil eder.

Başka bir örnek olarak, bir tercümanın stilini temsil etmek için bir sınıf tanımlayabiliriz:
```python
class Tercuman:
    def __init__(self, isim):
        self.isim = isim
        self.stil = []

    def cevir(self, cumle):
        # Tercümanın stilini kullanarak cümleyi çevirir
        # Bu örnekte stil sadece bir liste olarak temsil edilmiştir
        self.stil.append(cumle)
        return self.stil[-1]

tercuman1 = Tercuman("Tercüman 1")
tercuman2 = Tercuman("Tercüman 2")

cumle_A = "Kaynak dilindeki cümle"
print(tercuman1.cevir(cumle_A))
print(tercuman2.cevir(cumle_A))
```
Bu kod, iki farklı tercümanın aynı cümleyi farklı stillerle çevirmesini temsil eder.

---

