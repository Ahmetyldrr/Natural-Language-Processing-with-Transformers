# GPT-3.5-turbo veya GPT-4 için Arama Motoru Benzeri İstem Uygulanması

GPT-3.5-turbo veya GPT-4 için bir arama motoru benzeri istem uygulayacağız. İlk olarak, GPT-4'e bir istek göndermek için bir fonksiyon oluşturuyoruz, örneğin: 
```python
# convmodel = "gpt-3.5-turbo"
convmodel = "gpt-4"

def dialog(iprompt):
    client = OpenAI()
    response = client.chat.completions.create(
        model=convmodel,
        messages=iprompt
    )
    return response
```
Bu not defterinde, kullanıcı istekleri bir liste içinde yüklenir ve `dialog` fonksiyonunu çağıracak bir toplu istek yapılır. Aşağıdaki hücre altı adım içerir:

## Adım Adım İşlemler

1. **Kullanıcı İstekleri Üzerinde Döngü**: Kullanıcı istekleri üzerinde döngü yapılır.
2. **Anahtar Kelime Arama**: Uygulama, kullanıcı isteğini işler ve bir arama motoru benzeri teknikle anahtar kelimeleri arar.
3. **İstem Oluşturma**: Uygulama, bir sistem mesajı, bulunan bilgi tabanı kaydı ve ilk kullanıcı isteği ile bir istem oluşturur.
4. **İstem Gönderme**: İstem, ChatGPT `dialog` fonksiyonuna gönderilir.
5. **Yanıtı Depolama**: Yanıt, bir liste içinde depolanır.
6. **Bilgi Tabanını DataFrame Olarak Görüntüleme**: Bilgi tabanı, bir DataFrame olarak görüntülenir; Google Colaboratory sihirli çubuğuna tıklayarak güzel bir görünüm elde edebilirsiniz.

```python
responses = []  # dialog için bir liste oluşturma
# ChatGPT simülasyonu için kullanıcı istekleri üzerinde toplu olarak döngü
for i in range(n):
    # Adım 1: Kullanıcı istekleri üzerinde döngü
    user_request_num = i
    
    # Adım 2: Uygulama, kullanıcı isteğini işler ve bir arama motoru benzeri teknikle anahtar kelimeleri arar
    kb_record = parse_user(user_requests[user_request_num], kbkw, kbt)
    
    # Adım 3: Uygulama, bir istem oluşturur, sistem mesajı, bulunan bilgi tabanı kaydı ve ilk kullanıcı isteği ile
    iprompt = []
    iprompt.append({"role": "system", "content": "You are an assistant for Rothman Consulting."})
    iprompt.append(kb_record)
    iprompt.append(user_requests[user_request_num])
    # print(iprompt)
    
    # Adım 4: İstem, ChatGPT dialog fonksiyonuna gönderilir
    response = dialog(iprompt)
    
    # Adım 5: Yanıt, bir liste içinde depolanır
    ex = response.choices[0].message.content
    rt = "Total Tokens:" + str(response.usage.total_tokens)
    responses.append([user_requests[user_request_num], ex, rt])
    
    # Adım 6: Bilgi tabanı, bir DataFrame olarak görüntülenir
pd.DataFrame(responses, columns=['request', 'response', 'tokens'])
```

## Toplu İsteklerin Çıktıları

Toplu isteklerin çıktıları, bir pandas DataFrame içinde yüklenir:

### Şekil 15.6: Kullanıcı İstekleri Listesi

Bu, kullanıcı isteklerinin yanı sıra modelin verdiği yanıtları ve kullanılan toplam jeton sayısını içeren bir DataFrame'dir.

---

