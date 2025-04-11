# Shi ve Lin'in (2019) Araştırması ve Semantik Rol Etiketleme (SRL)

Shi ve Lin (2019), neyin kim tarafından ve nerede yapıldığını, sözcüksel veya sözdizimsel özelliklere bağlı kalmadan bulabileceğimizi ileri sürdü ve kanıtladı. Bu bölüm, Peng Shi ve Jimmy Lin'in California, Waterloo Üniversitesi'ndeki araştırmalarına dayanmaktadır. Transformerların dikkat katmanları ile dil yapılarını nasıl daha iyi öğrendiğini gösterdiler.

## Semantik Rol Etiketleme (SRL)

SRL, bir kelimenin veya kelime grubunun bir cümlede oynadığı rolü ve yüklem ile kurulan ilişkiyi etiketler. Semantik rol, bir isim veya isim tamlamasının bir cümlede ana fiile göre oynadığı roldür. Örneğin, "Marvin parkta yürüdü" cümlesinde, Marvin cümlede meydana gelen olayın failidir (agent). Fail, olayın gerçekleştiricisidir. Ana fiil (main verb) veya yönetici fiil (governing verb) "yürüdü"dür. Yüklem (predicate), özne veya fail hakkında bir şeyler tanımlar. Yüklem, bir öznenin özelliklerini veya eylemlerini tanımlayan herhangi bir şey olabilir. Yaklaşımımızda, yüklemi ana fiil olarak adlandıracağız. Örneğin, "Marvin parkta yürüdü" cümlesinde, yüklem "yürüdü" fiilinin kısıtlı halidir. "Parkta" kelimeleri "yürüdü" fiilinin anlamını değiştirir ve değiştiricidir (modifier). Yüklem etrafında dönen isim veya isim tamlamaları argümanlar veya argüman terimlerini oluşturur. Örneğin, "Marvin" "yürüdü" yükleminin bir argümanıdır.

## SRL'nin Özellikleri

SRL'nin bir sözdizim ağacı veya sözcüksel analiz gerektirmediğini görebiliriz. Örneğimize ait SRL'yi görselleştirelim.

Bu çeviride herhangi bir python kodu bulunmamaktadır. Eğer bir kod örneği isterseniz, lütfen belirtiniz. 

Eğer kod örneği verilseydi, örneğin:
```python
# Örnek bir SRL işlemi
def srl_islemi(cumle):
    # Cümleyi kelimelere ayırma
    kelimeler = cumle.split()
    
    # Kelimeleri etiketleme
    etiketler = []
    for kelime in kelimeler:
        # Kelimenin etiketini belirleme
        etiket = etiket_belirleme(kelime)
        etiketler.append(etiket)
    
    # SRL sonucunu döndürme
    return etiketler

def etiket_belirleme(kelime):
    # Kelimenin etiketini belirleme işlemi
    # Bu fonksiyon gerçek bir SRL modeliyle değiştirilmelidir
    return "Etiket"

# Örnek kullanım
cumle = "Marvin parkta yürüdü"
srl_sonucu = srl_islemi(cumle)
print(srl_sonucu)
```
Yukarıdaki kod örneğinde:
- `srl_islemi` fonksiyonu cümleyi kelimelere ayırır ve her kelime için `etiket_belirleme` fonksiyonunu çağırarak etiketleri belirler.
- `etiket_belirleme` fonksiyonu her kelimenin etiketini belirler. Gerçek bir SRL modeliyle değiştirilmesi gerekir.
- Örnek kullanım bölümünde, "Marvin parkta yürüdü" cümlesi için SRL işlemi yapılır ve sonuç yazdırılır.

---

