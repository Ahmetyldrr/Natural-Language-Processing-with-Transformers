# Yapay Zeka Yakında Kendini Değerlendirebilecek mi?

Geleceğe bir adım atalım ve muhtemelen neler geleceğini görelim. Bu bölümün klasöründen Open Auto-BIG-bench.ipynb dosyasını açın. Program, GPT-4'e iki bölümlü bir istem ile 140'tan fazla BIG-bench görevinin bir örneğini besleyecektir. İlk bölüm aşağıdaki talimatları içerir: 
"1. Aşağıdaki görevi açıklayın
2. Bir örnek verin 
Çözün": 
Not edin ki talimatlar noktalama işaretleri gerektirmez, sadece boşluk bırakın. İkinci bölüm, BIG-bench'in tanımıdır, örneğin: 
Bir anlatı verildiğinde, en ilgili atasözünü seçin 
GPT-4 sonra: 
Talimatların ilk bölümünü okuyacak. 
Yapılacak BIG-bench NLP görevini okuyacak. 
Görevin bir örneğini oluşturacak. 
Çözülecek. 
Bu yön, fonksiyonel AGI'ye doğru başka bir adımdır. Gelecekte, başka bir AI modeli muhtemelen yanıtı değerlendirecek ve geliştirecektir. 
Bu potansiyel sıçramayı geleceğe doğru göstermek için program, ilk 10 örneği aşağıda gösterilen 144 BIG-bench NLP görevi işleyecektir: 
1. Aşağıdaki görevi açıklayın 
2. Bir örnek verin 
Çözün: 
Bir anlatı verildiğinde, en ilgili atasözünü seçin 
1. Aşağıdaki görevi açıklayın 
2. Bir örnek verin 
Çözün: 
Abstraction and Reasoning Corpus'tan görevleri çözün 
1. Aşağıdaki görevi açıklayın 
2. Bir örnek verin 
Çözün: 
Belirli bir ifadenin anachronizm içerip içermediğini belirleyin 
1. Aşağıdaki görevi açıklayın 
2. Bir örnek verin 
Çözün: 
İki olay arasındaki analoji türünü belirleyin 
1. Aşağıdaki görevi açıklayın 
2. Bir örnek verin 
Çözün: 
Bir cümlenin diğerini içerip içermediğini belirleyin 
1. Aşağıdaki görevi açıklayın 
2. Bir örnek verin 
Çözün: 
Dört temel aritmetik işlemi gerçekleştirin 
1. Aşağıdaki görevi açıklayın 
2. Bir örnek verin 
Çözün: 
ASCII sanatı olarak görüntülenen kelimeyi belirleyin 
1. Aşağıdaki görevi açıklayın 
2. Bir örnek verin 
Çözün: 
Verilen metin pasajlarından hangisinin referans olarak verilen metin pasajıyla aynı yazar tarafından yazıldığını belirleyin 
1. Aşağıdaki görevi açıklayın 
2. Bir örnek verin 
Çözün: 
Birkaç örnek verildiğinde geniş bir sınıfı belirleyin 
1. Aşağıdaki görevi açıklayın 
2. Bir örnek verin 
Çözün: 
Bir Python 3.7 programının ara durumuyla ilgili soruları yanıtlayın 
Bu not defteri için istemler önceden işlenmiştir: 
İstem'in ilk bölümü talimatları içermelidir. 
İkinci bölüm, 200'den fazla BIG-bench görevinden alınan 144 NLP görevinin bir örneğini içerir. 
Veri kümesi tasks.txt olarak adlandırıldı.

### Veri Kümesinin İndirilmesi ve İşlenmesi

Program, veri kümesini indirerek başlar: 
```python
!curl -L https://raw.githubusercontent.com/Denis2054/Transformers_3rd_Edition/master/Chapter15/tasks.txt --output "tasks.txt"
```
Veri kümesi daha sonra içe aktarılır, bir pandas DataFrame'e yüklenir ve görüntülenir: 
```python
import pandas as pd
# Dosyayı oku
df = pd.read_csv('tasks.txt', header=None, on_bad_lines='skip')
# Yükledikten sonra sütun adını ekleyin
df.columns = ['Tasks']
# DataFrame'i yazdır
print(df)
```
Çıktı aşağıdaki alıntıda görüntülenir: 
### Şekil 15.1: Auto-BIG-bench görevlerinin çıktısı

Görev sayısını kontrol ediyoruz: 
```python
nbt = len(df)
print("Görev sayısı: ", nbt)
```
Çıktı, 144 görevi doğrular: 
Görev sayısı: 144

### OpenAI'ın Kurulumu ve API Anahtarının Alınması

Şimdi OpenAI'ı kuruyoruz ve API anahtarını alıyoruz: 
```python
# Openai'ı içe aktarma
try:
    import openai
except:
    !pip install openai
    import openai

# API Anahtarı
# Anahtarınızı bir dosyada saklayın ve okuyun (direkt olarak not defterine yazabilirsiniz ancak yanınızdaki biri tarafından görülebilir)
f = open("drive/MyDrive/files/api_key.txt", "r")
API_KEY = f.readline()
f.close()

# OpenAI Anahtarı
import os
os.environ['OPENAI_API_KEY'] = API_KEY
openai.api_key = os.getenv("OPENAI_API_KEY")
```
GPT-4'ün rolünü, her NLP görevi için kendi örneklerini oluşturacak ve çözecek şekilde tanımlıyoruz: 
```python
client = OpenAI()
import openai
gptmodel = "gpt-4"  # veya gpt-3.5-turbo seçin

def openai_chat(input_text):
    response = openai.ChatCompletion.create(
        model=gptmodel,
        messages=[
            {"role": "system", "content": "You are an expert Natural Language Processing exercise expert."},
            {"role": "assistant", "content": "1. Herhangi bir NLP görevini açıklayabilirsiniz. 2. Bir örnek oluşturun 3. Örneği çözün"},
            {"role": "user", "content": input_text}
        ],
        temperature=0.1  # Sıcaklık parametresini buraya ekleyin ve ihtiyacınız olan diğer parametreleri
    )
    return response.choices[0].message.content
```
### 144 Görevin Çalıştırılması

144 görevi çalıştırmadan önce, her görevin isteğini ve yanıtını daha sonra kullanmak üzere görüntülemek ve kaydetmek için bir HTML çerçevesi oluşturuyoruz. 
```python
from IPython.core.display import display, HTML

def display_response(input_text, response, bb_task):
    html_content = f"""
    <!DOCTYPE html>
    <html>
    <head>
    <title>Big-bench Tasks</title>
    <style>
    p {{ max-width: 600px; }}
    </style>
    </head>
    <body>
    <h1>{bb_task}</h1>
    <p>{task}</p>
    </body>
    </html>
    """
    # Ve son olarak görüntüleriz
    display(HTML(html_content))
    html_file = open("output.html", "a")
    html_file.write(html_content)
    html_file.close()

html_file = open("output.html", "w")  # Görevleri çalıştırmadan önce yeni bir dosya oluşturulduğundan emin olmak için
html_file.close()
```
Son olarak, GPT-4'ün 144 NLP görevini istem yoluyla okumasını ve görevi gerçekleştirmesini sağlayan bir fonksiyon oluşturuyoruz: 
```python
import time
counter = 0
nb_tasks = nbt

for index, row in df.iterrows():
    input_text = row['Tasks']  # Tam istem
    counter += 1  # Görev sayacı
    if counter > nb_tasks:
        break  # Görev sayısı
    task = openai_chat(input_text)  # Model çağrısı
    task = task.replace('\n', '<br>')  # Çıktıyı biçimlendirme
    parts = input_text.split('Çözün:')  # Girişten görevi çıkarma
    bb_task = parts[1].strip()  # strip() fonksiyonu
    display_response(input_text, task, bb_task)  # Görevi ve yanıtı görüntüleme
    if counter % 50 == 0:  # Sayaç 50'ye bölünebiliyorsa
        print(f"{counter} görev işlendi. 60 saniye duraklatılıyor.")
        time.sleep(60)  # 60 saniye duraklat
```
OpenAI'ın kullanım oranı politikası nedeniyle bir uyku süresi eklendi. Görevleri çalıştırmadan önce OpenAI'ın oran limitleri politikasını kontrol edin: https://platform.openai.com/docs/guides/rate-limits/overview

### Çıktının Görüntülenmesi

Çıktı oldukça etkileyici! Görevi çalıştırmadan çıktıyı doğrudan da görüntüleyebilirsiniz. 
İlk olarak, kaydedilen çıktıyı indiriyoruz: 
```python
!curl -L .githubusercontent.com/Denis2054/Transformers_3rd_Edition/master/Chapter15/output.html --output "output.html"
```
Daha sonra, 144 görev için çıktıyı görüntüleriz: 
```python
from IPython.display import display, HTML

# HTML dosyasını okumak için open() fonksiyonunu kullanın
with open('/content/output.html', 'r') as f:
    html_string = f.read()

# HTML dizesini görüntülemek için HTML() fonksiyonunu kullanın
display(HTML(html_string))
```
Birçok yanıt doğru, bazıları değil. Ancak süreç, AI'ın fonksiyonel bir AGI haline gelme yolunda büyük bir potansiyel taşıdığını gösteriyor. 

### Sonuç

Bu not defteri, AI'ın yükselen gücünü ve LLMs'i kontrol etmede ortaya çıkan zorlukları gösteriyor. WandB, otomatik AI öz-değerlendirmesinin yükselişine katkıda bulunan başka bir araçtır.

---

