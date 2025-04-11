# GPT-4 için ChatGPT Fonksiyonu Oluşturma

GPT-4 için bir ChatGPT fonksiyonu oluşturacağız. GPT-4'e erişiminiz yoksa, başka bir son modelini de deneyebilirsiniz. Çıktılar bir modelden diğerine farklılık gösterebilir. Ajanın rolünü tanımlarız, sistem rolünü açıklarız ve ayrıca asistanın rolünü de tanımlarız.

## Kullanıcı Girişini İşleme

Kullanıcı isteğini ekleriz: 
```python
def dialog(uinput):
```
### Prompt Hazırlama

OpenAI için prompt hazırlıyoruz
```python
    role = "user"
    line = {"role": role, "content": uinput}
```
#### Mesaj Oluşturma

Mesajı oluşturuyoruz
```python
    assert1 = {"role": "system", "content": "You are a Natural Language Processing Assistant for Semantic Role Labeling."}
    assert2 = {"role": "assistant", "content": "You provide Semantic Role Labeling and display the result in a nice chart."}
    assert3 = line
    iprompt = []
    iprompt.append(assert1)
    iprompt.append(assert2)
    iprompt.append(assert3)
```
### OpenAI İstemcisi Oluşturma

OpenAI istemcisini oluşturuyoruz
```python
    client = OpenAI()
```
### Mesajı ChatGPT'ye Gönderme

Mesajı ChatGPT'ye gönderiyoruz
```python
    response = openai.ChatCompletion.create(model="gpt-4", messages=iprompt)
```
### Yanıtı Alma

ChatGPT diyalog metnini alıyoruz
```python
    text = response["choices"][0]["message"]["content"]
```
### Yanıtı Dönderme

Yanıtı JSON formatında döndürüyoruz
```python
    return text
```
Fonksiyon, isteği gpt-4'e gönderecek ve yanıtı `text` değişkeninde döndürecektir. Artık SRL isteklerini çalıştırabiliriz.

---

