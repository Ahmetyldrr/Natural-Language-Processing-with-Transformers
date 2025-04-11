# OpenAI Model İnce Tunlama

OpenAI, GPT-3 serisi, GPT-4, Babbage-002 ve Davinci dahil olmak üzere bir dizi modeli ince ayarlamak için bir hizmet sunar. Bu modellerin bazıları önerilirken, diğerleri deneyseldir. Ancak, bu modellerden birini seçip seçmemek nihayetinde sizin kararınıza bağlıdır. İnce ayarlanmış bir model, orijinal modeller gibi veri keşfi, sınıflandırma, soru cevaplama ve diğer NLP görevlerini gerçekleştirebilir. Bu nedenle, ince ayarlanmış model kabul edilebilir veya yanlış sonuçlar üretebilir. Kalite kontrolü hala önemlidir. Bir projeye başlamadan önce OpenAI'ın belgelerini incelediğinizden emin olun: https://platform.openai.com/docs/guides/fine-tuning/. Bu bölüm, bir modeli bir not defterinde hücre hücre ince ayarlamayı uygulamayı amaçlamaktadır, böylece ince ayarlamayı kendi özel alanınıza uygulayabilirsiniz.

## GPT Modellerini İnce Ayarlama Süreci

GPT modellerini ince ayarlamak dört aşamayı içerir, ki biz bu bölümde bunları uygulayacağız:
1. Verileri hazırlama.
2. Babbage-002 modeli ile bir üretken görev (tamamlama) için GPT-3 mimarisini ince ayarlamak.
3. İnce ayarlanmış modeli çalıştırma.
4. Modelleri yönetme.

Bir OpenAI modelini nasıl ince ayarlayacağınızı öğrendikten sonra, diğer veri türlerini kullanarak ona özel alanlar, bilgi grafikleri ve metinler öğretebilirsiniz. Diğer modelleri de değerlendirebilirsiniz. Gördüğünüz gibi, eğitim süreci, 5. Bölüm'de BERT aracılığıyla İnce Ayarlamaya Dalma ve 6. Bölüm'de RoBERTa aracılığıyla Sıfırdan bir Transformer Ön Eğitimi'nde uyguladıklarımıza benzer. Gerçek hayattaki projelerde, yalnızca maliyet etkin sonuçlar önemlidir. Bir modele ve sürece enerji ve kaynaklarınızı yatırmadan önce birkaç seçeneği keşfedin. Bu bölümdeki programı çalıştırmadan önce bir OpenAI modelini ince ayarlamanın maliyetini değerlendirin.

## OpenAI Kütüphanesini Yükleme ve API Anahtarını Alma

Başlamak için, GitHub bölüm dizinindeki Fine_Tuning_OpenAI_Models.ipynb dosyasını Google Colab'da açın ve önce OpenAI kütüphanesini yükleyin ve anahtarınızı girin:
```python
try:
    import openai
except:
    !pip install openai
    import openai
```
API anahtarınızı bir dosyadan alabilir veya aşağıdaki kodu yorumlayabilir ve anahtarınızı manuel olarak girebilirsiniz. Anahtarı bir dosyadan okumak için Google Drive veya istediğiniz herhangi bir dosya sistemini kullanabilirsiniz:

### (1) API Anahtarını Bir Dosyadan Alma
```python
# API Anahtarını bir dosyadan al
from google.colab import drive
drive.mount('/content/drive')
f = open("drive/MyDrive/files/api_key.txt", "r")
API_KEY = f.readline()
f.close()
```

### (2) API Anahtarını Manuel Olarak Girme
```python
# API Anahtarını manuel olarak gir
# API_KEY yerine anahtarınızı girin
import os
os.environ['OPENAI_API_KEY'] = API_KEY
openai.api_key = os.getenv("OPENAI_API_KEY")
```
Artık veri setini hazırlamaya ve bir OpenAI modelini ince ayarlamaya hazırsınız.

**Kod Açıklamaları:**

1. `try` bloğu OpenAI kütüphanesini içe aktarmayı dener. Eğer kütüphane yüklü değilse, `except` bloğu çalışır ve `!pip install openai` komutu ile OpenAI kütüphanesini yükler.
2. API anahtarını bir dosyadan okumak için Google Drive'ı bağlar ve `api_key.txt` dosyasını okur.
3. API anahtarını manuel olarak girmek için `os` kütüphanesini kullanarak ortam değişkeni olarak ayarlar ve OpenAI kütüphanesine anahtarı iletir.

---

