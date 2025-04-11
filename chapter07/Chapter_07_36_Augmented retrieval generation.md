# İngilizce Paragrafın Birebir Türkçe Çevirisi

İlk olarak, ihtiyacımız olan modülleri ve sınıfları içe aktarıyoruz: 
```python
from openai import OpenAI
import ipywidgets as widgets
from IPython.display import display
```
Ardından, istemciyi ve modeli tanımlıyoruz: 
```python
client = OpenAI()
AImodel = "gpt-4"  # veya başka bir model seçin
```
API işlevini oluşturuyoruz: 
### OpenAI Modeli ile Etkileşim Kurmak için İşlev
```python
def openai_chat(input_text, document_excerpt, web_article_summary):
    # OpenAI API çağrısını başlatarak bir sohbet yanıtı oluşturun
    response = client.chat.completions.create(
        model=AImodel,
```
İstem mesajı üç rol içerir: 
- Belge alıntısı, herhangi bir kaynaktan gelebilir (veritabanı, web, metin dosyası, JSON veya sabit kodlanmış): 
    ```python
"role": "system",  
"content": f"The following is an excerpt from a document about climate change: {document_excerpt} "
```
- Web alıntısı, tanımladığımız özetleme işlevinden gelir: 
    ```python
"role": "system",  
"content": f"The following is a summary of a web article on renewable energy: {web_article_summary} "
```
- Kullanıcının girdi metni: 
    ```python
"role": "user",  
"content": input_text
```
Şimdi, bu bölümün "GPT-4 API'sine Başlarken" bölümünde incelediğimiz parametreleri tanımlıyoruz: 
```python
temperature=0.1,  # Rastgeleliği kontrol eder. Düşük değerler yanıtları daha deterministik hale getirir.
max_tokens=150,  # Yanıtın maksimum uzunluğunu belirler (kelimeler/kelime parçaları).
top_p=0.9,  # Çekirdek örnekleme: Daha yüksek bir değer yanıtın çeşitliliğini artırır.
frequency_penalty=0.5,  # Aynı metnin tekrarını azaltır. Daha yüksek değerler tekrarı caydırır.
presence_penalty=0.5  # Benzer konuların tekrarını azaltır. Daha yüksek değerler yeni konuları teşvik eder.
```
Yanıt, bir sözlük değil, bir sınıfın örneğidir: 
```python
return response.choices[0].message.content
```
Şimdi, kullanıcı isteğini tanımlayabiliriz: 
```python
input_text = "What are the impacts of climate change?"  
# input_text = "What is RAG"
```
Bu durumda, girdi metni kodda yer alır. Bir uygulama dağıttığınızda, kullanıcı isteği tasarladığınız arayüzden gönderilecektir. Buradaki örnek iklim değişikliği veya RAG olabilir. Daha ileri gitmek için belge alma işlevselliğini geliştirmek zorunda kalacaksınız. Bunun tasarım, geliştirme, telif hakkı yönetimi ve belge alma ve kullanımı ile ilgili tüm standart prosedürler için kaynak gerektirdiğini unutmayın.

Şimdi, kullanıcı isteğini hangi tür belge alıntısının kullanılacağına karar vermek için ayrıştırıyoruz. Bu giriş niteliğindeki eğitici örnek anahtar kelimeleri kullanır. Daha karmaşık ayrıştırıcılar uygulanabilir. Ayrıca, belge bu örnekte sabit kodlanmıştır. Bir PDF alabilir, özetleyebilir, tam bir metin ekleyebilir veya uygulamak istediğiniz başka bir içerik ekleyebilirsiniz. Bu durumda, iklim değişikliği üzerine odaklanıyoruz ancak bir belge alıntısı seçmeyi koda bırakıyoruz: 
```python
# 1. farklı durumlar için alanınıza özel bir işlev oluşturabilirsiniz:
if "climate" in input_text.lower():
    document_excerpt = "Climate change refers to significant changes in global temperatures and weather patterns over time."
if "RAG" in input_text.lower():
    document_excerpt = "OpenAI documentation states that RAG or retrieval augmented generation can tell the model about relevant documents."
```
Bilgileri sabit kodlayabilirsiniz, eğer bir ürün için müşteri desteği için ise ve ürünün yaşam döngüsü boyunca stabil olacaksa, veya özetleme işlevselliğini etkinleştirerek süreci otomatize edebilirsiniz: 
```python
# 2. ve/veya belge alma işlemini otomatize edebilirsiniz
summaries = fetch_and_summarize(input_text)
web_article_summary = summaries
```
Şimdi, belge alıntısını ve özetini OpenAI'a göndermeye hazırız, ayrıca kullanıcı isteği ile birlikte. GPT-4'ün yanıtı için önemli ölçüde geliştirilmiş bir bağlamı olacaktır: 
```python
iresponse = openai_chat(input_text, document_excerpt, web_article_summary)
formatted_response = iresponse.replace('\n', '<br>')  # \n'yi HTML satır sonlarına değiştirin
display(widgets.HTML(value=formatted_response))  # Yanıtı HTML olarak görüntüleyin
```
Yanıt ve çıktı ilginçtir: 
İklim değişikliği fiziksel çevreyi, ekosistemleri ve insan toplumlarını etkiler. Genel bir ısınma eğilimine, daha aşırı hava koşullarına ve yükselen deniz seviyelerine yol açar. Bu değişiklikler doğayı ve vahşi yaşamı, ayrıca insan yerleşimlerini ve toplumlarını olumsuz etkileyebilir.

RAG'ın, Üretken Yapay Zeka modellerinin kalitesini artırmak ve ayrıca yönlendirilmiş geliştirilmiş girdi istekleri yoluyla çıktıları kontrol etmek için oldukça iyi bir yol olabileceğini görebiliriz.

---

