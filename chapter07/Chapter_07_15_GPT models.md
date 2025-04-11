# OpenAI Sürekli Evrimleşiyor
OpenAI sürekli olarak gelişmektedir. Yeni modeller ortaya çıkarken diğerleri eskimektedir. Bazıları güncellenir, fonksiyon çağrıları değişir, API arayüzleri evrimleşir ve dokümantasyon birçok güncellemeden geçer. Bu, bu bölümün GPTs are GPTs bölümünde açıklanan genel amaçlı bir teknoloji için normaldir. Bu hızlı tempolu teknoloji ile başa çıkmak zorundayız. Neyse ki OpenAI, modellerinin evrimini bize bildiren çevrimiçi kaynaklara sahiptir. 
OpenAI'ın model dokümantasyon sayfası, model kategorilerini ve listelerini detaylı olarak açıklar: https://platform.openai.com/docs/models 
Liste, OpenAI modellerinin ana alanlarını içerir, örneğin dil, vizyon, embedding ve moderasyon. Bu alanları bu bölümde ve sonraki bölümlerde uygulayacağız. Örneğin, Chapter 11'de embedding modelini uygulayacağız: Leveraging LLM Embeddings as an Alternative to Fine-Tuning. 
Moderasyon ve whisper modellerini Chapter 15'te uygulayacağız: Guarding the Giants: Mitigating Risks in Large Language Models. 
Vizyon modellerini (OpenAI ve diğerleri) Chapter 16'da uygulamaya başlayacağız: Beyond Text: Vision Transformers in the Dawn of Revolutionary AI. 
OpenAI ayrıca, bu hızlı hareket eden pazarda "eski" modellerin emeklilik tarihlerini detaylandıran bir model eskitme sayfası sağlar: https://platform.openai.com/docs/deprecations. 
Şimdi OpenAI'ın kaputunu açalım ve mevcut modelleri ve varyantları inceleyelim. Bu not defteri, OpenAI'ın dokümantasyonuna danışırken model listesini ve varyantlarını görmenize yardımcı olacaktır. 
Open OpenAI_Models.ipynb dosyasını açın.

## OpenAI'ı Yükleme ve API Anahtarını Alma
İlk olarak OpenAI'ı yükleyeceğiz:
```python
try:
    import openai
except:
    !pip install openai
import openai
```
Ardından OpenAI API_KEY'ini bir dosyadan alacağız:
```python
from google.colab import drive
drive.mount('/content/drive')
f = open("drive/MyDrive/files/api_key.txt", "r")
API_KEY = f.readline()
f.close()
```
API_KEY'i bir dosyadan yükleyebilir veya gizlemek istemiyorsanız doğrudan girebilirsiniz.

## API Anahtarını Ortam Değişkeni Olarak Ayarlama
Şimdi API_KEY ile bir ortam değişkeni ayarlayabiliriz:
```python
import os
os.environ['OPENAI_API_KEY'] = API_KEY
openai.api_key = os.getenv("OPENAI_API_KEY")
```

## Modelleri ve Motorları Listeleme
Şimdi bir model ve motor listesi oluşturacağız:
```python
elist = openai.models.list()
print(elist)
```
Kaç model ve motor olduğunu öğrenmek istiyoruz:
```python
count = 0
for model in elist:
    count += 1
print("Number of models:", count)
```
Çıktı, model ve motor sayısını gösterir: Number of models: 81 
Bu liste ve sayı sürekli olarak değiştiğinden, OpenAI'ın dokümantasyonu (model ve eskitme sayfaları) ile birlikte bu listeyi düzenli olarak kontrol etmek iyi bir uygulamadır.

## Modelleri Pandas ile Sıralama
Aşağıdaki hücre, pandas'ta sıralanmış bir model listesi görüntüler (elist nesnesinin kendisi de değişebilir):
```python
import pandas as pd
model_data = []
# elist içindeki her bir model üzerinden yineleme yapın ve gerekli bilgileri toplayın
for model in elist:
    model_info = {
        'id': model.id,
        'created': model.created,
        'object': model.object,
        'owned_by': model.owned_by
    }
    model_data.append(model_info)
# Toplanan verilerden bir DataFrame oluşturun
df = pd.DataFrame(model_data)
# DataFrame'i 'id' sütununa göre sıralayın
df_sorted = df.sort_values(by='id')
# Sıralanmış DataFrame'i görüntüleyin
df_sorted
```
Artık id sütununda model listesini görebiliriz, Şekil 7.3'teki alıntıda gösterildiği gibi: 
Şekil 7.3: GPT tabanlı modellerin listesinin bir alıntısı 
OpenAI'ın kütüphanesi oldukça fazla fırsat ve keşif yoluna sahiptir! 
Unutmayın ki OpenAI tam hız ilerlemektedir ve bazı modelleri keskin modellerle düzenli olarak değiştirmektedir. 
Şimdi ChatGPT modellerini asistan olarak kullanmanın sihirbazlığına başlayacağız.

---

