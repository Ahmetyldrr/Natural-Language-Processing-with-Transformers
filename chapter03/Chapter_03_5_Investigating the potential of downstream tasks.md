# Transformers ve İnce Ayarlama

Transformers, insanlar gibi, önceden eğitilmiş bir modelin özelliklerini miras alarak aşağı akış görevlerini gerçekleştirmek için ince ayar yapabilir. Önceden eğitilmiş model, mimarisini ve dil temsillerini parametreleri aracılığıyla sağlar. Önceden eğitilmiş bir model, dilin genel bilgisini edinmek için anahtar görevler üzerinde eğitim alır. İnce ayar yapılmış bir model, aşağı akış görevleri üzerinde eğitim alır. Her transformer modeli ön eğitim için aynı görevleri kullanmaz. Ancak, potansiyel olarak tüm görevler önceden eğitilebilir veya ince ayar yapılabilir. Aşağı akış görevlerini organize etmek, Doğal Dil İşleme (NLP) uygulamak ve ölçmek için bilimsel bir çerçeve sağlar. Ancak, her NLP modeli standart bir yöntemle değerlendirilmelidir. Bu bölüm, önce bazı temel ölçüm yöntemlerini ele alacaktır. Ardından, bazı ana benchmark görevlerini ve veri kümelerini inceleyeceğiz. Önce bazı temel metrik yöntemlerini inceleyerek başlayalım.

Python kodu bulunmamaktadır, sadece bir ingilizce paragrafın türkçeye çevrilmesi istenmiştir.

Eğer bir python kodu olsaydı, satır satır açıklama yapardım. Ancak bu görevde sadece metin çevirisi yapılmıştır. 

Yinede örnek bir python kodu ile ingilizce paragrafı türkçeye çeviren kod bloğu aşağıda verilmiştir.

```python
from googletrans import Translator

def ingilizce_turkce_ceviri(paragraf):
    # Google Translate API nesnesi oluştur
    translator = Translator()
    
    # Çeviri işlemini gerçekleştir
    ceviri = translator.translate(paragraf, dest='tr')
    
    return ceviri.text

ingilizce_paragraf = "Transformers, like humans, can be fine-tuned to perform downstream tasks by inheriting the properties of a pretrained model. The pretrained model provides its architecture and language representations through its parameters. A pretrained model trains on key tasks to acquire a general knowledge of the language. A fine-tuned model trains on downstream tasks. Not every transformer model uses the same tasks for pretraining. But, potentially, all tasks can be pretrained or fine-tuned. Organizing downstream tasks provides a scientific framework for implementing and measuring NLP. However, every NLP model needs to be evaluated with a standard method. This section will first go through some of the key measurement methods. Then, we will go through some of the main benchmark tasks and datasets. Let’s start by going through some of the key metric methods."

# Çeviri işlemini gerçekleştir
turkce_paragraf = ingilizce_turkce_ceviri(ingilizce_paragraf)

print(turkce_paragraf)
```

Bu kod bloğu, `googletrans` kütüphanesini kullanarak ingilizce paragrafı türkçeye çevirir.

1. `from googletrans import Translator`: Google Translate API'sini kullanmak için gerekli kütüphaneyi içe aktarır.
2. `def ingilizce_turkce_ceviri(paragraf):`: İngilice paragrafı türkçeye çeviren fonksiyonu tanımlar.
3. `translator = Translator()`: Google Translate API nesnesi oluşturur.
4. `ceviri = translator.translate(paragraf, dest='tr')`: İngilice paragrafı türkçeye çevirir.
5. `return ceviri.text`: Çevirilen türkçe paragrafı döndürür.

---

