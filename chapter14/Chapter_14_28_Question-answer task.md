# İngilizce Paragrafın Türkçe Çevirisi

Bu istek, referans alınacak metin içermeyen açık bir soru içerecektir. Bu sefer, bir fonksiyon oluşturacağız. Fonksiyon, tam isteği içerir. Değiştirilebilir ve özelleştirilebilir:

```python
from vertexai.preview.language_models import ChatModel, InputOutputTextPair

def predict_large_language_model_sample(
    project_id: str,
    model_name: str,
    temperature: float,
    max_output_tokens: int,
    top_p: float,
    top_k: int,
    location: str = "us-central1",
):
    """Büyük Dil Modeli kullanarak tahmin edin."""
    # vertexai kütüphanesini projeye göre başlatır
    vertexai.init(project=project_id, location=location)
    
    # ChatModel'i önceden eğitilmiş model adı ile oluşturur
    chat_model = ChatModel.from_pretrained(model_name)
    
    # Model parametrelerini ayarlar
    parameters = {
        "temperature": temperature,
        "max_output_tokens": max_output_tokens,
        "top_p": top_p,
        "top_k": top_k,
    }
    
    # Boş örnek listesi ile sohbeti başlatır
    chat = chat_model.start_chat(examples=[])
    
    # Mesajı belirtilen parametrelerle gönderir
    response = chat.send_message(
        '''Bu konuşma için hangi Transformer modelini kullanıyorsunuz?''',
        **parameters
    )
    
    # # Yanıtın metiniyi yazdırır (yorum satırı)
    # print(response.text)
    
    # Yanıt metnini 40 karakter genişliğinde kaydırır
    wrapped_text = textwrap.fill(response.text, width=40)
    
    # Kaydırılmış metni yazdırır
    print(wrapped_text)
```

# Fonksiyonun Çağrılması

PaLM 2'nin hangi modeli kullandığını soran fonksiyonu çağırıyoruz:

```python
predict_large_language_model_sample(
    "aiex-57523",
    "chat-bison@001",
    0.2,
    256,
    0.8,
    40,
    "us-central1"
)
```

# Yanıt

Yanıt doğru:

I am powered by PaLM 2, which stands for
Pathways Language Model 2. PaLM 2 was
trained by a team of engineers and
scientists at Google AI. PaLM 2 can summarize texts efficiently.

Türkçe Çevirisi:
Ben Pathways Language Model 2 anlamına gelen PaLM 2 tarafından destekleniyorum. PaLM 2, Google AI'deki bir mühendis ve bilim insanı ekibi tarafından eğitildi. PaLM 2, metinleri verimli bir şekilde özetleyebilir.

# Kod Açıklaması

1. `from vertexai.preview.language_models import ChatModel, InputOutputTextPair`: Vertex AI kütüphanesinden `ChatModel` ve `InputOutputTextPair` sınıflarını içe aktarır.
2. `def predict_large_language_model_sample(...):`: `predict_large_language_model_sample` fonksiyonunu tanımlar.
3. `vertexai.init(project=project_id, location=location)`: Vertex AI kütüphanesini belirtilen proje ve lokasyon ile başlatır.
4. `chat_model = ChatModel.from_pretrained(model_name)`: Önceden eğitilmiş `model_name` adlı modeli kullanarak bir `ChatModel` örneği oluşturur.
5. `parameters = {...}`: Model parametrelerini bir sözlük olarak tanımlar.
6. `chat = chat_model.start_chat(examples=[])`: Boş bir örnek listesi ile sohbeti başlatır.
7. `response = chat.send_message(...):`: Belirtilen mesajı ve parametreleri kullanarak sohbete bir mesaj gönderir.
8. `wrapped_text = textwrap.fill(response.text, width=40)`: Yanıt metnini 40 karakter genişliğinde kaydırır.
9. `print(wrapped_text)`: Kaydırılmış metni yazdırır.

Bu kod, PaLM 2 modelini kullanarak bir sohbet başlatır ve modele bir soru sorar. Yanıtı alır ve biçimlendirerek yazdırır.

---

