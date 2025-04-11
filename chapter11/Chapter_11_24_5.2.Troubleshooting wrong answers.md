# Önceki Yanıttaki Bilgiler
Bu önceki yanıttaki bilgiler şunlar olabilir: Gönderdiğimiz mesajda bilgi eksikliği olması veya GPT modelinin mantık yürütme hatası yapması. `print_message` seçeneğini `True` olarak ayarlayarak bunu öğrenebiliriz: 

```python
# Kaynak metni görmek için print_message=True olarak ayarlayın
ask('Hangi atletler 2022 Kış Olimpiyatları\'nda curlingde altın madalya kazandı?', print_message=True)
```

Çıktı, modele gönderilen bilgiyi ve sorguyu gösterir, aşağıdaki alıntıda olduğu gibi, yanıtta eksik olan karışık çiftler dahil:

```
…
|Women<br/>{{DetailsLink|Curling at the 2022 Winter Olympics – Women's tournament}}
|{{flagIOC|GBR|2022 Winter}}<br>[[Eve Muirhead]]<br>[[Vicky Wright]]<br>[[Jennifer Dodds]]<br>[[Hailey Duff]]<br>[[Mili Smith]]
|{{flagIOC|JPN|2022 Winter}}<br>[[Satsuki Fujisawa]]<br>[[Chinami Yoshida]]<br>[[Yumi Suzuki]]<br>[[Yurika Yoshida]]<br>[[Kotomi Ishizaki]]
|{{flagIOC|SWE|2022 Winter}}<br>[[Anna Hasselborg]]<br>[[Sara McManus]]<br>[[Agnes Knochenhauer]]<br>[[Sofia Mabergs]]<br>[[Johanna Heldin]]
|-
|Mixed doubles<br/>{{DetailsLink|Curling at the 2022 Winter Olympics – Mixed doubles tournament}}
|{{flagIOC|ITA|2022 Winter}}<br>[[Stefania Constantini]]<br>[[Amos Mosaner]]
|{{flagIOC|NOR|2022 Winter}}<br>[[Kristin Skaslien]]<br>[[Magnus Nedregotten]]
|{{flagIOC|SWE|2022 Winter}}<br>[[Almida de Val]]<br>[[Oskar Eriksson]]
|}
…
```

Gerekli bilginin mesajda olduğu ortaya çıktı, bu nedenle modelin mantık yürütme sorunu vardı.

Bu sorunun zor çözümü, modelin doğru yanıt vermesini sağlamak için arama veri kümesini geliştirmektir. 
Kolay yolu denemek için aynı sorguyu GPT-3.5 modelinden daha güçlü olan GPT-4 modeli ile çalıştırabiliriz:

```python
# GPT-4 modelini kullanarak sorguyu çalıştırın
ask('Hangi atletler 2022 Kış Olimpiyatları\'nda curlingde altın madalya kazandı?', model="gpt-4")
```

Bu kez, yanıt kadınlar karışık çiftler altın madalya kazananlarını içerir:

2022 Kış Olimpiyatları'nda curlingde altın madalya kazanan atletler şunlardır:
Erkekler turnuvası: İsveç'ten Niklas Edin, Oskar Eriksson, Rasmus Wranå, Christoffer Sundgren ve Daniel Magnusson.
Kadınlar turnuvası: Büyük Britanya'dan Eve Muirhead, Vicky Wright, Jennifer Dodds, Hailey Duff ve Mili Smith.
Karışık çiftler turnuvası: İtalya'dan Stefania Constantini ve Amos Mosaner.

# 5.3 Bölümündeki Örnekleri Deneyin
Sonraki bölüme geçmeden önce bu not defterinin aşağıdaki bölümündeki 5.3 bölümündeki örnekleri deneyin. Sistemin skorunu ve sınırlarını göreceksiniz. Şimdi soru-cevap için bir arama veri kümesini gömmeye devam edeceğiz.

---

