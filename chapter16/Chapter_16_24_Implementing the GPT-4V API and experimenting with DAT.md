# GPT-4 ile Görsel Analizi
GPT-4 ile vizyon (GPT-4V), OpenAI API aracılığıyla gönderdiğimiz görselleri analiz edebilir. Bazı oldukça farklı NLP semantik çağrışımlar ve CV görselleri ürettik. Ancak GPT-4V bunları tanıyabilir ve tanımlayabilir mi? Hadi öğrenelim. `GPT-4V.ipynb` dosyasını açın. Notebook, standart OpenAI kurulumu ve API anahtarı etkinleştirmesiyle başlar. Öncelikle GPT-4V'a standart bir farklı olmayan görseli analiz etmesini soracağız.

Python kodu bulunmamaktadır, ancak ilgili notebook dosyası `GPT-4V.ipynb` içerisindeki kodlara satır satır açıklama verebilirim. Ancak kod verilmediği için örnek bir kod üzerinden açıklama yapacağım.

Örnek Kod:
```python
# OpenAI kütüphanesini yükler
import openai

# API anahtarını etkinleştirir
openai.api_key = "API_ANAHTARINIZ"

# GPT-4V modelini kullanarak görsel analizi yapar
def analyze_image(image_path):
    response = openai.Image.analyze(
        image=open(image_path, "rb"),
        model="gpt-4v"
    )
    return response

# Analiz edilecek görselin path'i
image_path = "path/to/image.jpg"

# Görseli analiz eder
response = analyze_image(image_path)

# Analiz sonucunu yazdırır
print(response)
```
Satır satır açıklama:

1. `import openai`: OpenAI kütüphanesini yükler.
2. `openai.api_key = "API_ANAHTARINIZ"`: API anahtarını etkinleştirir. `API_ANAHTARINIZ` kısmını kendi API anahtarınızla değiştirin.
3. `def analyze_image(image_path):`: Görsel analizi yapan fonksiyonu tanımlar.
4. `response = openai.Image.analyze(...)`: GPT-4V modelini kullanarak görseli analiz eder.
5. `image=open(image_path, "rb")`: Analiz edilecek görseli binary modda okur.
6. `model="gpt-4v"`: Kullanılacak modeli GPT-4V olarak belirler.
7. `return response`: Analiz sonucunu döndürür.
8. `image_path = "path/to/image.jpg"`: Analiz edilecek görselin path'ini belirler.
9. `response = analyze_image(image_path)`: Görseli analiz eder.
10. `print(response)`: Analiz sonucunu yazdırır.

---

