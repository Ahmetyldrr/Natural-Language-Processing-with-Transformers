# Tiktoken ve OpenAI Kütüphanelerinin Kurulumu

İlk olarak, token sayısını saymak için kullanılacak olan tiktoken kurulur. 
```python
!pip install tiktoken
```
Program daha sonra OpenAI kütüphanesini kurar:
```python
try:
    import openai
except:
    !pip install openai
    import openai
```
Not: Bu bölümde, en son OpenAI API sürümünü uygulayacağız. Bu seçenek yeni bir proje üzerinde çalışırken verimlidir. Ancak, kritik bir proje üretimdeyse, bir sonraki bölümde göreceğimiz gibi Ada Embeddings ile Transfer Öğrenme bölümünde olduğu gibi OpenAI'ın sürümünü sabitleyebilirsiniz.

# API Anahtarının Alınması

Program, Google Drive'daki bir dosyadan API anahtarını alır:
```python
from google.colab import drive
drive.mount('/content/drive')
f = open("drive/MyDrive/files/api_key.txt", "r")
API_KEY = f.readline()
f.close()
```
API anahtarını bir dosyada saklayabilirsiniz, böylece programda görünmez. Doğrudan girilebilir, ancak görünür olacaktır.

# API Anahtarının Ortam Değişkenine Atanması

Program, API anahtarını bir ortam değişkenine atar:
```python
import os
os.environ['OPENAI_API_KEY'] = API_KEY
openai.api_key = os.getenv("OPENAI_API_KEY")
```
Artık gerekli modülleri içe aktarabiliriz:

# Gerekli Modüllerin İçe Aktarılması
```python
# içe aktarmalar
import ast  # dizileri string olarak kaydedilen embeddingsleri dizilere çevirmek için
import openai  # OpenAI API'sini çağırmak için
import pandas as pd  # metin ve embeddings verilerini depolamak için
import tiktoken  # bu programda token sayısını saymak için
from scipy import spatial  # arama için vektör benzerliklerini hesaplamak için
```
Sonraki adım, modellerin uygulanmasıdır.

---

