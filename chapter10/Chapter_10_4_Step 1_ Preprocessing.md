# Veri Kümelerinin Ön İşlemesi

Raffel ve diğerleri (2019) modelleri eğitmeden önce veri kümelerini ön işlemden geçirmeyi önerdiler ve ben de bazı ekstra fikirler ekledim. Dönüştürücüler (Transformers) dil öğrenenler haline geldi ve biz de onların öğretmenleri olduk. Ancak bir makine öğrencisine dil öğretmek için, örneğin düzgün İngilizce'nin ne olduğunu açıklamak zorundayız. Veri kümelerini kullanmadan önce bazı standart sezgisel yöntemleri uygulamak zorundayız:

## Noktalama İşaretli Cümleler
Tavsiye, nokta veya soru işareti gibi noktalama işaretleriyle biten cümleleri seçmektir.

## Kötü Kelimelerin Kaldırılması
Kötü kelimeler kaldırılmalıdır. Bu kelimelerin listeleri örneğin şu sitede bulunabilir: https://github.com/LDNOOBW/List-of-Dirty-Naughty-Obscene-and-Otherwise-Bad-Words

## Kodun Kaldırılması
Bu zor çünkü bazen aradığımız içerik kodlardır. Ancak genellikle NLP görevleri için içerikten kodları kaldırmak en iyisidir.

## Dil Tespiti
Bazen web siteleri varsayılan "lorem ipsum" metni içeren sayfalar içerir. Bir veri kümesinin tüm içeriğinin istediğimiz dilde olduğundan emin olmak gerekir. İyi bir başlangıç noktası, 50'den fazla dili algılayabilen langdetect'tir: https://pypi.org/project/langdetect/

```python
# Langdetect kütüphanesini kullanarak dil tespiti örneği
from langdetect import detect

text = "Bu bir Türkçe metindir."
print(detect(text))  # Çıktı: tr
```

## Ayrımcılığa Atıfların Kaldırılması
Bu zorunludur. Web'den veya belirli veri kümelerinden kazıdığınız her şeyi içeren bir bilgi tabanı oluşturmanızı öneririm. Her türlü ayrımcılığı bastırın. Makinenizin etik olmasını istiyorsunuz!

## Mantık Kontrolü
Eğitilmiş bir dönüştürücü modelini, anlamsız cümleleri filtrelemek için Doğal Dil Çıkarımı (NLI) yapan bir veri kümesi üzerinde çalıştırmak iyi bir fikir olabilir.

## Kötü Bilgi Atıfları
Çalışmayan bağlantılara, etik olmayan web sitelerine veya kişilere atıfta bulunan metinleri ortadan kaldırın. Bu zor bir iş ama kesinlikle değer.

Bu liste bazı birincil en iyi uygulamaları içerir. Ancak, belirli projeler için gizlilik yasası ihlallerini filtrelemek ve diğer eylemleri gerçekleştirmek gibi daha fazlası gereklidir. Bir dönüştürücü düzgün İngilizce öğrenmek üzere eğitildikten sonra, üretim aşamasında girdi metinlerindeki sorunları tespit etmesine yardımcı olmalıyız.

---

