#Bill of Rights
Verilen örnek, bir kişinin özel haklarını ifade ettiği için daha zordur:
```python
text = """ Hiçbir kişi, bir Büyük Jüri'nin sunumu veya iddianamesi olmadan, kara veya deniz kuvvetlerinde veya Milislerde, savaş veya kamu tehlikesi zamanında fiili hizmette ortaya çıkan haller dışında, ölüm cezasına veya başka türlü kötü şöhretli bir suçtan dolayı cevap vermek zorunda tutulamaz; aynı zamanda aynı suç için hayat veya uzuvdan iki kez tehlikeye atılamaz; herhangi bir ceza davasında kendi aleyhine tanık olmaya zorlanamaz, veya kanuni işlem yapılmadan hayat, özgürlük veya mülkiyetten yoksun bırakılamaz; özel mülkiyet, adil bir tazminat yapılmadan kamu kullanımı için alınamaz. """
```
#Metin Uzunluğu
```python
print("Karakter sayısı:", len(text))
```
Bu kod, `text` değişkeninde saklanan metnin karakter sayısını yazdırır.

#Özetleme
```python
summary = summarize(text, 50)
```
Bu kod, `text` metnini özetler ve `summary` değişkenine atar. `summarize` fonksiyonu, metni özetlemek için kullanılır ve ikinci argüman olarak özet uzunluğunu alır.

```python
wrapped_summary = textwrap.fill(summary, width=70)
```
Bu kod, özet metnini 70 karakter genişliğinde satırlara böler.

```python
print("\nÖzetlenmiş metin:\n", wrapped_summary)
```
Bu kod, özetlenmiş metni yazdırır.

Dönüştürücüler (transformers) stokastik algoritmalardır, bu nedenle çıktı her çalıştırdığınızda değişebilir. 
T5'in girdi metnini gerçekten özetlemediğini, sadece kısalttığını görebiliriz:
Karakter sayısı: 591
Ön işlenmiş ve hazırlanmış metin:
Özetle: Hiçbir kişi cevap vermek zorunda tutulamaz..
Özetlenmiş metin:
hiçbir kişi, bir Büyük Jüri'nin sunumu veya iddianamesi olmadan, ölüm cezasına veya başka türlü kötü şöhretli bir suçtan dolayı cevap vermek zorunda tutulamaz. aynı zamanda aynı suç için hayat veya uzuvdan iki kez tehlikeye atılamaz 

Bu örnek, bir metin gibi karmaşık bir metin sağlandığında herhangi bir dönüştürücü modelin veya diğer Doğal Dil İşleme (NLP) modelinin karşı karşıya olduğu sınırları gösterir. 
Kullanıcılara dönüştürücülerin inovatif olmalarına rağmen, karşılaştığımız tüm NLP zorluklarını çözdüğünü inanmalarını sağlamak için her zaman işe yarayan örnekler sunamayız. 
Hala sonucu işlememiz ve eksik cümlelerin tespiti, maksimum uzunluğun arttırılması ve diğer klasik veri işleme yöntemleri gibi çözümler bulmamız gerekiyor. 
Belki de özetlemek için daha uzun bir metin sağlamalı, diğer parametreleri kullanmalı, daha büyük bir model kullanmalı veya T5 modelinin yapısını değiştirmeliyiz. 
Ancak, bir NLP modeli ile karmaşık bir metni özetlemeye çalışsanız da, modelin özetleyemediği belgeler her zaman bulacaksınız. 
Bir model bir görevde başarısız olduğunda, alçakgönüllü olmalı ve kabul etmeliyiz. 
Dönüştürücü modellerini bugün yaptıklarından daha iyi performans gösterene kadar sabırlı olmalı, daha çok çalışmalı ve geliştirmeliyiz. 
Hala çok ilerleme kaydedilmesi gerekiyor. 
Raffel ve diğerleri (2018), T5'e yaklaşımını tanımlamak için uygun bir başlık seçti: Birleştirilmiş Metin-Metin Dönüştürücü ile Transfer Öğreniminin Sınırlarını Keşfetmek. 
Kendi yasal belgelerinizde bulduğunuz örneklerle deneyler yapmak için gerekli zamanı ayırın. 
Modern bir NLP öncüsü olarak transfer öğreniminin sınırlarını keşfedin! 
Bazen heyecan verici sonuçlar keşfedeceksiniz ve bazen de geliştirilmesi gereken alanlar bulacaksınız. 
Şimdi, bir şirket hukuku örneği deneyelim.

---

