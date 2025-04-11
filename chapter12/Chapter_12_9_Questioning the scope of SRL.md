# Gerçek Hayat Projesiyle Yüzleştiğimizde
Gerçek hayat projesiyle karşı karşıya kaldığımızda yalnızız. Yapmamız gereken bir iş var ve memnun etmek zorunda olduğumuz tek kişiler o projeyi talep edenlerdir. Pragmatizm ilk sırada gelmelidir - teknik ideoloji ondan sonra gelir. 2020'li yıllarda, eski AI ideolojisi ve yeni ideoloji bir arada var olur. On yılın sonunda, iki dünya yeni bir çağı oluşturmak üzere birleşecektir. Bu bölüm, SRL'nin üretkenliğini ve motivasyonunu iki açıdan sorgulamaktadır: 
# Yüklem Analizinin Sınırı 
"Anlamsal" teriminin kullanımını sorgulama


Python kodu bulunmamaktadır, sadece bir ingilizce paragrafın türkçeye çevirisi yapılmıştır.

Eğer ingilizce paragrafı türkçeye çeviren bir python kodu yazmak isteseydik, aşağıdaki gibi bir kod yazabilirdik:

```python
# Googletrans kütüphanesini kullanarak ingilizce metni türkçeye çevirme

from googletrans import Translator

def ceviri(metin):
    translator = Translator()
    sonuc = translator.translate(metin, dest='tr')
    return sonuc.text

ingilizce_paragraf = "We are alone when faced with a real-life project. We have a job to do, and the only people to satisfy are those who asked for that project. Pragmatism must come first – technical ideology after . In the 2020s, former AI ideology and new ideology coexist. By the decade’s end, the two worlds will have merged to form a new era. This section questions the productivity of SRL and its motivation through two aspects: The limit of predicate analysis Questioning the use of the term “semantic”"

turkce_paragraf = ceviri(ingilizce_paragraf)
print(turkce_paragraf)
```

Bu kod, `googletrans` kütüphanesini kullanarak ingilizce paragrafı türkçeye çevirir.

1. `from googletrans import Translator`: Googletrans kütüphanesinden Translator sınıfını içe aktarır.
2. `def ceviri(metin):`: `ceviri` adında bir fonksiyon tanımlar. Bu fonksiyon, ingilizce metni türkçeye çevirir.
3. `translator = Translator()`: Translator sınıfından bir nesne oluşturur.
4. `sonuc = translator.translate(metin, dest='tr')`: `translate` metodunu kullanarak ingilizce metni türkçeye çevirir. `dest='tr'` parametresi, çeviri dilinin türkçe olduğunu belirtir.
5. `return sonuc.text`: Çeviri sonucunu döndürür.
6. `ingilizce_paragraf = "..."`: Ingilizce paragrafı bir değişkene atar.
7. `turkce_paragraf = ceviri(ingilizce_paragraf)`: `ceviri` fonksiyonunu kullanarak ingilizce paragrafı türkçeye çevirir.
8. `print(turkce_paragraf)`: Türkçeye çevrilmiş paragrafı yazdırır.

---

