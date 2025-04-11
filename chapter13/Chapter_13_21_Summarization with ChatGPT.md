# Bölümün Amacı
Bu bölümün amacı, ChatGPT'nin özetleme konusunda Hugging Face'in T4 modellerinden daha iyi performans gösterip göstermediğini kanıtlamak değildir. Sadece içerik oluşturma kullanan başka bir özetleme paradigması ile deney yapmamız gerekiyor. Bu bölümün GitHub dizininde bulunan `Summarizing_ChatGPT.ipynb` dosyasını açın.

# OpenAI Kurulumu
İlk olarak, program OpenAI'in kurulumunu yönetir:
```python
# Openai'i içe aktarma
try:
    import openai
    from openai import OpenAI
except:
    !pip install openai -qq
    import openai
    from openai import OpenAI
```
Bu kod, OpenAI kütüphanesini içe aktarmaya çalışır. Eğer kütüphane yüklü değilse, `pip install openai` komutunu kullanarak kurulum yapar.

# API Anahtarı Alma
API anahtarı alınır:
```python
# 2. API Anahtarı
# Anahtarınızı bir dosyada saklayın ve okuyun (doğrudan not defterine yazabilirsiniz, ancak yanınızdaki biri tarafından görülebilir)
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
Bu kod, Google Colab'ı kullanarak API anahtarını bir dosyadan okur ve ortam değişkeni olarak ayarlar.

# Diyalog Fonksiyonu
Diyalog fonksiyonu oluşturulur:
```python
def dialog(uinput):
    # OpenAI için prompt hazırlama
    role = "user"
    line = {"role": role, "content": uinput}

    # Mesaj oluşturma
    assert1 = {"role": "system", "content": "You are a Natural Language Processing Assistant for summarizing."}
    assert2 = {"role": "assistant", "content": "Summarize the texts provided in the prompt."}
    assert3 = line
    iprompt = []
    iprompt.append(assert1)
    iprompt.append(assert2)
    iprompt.append(assert3)

    # Mesajı ChatGPT'ye gönderme
    client = OpenAI()
    response = client.chat.completions.create(model="gpt-4", messages=iprompt)

    # ChatGPT diyalog metni
    text = response.choices[0].message.content
    return text
```
Bu fonksiyon, kullanıcı girdisini alır ve ChatGPT'ye gönderir. Daha sonra, ChatGPT'nin cevabını döndürür.

# Özetleme İşlemi
Özetleme işlemi için bir metin seçilir:
```python
# Özetlenecek metin
input_text = "Summarize the following paragraph:…"
# ...
```
Bu metin, bir tıbbi makaleden alınmıştır.

# API İsteği
API isteği yapılır:
```python
uinput = input_text
text = dialog(uinput)
```
Bu kod, `dialog` fonksiyonunu çağırarak API isteğini yapar.

# Çıktı
Çıktı biçimlendirilir ve yazdırılır:
```python
wrapped_request = textwrap.fill(uinput, width=70)
print("Request ", wrapped_request)

wrapped_response = textwrap.fill(text, width=70)
print("ChatGPT response: ", wrapped_response)
```
Bu kod, hem isteği hem de cevabı biçimlendirir ve yazdırır.

# Sonuç
ChatGPT'nin cevabı mantıklı görünmektedir:
```
ChatGPT response:  Cell migration is critical for various processes like wound healing, angiogenesis, tumor formation, and metastasis. Cells respond to external signals, known as taxis, and migrate in a specific direction. Guidance cues for cell migration can be biochemical or biophysical. Examples include chemotaxis (dependent on the concentration of soluble molecules), electrotaxis (electric fields), phototaxis (light cues), haptotaxis (substratum-bound ligands), and durotaxis (matrix stiffness). The simultaneous sensing of multiple cues and their interaction is essential in understanding cell behavior during migration. Chemotaxis and contact guidance are key processes relevant to wound healing and cancer progression, and understanding the relationship between multiple directional cues can help unravel both physiological and pathological processes.
```
Bu özet, yalnızca bu alandaki tıbbi uzmanlar tarafından doğrulanabilir. Yapay zeka profesyonelleri, bu tür NLP görevlerinde insan uzmanlığına ihtiyaç duyulduğunu kabul etmelidir.

---

