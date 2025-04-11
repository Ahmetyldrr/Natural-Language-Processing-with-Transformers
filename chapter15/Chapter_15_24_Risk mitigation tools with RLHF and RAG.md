# Bu Bölümün Konusu
Bu bölüm, bizi, bu alana başlamak için bazı azaltma araçlarıyla birlikte hızlı tasarım dan gelişmiş hızlı mühendisliğe kadar götürecektir: RLHF. İnsan Geri Bildirimli Pekiştirmeli Öğrenme (RLHF) bu bölümde açıklanan sürecin ötesinde düzenlenebilir. Terim korkutucu görünebilir, ancak bunu sisteminizin yanıtları hakkında geri bildirim sağlayabilecek bir grup kilit kullanıcı ile düzenleyebilirsiniz. Ardından, modeli yeniden ince ayar yapmadan veya örneğin RAG'ı uygulamadan önce hiperparametreleri, parametreleri, veri kümelerini ve projenin herhangi bir yönünü buna göre uyarlayabilir ve değiştirebilirsiniz.

## RAG
Bu bölüm, bir bilgi tabanı aracılığıyla Erişim-Geliştirilmiş Üretim (RAG) yöntemini uygular. Bölüm 7, ChatGPT ile Üretken Yapay Zeka Devrimi ve Bölüm 11, İnce Ayar yerine LLM Gömme Kullanma gibi uyguladığımız birkaç olası yaklaşım vardır. Özel bir bilgi tabanı etkili bir çözüm olabilir. Her proje belirli bir yaklaşım gerektirecektir. Amaç, öngörülemeyen açık bir ortamdan kapalı ve izlenen bir ekosisteme geçmektir.

### Azaltma Teknikleri
Bu bölümdeki beş azaltma tekniğinin başlıkları, not defterindekiyle aynıdır. GitHub deposunun chapter dizininde Open Mitigating Generative AI.ipynb dosyasını açın.

#### OpenAI Kurulumu
İlk olarak, OpenAI'ı kurun:
```python
# Openai'ı içe aktarma
try:
    import openai
except:
    !pip install openai
    import openai
```
#### Kimlik Doğrulama İşlemi
Ardından, API anahtarınızla kimlik doğrulama işlemini etkinleştirin:
```python
# 2.API Anahtarı
# Anahtarınızı bir dosyada saklayın ve okuyun (direkt not defterine yazabilirsiniz ancak yanınızdaki biri için görünür olur)
from google.colab import drive
drive.mount('/content/drive')
f = open("drive/MyDrive/files/api_key.txt", "r")
API_KEY = f.readline()
f.close()

# OpenAI Anahtarı
import os
os.environ['OPENAI_API_KEY'] = API_KEY
openai.api_key = os.getenv("OPENAI_API_KEY")
```
Bu işlemlerin ardından OpenAI moderasyon modeli ve bir kural ile başlayacağız.

# Kod Açıklamaları

1. `try: import openai except: !pip install openai import openai` 
   - Bu satır, OpenAI kütüphanesini içe aktarmaya çalışır. Eğer kütüphane yoksa, `pip install openai` komutunu çalıştırarak kütüphaneyi kurar ve ardından içe aktarır.

2. `from google.colab import drive` 
   - Google Colab'da drive'ı içe aktarır.

3. `drive.mount('/content/drive')` 
   - Google Drive'ı Colab'a bağlar.

4. `f = open("drive/MyDrive/files/api_key.txt", "r")` 
   - Belirtilen yoldaki `api_key.txt` dosyasını okumak için açar.

5. `API_KEY = f.readline()` 
   - Dosyadan ilk satırı okur ve `API_KEY` değişkenine atar.

6. `f.close()` 
   - Dosyayı kapatır.

7. `import os` 
   - İşletim sistemi ile ilgili işlemler için `os` modülünü içe aktarır.

8. `os.environ['OPENAI_API_KEY'] = API_KEY` 
   - `OPENAI_API_KEY` adlı ortam değişkenine `API_KEY` değerini atar.

9. `openai.api_key = os.getenv("OPENAI_API_KEY")` 
   - OpenAI kütüphanesinin `api_key` özelliğine, `OPENAI_API_KEY` ortam değişkeninin değerini atar.

---

