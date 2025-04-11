# Keskin Yazılım Kalite Kontrolü

Keskin yazılım kalite kontrolü, yenilikleri izlemek ve üretimdeki sistemleri iyileştirmek için sürekli insan müdahalesi gerektirir. Dönüştürücüler (Transformers) giderek daha karmaşık Doğal Dil İşleme (NLP) görevlerinin çoğunu üstlenecektir. Ancak, insan müdahalesi zorunludur. Sosyal medya devlerinin her şeyi otomatikleştirdiğini düşünüyoruz. Ardından, içerik yöneticilerinin bazen platformları için neyin iyi veya kötü olduğuna manuel olarak karar verdiklerini keşfediyoruz.

# Doğru Yaklaşım

Doğru yaklaşım, bir dönüştürücü eğitmek, uygulamak, çıktıyı kontrol etmek ve önemli sonuçları geri besleme yoluyla eğitim setine geri vermektir. Böylece, eğitim seti sürekli olarak gelişecek ve dönüştürücü öğrenmeye devam edecektir. Şekil 10.1, sürekli kalite kontrolün dönüştürücünün eğitim veri setinin büyümesine ve üretimdeki performansının artmasına nasıl yardımcı olacağını gösterir:

Şekil 10.1: Sürekli Kalite Kontrolü

Eğitim tamamlandıktan ve model kalite kontrolü ile üretime alındıktan sonra, sistemin genel yaşam döngüsünü ölçmek için sürekli insan kalite kontrolü gerekir. Raffel ve diğerleri (2019) tarafından açıklanan birkaç en iyi uygulamayı inceledik ve kurumsal Yapay Zeka projesi yönetimindeki deneyimlerime dayanarak bazı rehberlikler ekledim. Tokenizerlerle karşılaşılan bazı sınırların örnekleri ile bir Python programını inceleyelim.

Python kodları bulunmamaktadır, ancak bir Python programından bahsedilmektedir. Eğer bir Python kodu örneği verilseydi, satır satır açıklama yapılabilirdi. 

Örneğin, eğer aşağıdaki gibi bir Python kodu verilseydi:

```python
import pandas as pd
```

Bu satır, pandas kütüphanesini pd takma adıyla içe aktarır.

```python
df = pd.read_csv('data.csv')
```

Bu satır, 'data.csv' dosyasını okuyarak bir DataFrame oluşturur ve df değişkenine atar.

Böylece, her bir Python kodu satırı için açıklama yapılabilir. Ancak, verdiğiniz metinde Python kodu bulunmamaktadır.

---

