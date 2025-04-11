# Prompt Tasarımından Prompt Mühendisliğine

İstem tasarımından, hiçbir mühendislik içermeyen bir istek tasarlamaktan, gömülü tabanlı bir RAG soru-cevap sistemine sahip prompt mühendisliğine geçtik. Sisteme 2022 Olimpiyatları hakkında orijinal soruyu sorabiliriz: 
```python
ask('2022 Kış Olimpiyatları'nda curlingde altın madalyayı hangi atletler kazandı?')
```
GPT modeli cevap verebilir ve cevap doğrudur: 
Erkekler curling turnuvasine, altın madalya İsveç takımı tarafından kazanıldı, takım Niklas Edin, Oskar Eriksson, Rasmus Wranå, Christoffer Sundgren ve Daniel Magnusson'dan oluşuyordu. Kadınlar curling turnuvasinda, altın madalya Büyük Britanya takımı tarafından kazanıldı, takım Eve Muirhead, Vicky Wright, Jennifer Dodds, Hailey Duff ve Mili Smith'den oluşuyordu.

Sonuç mükemmel değil, ancak iyi bir ilerleme. Örneğin, veri kümesi bu konudaki bir projede daha ayrıntılı bir şekilde ön işleme tabi tutulabilir. Bu durumda, model etkinliklerden birinin (karma çiftler) altın madalya kazananlarını listelemekte başarısız oldu: 
|Karma Çiftler<br/>{{DetailsLink|2022 Kış Olimpiyatları'nda Curling – Karma çiftler turnuvası}}
|{{flagIOC|ITA|2022 Kış}}<br>[[Stefania Constantini]]<br>[[Amos Mosaner]]
|{{flagIOC|NOR|2022 Kış}}<br>[[Kristin Skaslien]]<br>[[Magnus Nedregotten]]
|{{flagIOC|SWE|2022 Kış}}<br>[[Almida de Val]]<br>[[Oskar Eriksson]]
|} 
Neyin yanlış gittiğini görmek için daha fazla bilgiye ihtiyacımız var.

# Python Kodlarının Açıklaması

Verilen metinde python kodu olarak sadece `ask()` fonksiyonu geçmektedir. Bu fonksiyonun ne yaptığına dair bilgi verilmemekle birlikte, bir soru-cevap sistemi içinde kullanıldığı anlaşılmaktadır.

```python
ask('2022 Kış Olimpiyatları'nda curlingde altın madalyayı hangi atletler kazandı?')
```
Bu satır, `ask()` fonksiyonunu çağırarak bir soru sorar. `ask()` fonksiyonu muhtemelen bir GPT modeli kullanarak soruyu işler ve bir cevap döndürür. 

- `'2022 Kış Olimpiyatları'nda curlingde altın madalyayı hangi atletler kazandı?'`: Bu, `ask()` fonksiyonuna geçirilen sorudur.

Bu fonksiyonun nasıl çalıştığını anlamak için daha fazla kod ve içerik gerekli. Ancak basitçe, bu fonksiyon bir soru alır, muhtemelen bir GPT modeli veya benzeri bir doğal dil işleme modeli kullanarak cevabı üretir ve döndürür.

---

