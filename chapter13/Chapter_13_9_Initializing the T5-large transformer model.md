# Bu Alt Bölümde
Bu alt bölümde, bir T5-large modeli başlatacağız. GitHub'da bu bölümün dizininde bulacağınız aşağıdaki not defterini, Summarizing_Text_T5.ipynb, açın. T5 ile başlayalım! 

İstediğiniz çeviri yukarıda. Python kodları bulunmamaktadır. 

Eğer ingilizce paragrafı python içerisinde çevirmek isterseniz aşağıdaki kodları kullanabilirsiniz.

```python
# İngilizce paragrafı tanımlayalım
ingilizce_paragraf = "In this subsection, we will initialize a T5-large model. Open the following notebook, Summarizing_Text_T5.ipynb , which you will find in the directory of this chapter on GitHub. Let’s get started with T5 !"

# Çeviri için gerekli kütüphaneyi içe aktaralım
from deep_translator import GoogleTranslator

# Çeviri işlemini gerçekleştirelim
def ceviri(paragraf):
    # GoogleTranslator kullanarak ingilizce paragrafı türkçeye çevirelim
    translated_text = GoogleTranslator(source='auto', target='tr').translate(paragraf)
    return translated_text

# Çeviri işlemini çağıralım
ceviri_sonucu = ceviri(ingilizce_paragraf)

# Sonucu yazdıralım
print(ceviri_sonucu)
```

Yukarıdaki python kodlarının satır satır açıklamaları:

1. `# İngilizce paragrafı tanımlayalım` : İngilizce paragrafı bir değişkene atıyoruz.
2. `ingilizce_paragraf = "In this subsection, we will initialize a T5-large model. Open the following notebook, Summarizing_Text_T5.ipynb , which you will find in the directory of this chapter on GitHub. Let’s get started with T5 !"` : İngilizce paragrafı `ingilizce_paragraf` değişkenine atandı.
3. `# Çeviri için gerekli kütüphaneyi içe aktaralım` : Çeviri işlemi için gerekli olan `deep_translator` kütüphanesini içe aktarmak için kullanılan açıklama.
4. `from deep_translator import GoogleTranslator` : `deep_translator` kütüphanesinden `GoogleTranslator` sınıfını içe aktardık.
5. `# Çeviri işlemini gerçekleştirelim` : Çeviri işlemini gerçekleştirecek fonksiyonu tanımlamak için kullanılan açıklama.
6. `def ceviri(paragraf):` : `ceviri` adında, çeviri işlemini gerçekleştirecek bir fonksiyon tanımladık. Bu fonksiyon bir paragrafı parametre olarak alır.
7. `# GoogleTranslator kullanarak ingilizce paragrafı türkçeye çevirelim` : `GoogleTranslator` kullanarak çeviri işlemini gerçekleştirmek için kullanılan açıklama.
8. `translated_text = GoogleTranslator(source='auto', target='tr').translate(paragraf)` : `GoogleTranslator` sınıfını kullanarak, kaynak dili otomatik (`auto`) olarak belirleyip, hedef dili türkçe (`tr`) olarak belirledik ve `paragraf` değişkenini çevirdik. Çeviri sonucunu `translated_text` değişkenine atadık.
9. `return translated_text` : Çeviri sonucunu döndürdük.
10. `# Çeviri işlemini çağıralım` : Çeviri işlemini çağırmak için kullanılan açıklama.
11. `ceviri_sonucu = ceviri(ingilizce_paragraf)` : `ceviri` fonksiyonunu çağırarak, `ingilizce_paragraf` değişkenini çevirdik ve sonucu `ceviri_sonucu` değişkenine atadık.
12. `# Sonucu yazdıralım` : Çeviri sonucunu yazdırmak için kullanılan açıklama.
13. `print(ceviri_sonucu)` : Çeviri sonucunu yazdırdık.

---

