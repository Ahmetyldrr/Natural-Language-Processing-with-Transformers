# Depolama Alanı ve İzinlerin Yapılandırılması
Bir bucket (verilerin depolandığı bir konteyner) oluşturmak ve kullanmak için depolama alanına ve izinlere sahip olmanız gerekir: https://cloud.google.com/storage/docs/creating-buckets . Depolama alanınızı ve izinlerinizi yapılandırdıktan sonra, bucket'ınıza bir JSONL dosyası yükleyebilirsiniz. Bu örnekte yüklenen veri kümesi olan `sports2_prepared_valid.jsonl`, 8. Bölüm, OpenAI GPT Modellerini İnce Ayara Alma, bölüm 1.2. Verileri JSONL'e Dönüştürme ile aynı yöntem kullanılarak oluşturulan bir dosyadır. Bu veri kümesini, `sports2_prepared_valid.jsonl`, bu bölümün deposundan alabilir veya kendi seçtiğiniz bir tane hazırlayabilirsiniz.

## Veri Kümesinin Hazırlanması
Bu bölümdeki örnekte, veriler aşağıdaki kod ile alındı ve daha sonra 8. Bölüm'de açıklandığı gibi işlendi:
```python
from sklearn.datasets import fetch_20newsgroups
import pandas as pd
import openai

# Kategorilerin belirlenmesi
categories = ['rec.sport.baseball', 'rec.sport.hockey']

# Veri kümesinin yüklenmesi
sports_dataset = fetch_20newsgroups(subset='train', shuffle=True, random_state=42, categories=categories)
```
Amaç, kategorileri tanımlamaktır.

## Veri Kümesinin Yüklenmesi
İlk olarak, hazırlanan veri kümesini yüklüyoruz:
Şekil 14.14: Google'ın veri kümesi denetleyicisini ince ayarlamak için kullanılacak veri kümesini yüklemek aşağıdaki hatayı üretti: Hatalar Satır:0. Gerekli `input_text` veya `output_text` alanı(alanları) eksik.

`sports2_prepared_valid.jsonl` dosyası `prompt` ve `completion` içeriyor; bunları sırasıyla `input_text` ve `output_text` ile bulabilir ve değiştirebiliriz.

Bunun nedeni, LLMs'lerin genellikle üretken dönüştürücüler olmasına rağmen, tamamlayıcılar üretmeyen ancak Class_A veya Class_B gibi etiketler üreten ayrımcı (temel sınıflandırma) görevlerini gerçekleştirebilmeleridir. Bu durumda, daha genel "input" ve "output" ön eklerini kullanmak mantıklıdır çünkü hem ayrımcı hem de üretken görevleri kapsarlar.

Biçim zaman içinde değişebilir, ancak süreç aynı kalır: bir denetimli öğrenme görevi için bir istem ve bir etiket.

---

