# Örnek Uygulama: Codechat-Bison Uygulaması

Bu örnek için, codechat-bison kodunu uygulayacağız. Kodlama problemi için basit bir istekte bulunacağız:

```python
from vertexai.preview.language_models import CodeChatModel
vertexai.init(project="aiex-57523", location="us-central1")
chat_model = CodeChatModel.from_pretrained("codechat-bison@001")
parameters = {"temperature": 0.5, "max_output_tokens": 1024}
chat = chat_model.start_chat()
response = chat.send_message("""Python'da Fibonacci serisini 10'a kadar hesaplayan bir fonksiyon için kodu yazın:""", **parameters)
print(f"Modelden Gelen Yanıt: {response.text}")
```

# Beklenen Yanıt

10'a kadar Fibonacci serisi için kod içeren bir yanıt bekliyoruz. Ve gerçekten de, yanıt doğru görünüyor:

Modelden Gelen Yanıt: Fibonacci dizisi, her sayının önceki iki sayının toplamı olduğu bir sayı dizisidir. Dizi 0 ve 1 ile başlar ve ardından her sayı önceki iki sayının toplamıdır. Yani dizi şöyle görünür:
0, 1, 1, 2, 3, 5, 8, 13, 21, 34, ...
Herhangi bir sayıya kadar Fibonacci dizisini hesaplamak için Python'da bir fonksiyon yazabilirsiniz. İşte bir örnek:
```python
def fibonacci(n):
  """
  Bu fonksiyon verilen sayıya kadar Fibonacci dizisini hesaplar.
  Args:
    n: Fibonacci dizisini hesaplamak için verilen sayı.
  Returns:
    Verilen sayıya kadar Fibonacci dizisi.
  """
  # Diziyi 0 ve 1 ile başlatın.
  a = 0
  b = 1
  # Diziyi, her sayıyı önceki sayıya ekleyerek yineleyin.
  for i in range(n):
    a, b = b, a + b
  # Diziyi döndürün.
  return a
```
Bu fonksiyon, girdi olarak bir sayı alır ve o sayıya kadar Fibonacci dizisini döndürür. Örneğin, fonksiyona 10 girdiğini verirseniz, aşağıdaki diziyi döndürecektir:
0, 1, 1, 2, 3, 5, 8, 13, 21, 34
Tabii ki, 0'dan başlarsanız, 34'e ulaşacaksınız. 1'den başlarsanız, 55'e ulaşacaksınız.

# Yanıtın Doğrulanması

Şimdi, bu yanıtın anlamlı olup olmadığını kontrol etmek ve bir sonraki hücrede çalıştırmak istiyoruz:
```python
def fibonacci(n):
  """
  Bu fonksiyon verilen sayıya kadar Fibonacci dizisini hesaplar.
  Args:
    n: Fibonacci dizisini hesaplamak için verilen sayı.
  Returns:
    Verilen sayıya kadar Fibonacci dizisi.
  """
  # Diziyi 0 ve 1 ile başlatın.
  a = 0
  b = 1
  # Diziyi, her yeni sayıyı hesaplayarak yineleyin.
  for i in range(n):
    # Dizideki bir sonraki sayıyı hesaplayın.
    c = a + b
    # Diziyi güncelleyin.
    a = b
    b = c
  # Diziyi döndürün.
  return a, b

# Fonksiyonu çağırın:
fibonacci(10)
```
Çıktı kavramsal olarak doğru, ancak sonuç doğru değil: (55, 89)
89, 10'dan fazla adım gerektirir.

# Yanıtın Düzeltmesi

Şimdi, PaLM 2'ye ürettiği kodu düzeltmesini soralım:
```python
import vertexai
from vertexai.preview.language_models import CodeGenerationModel
vertexai.init(project="aiex-57523", location="us-central1")
parameters = {"temperature": 0.2, "max_output_tokens": 1024}
model = CodeGenerationModel.from_pretrained("code-bison@001")
response = model.predict(
    prefix="""0 veya 1'den başlayarak 10 sayıya kadar Fibonacci serisini hesaplayan Python kodunu düzeltin. Kod, 10 sayı yerine 11 sayı hesapladığı için yanlış. Düzeltin:""",
    **parameters
)
print(f"Modelden Gelen Yanıt: {response.text}")
```
Modelden Gelen Yanıt:
```python
def fibonacci(n):
  """
  n'inci Fibonacci sayısını hesaplar.
  Args:
    n: Hesaplanacak n'inci Fibonacci sayısı.
  Returns:
    n'inci Fibonacci sayısı.
  """
  if n == 0:
    return 0
  elif n == 1:
    return 1
  else:
    return fibonacci(n - 1) + fibonacci(n - 2)
print(fibonacci(10))
```
# Düzeltmenin Doğrulanması

Kodu yapıştırıp test edebiliriz:
```python
def fibonacci(n):
  """
  n'inci Fibonacci sayısını hesaplar.
  Args:
    n: Hesaplanacak n'inci Fibonacci sayısı.
  Returns:
    n'inci Fibonacci sayısı.
  """
  if n == 0:
    return 0
  elif n == 1:
    return 1
  else:
    return fibonacci(n - 1) + fibonacci(n - 2)
print(fibonacci(10))
```
Çıktı doğru: 55

# Sonuç

Bu örnek, Büyük Dil Modellerinin (LLM) yüzlerce Doğal Dil İşleme (NLP) görevini yerine getirme potansiyelini göstermektedir. Bu potansiyel, "Kapsamlı Çoklu Görev Dil Anlama" (MMLU) terimini doğurmuştur. LLM'ler, ileride hemen hemen her NLP görevini yerine getirebilecek hale gelecektir. Ancak, LLM'ler bazen belirli bir proje için başarısız olabilir ve bu durumda bir Google AI modelini fine-tune etmek gerekebilir.

---

