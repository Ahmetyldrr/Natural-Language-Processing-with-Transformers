# 2017-2020 Yılları Arasında Transformatör Modellerinin Gelişimi

Yalnızca 2017'den 2020'ye kadar, parametre sayısı, Tablo 7.1'de gösterildiği gibi, Orijinal Transformatör modelindeki 65M parametreden GPT-3 modelindeki 175B parametreye kadar arttı: 
Transformatör Modeli | Makale | Parametreler 
---------|----------|---------- 
Transformatör Base | Vaswani ve diğerleri. (2017) | 65M 
Transformatör Big | Vaswani ve diğerleri. (2017) | 213M 
BERT-Base | Devlin ve diğerleri. (2019) | 110M 
BERT-Large | Devlin ve diğerleri. (2019) | 340M 
GPT-2 Small | Radford ve diğerleri. (2019) | 117M 
GPT-2 Medium | Radford ve diğerleri. (2019) | 345M 
GPT-2 Large | Radford ve diğerleri. (2019) | 1.5B 
GPT-3 | Brown ve diğerleri. (2020) | 175B 
GPT-3.5 | OpenAI (Mart 2022) | 175B 
GPT-4 | OpenAI (Mart 2023) | - 
GPT-4V | OpenAI (Eylül 2023) | -

Tablo 7.1: Transformatör parametre sayısının evrimi

Tablo 7.1 yalnızca bu kısa süre zarfında tasarlanan ana modelleri içermektedir. Yayınların tarihleri, modellerin aslında tasarlandığı tarihten sonra gelmektedir. Bu tablonun bir anlık görüntü olduğunu ve Orijinal Transformatör piyasayı harekete geçirdikten sonra, Google Brain ve Research, OpenAI ve Facebook AI'den yeni transformatörlerin ve modellerin ortaya çıktığını unutmayın. Parametre sayısı, nispeten kısa bir süre içinde önemli ölçüde arttı ve GPT-3 için 175 milyar parametreye ulaştı. GPT-3.5 ve GPT-3.5-turbo'nun 175B parametresi vardır. GPT-4 modellerinin mimarisi hakkında bilgi azdır. OpenAI, GPT-4'ün mimarisinin detaylarını resmi olarak açıklamadı. Ancak, sistemi optimize ettiler ve aşağıdaki GPT-4 Teknik Raporu, 23 Mart 2023, sayfa 5'ten alıntılandığı gibi, iyi bilinen sınavlarda ve değerlendirmelerde yüksek puanlar elde ettiler:

# Şekil 7.1: GPT modeli performansı belirli sınavlarda

GPT-4 (GPT-4V'ye genişletildi) çok modlu (dil ve vizyon). Devrim niteliğindeki Yapay Zeka'nın Şafağında Metin: Vizyon Transformatörleri adlı 16. Bölüm'de bilgisayar vizyonu için transformatörleri keşfedeceğiz. ChatGPT, GPT-3.5-turbo, GPT-4, GPT-4V ve muhtemel gelecekteki iyileştirmeleri kapsayan bir şemsiye terimdir.

Mimari boyutu aynı anda gelişti: 
- Bir modelin katman sayısı, Orijinal Transformatör modelindeki 6 katmandan GPT-3 modelindeki 96 katmana çıktı. 
- Bir katmanın kafa sayısı, Orijinal Transformatör modelindeki 8'den GPT-3 modelindeki 96'ya çıktı. 
- Bağlam boyutu, Orijinal Transformatör modelindeki 512 belirteçten GPT-3 modelinin davinci sürümündeki 12.288'e çıktı.

Mimari boyutu, GPT-3 175B'nin neden sadece 40 katmanlı GPT-2 1.542M'den daha etkileyici sonuçlar ürettiğini açıklamaktadır. Her iki modelin parametreleri karşılaştırılabilir, ancak katman sayısı iki katına çıktı. Transformatörlerin hızlı evriminin bir başka yönünü anlamak için bağlam boyutuna odaklanalım.

Python kodları bulunmamaktadır, ancak yukarıdaki metin bir tablo ve şekil içermektedir. Bu tablonun ve şeklin Python kodları ile oluşturulmuş olsaydı nasıl olabileceğine dair bir örnek verebilirim:

```python
import pandas as pd

# Tablo 7.1 verileri
data = {
    "Transformatör Modeli": ["Transformatör Base", "Transformatör Big", "BERT-Base", "BERT-Large", "GPT-2 Small", "GPT-2 Medium", "GPT-2 Large", "GPT-3", "GPT-3.5", "GPT-4", "GPT-4V"],
    "Makale": ["Vaswani et al. (2017)", "Vaswani et al. (2017)", "Devlin et al. (2019)", "Devlin et al. (2019)", "Radford et al. (2019)", "Radford et al. (2019)", "Radford et al. (2019)", "Brown et al. (2020)", "OpenAI (Mart 2022)", "OpenAI (Mart 2023)", "OpenAI (Eylül 2023)"],
    "Parametreler": ["65M", "213M", "110M", "340M", "117M", "345M", "1.5B", "175B", "175B", "-", "-"]
}

df = pd.DataFrame(data)
print(df)
```

Bu kod, Tablo 7.1'i pandas DataFrame olarak oluşturur. Şekil 7.1 için ise bir grafik kütüphanesi (örneğin matplotlib) kullanılarak bir grafik oluşturulabilir. Ancak, orijinal metinde şekil verileri bulunmamaktadır.

---

