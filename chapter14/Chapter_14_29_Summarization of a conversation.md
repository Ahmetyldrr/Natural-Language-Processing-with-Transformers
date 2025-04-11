# Büyük Dil Modelleri (LLMs) ve Diyalog Özetleme

Büyük Dil Modelleri (LLMs) metinleri özetlemede iyidir. Peki ya diyaloglar? Bu istek bir diyalog içermektedir. Öncelikle modele ne istediğimizi söylüyoruz:

```python
import vertexai 
from vertexai.language_models import TextGenerationModel
```

*   Yukarıdaki kod, `vertexai` ve `vertexai.language_models` modüllerinden `TextGenerationModel` sınıfını içe aktarır.

```python
vertexai.init(project="aiex-57523", location="us-central1")
```

*   `vertexai.init()` fonksiyonu, Vertex AI projesini başlatır. Proje ID'si "aiex-57523" ve lokasyon "us-central1" olarak belirlenmiştir.

```python
parameters = {
    "temperature": 0.2, 
    "max_output_tokens": 256, 
    "top_p": 0.8, 
    "top_k": 40
}
```

*   Yukarıdaki kod, modelin tahmin yaparken kullanacağı parametreleri tanımlar.
    *   `temperature`: Modelin yaratıcılığını kontrol eder. Düşük değerler daha deterministik sonuçlar verir.
    *   `max_output_tokens`: Modelin üreteceği maksimum token sayısını belirler.
    *   `top_p`: Modelin olasılık dağılımından örnekleme yaparken dikkate alacağı kümülatif olasılık değerini belirler.
    *   `top_k`: Modelin olasılık dağılımından örnekleme yaparken dikkate alacağı en yüksek olasılıklı token sayısını belirler.

```python
model = TextGenerationModel.from_pretrained("text-bison@001")
```

*   `TextGenerationModel.from_pretrained()` fonksiyonu, önceden eğitilmiş "text-bison@001" modelini yükler.

```python
response = model.predict(
    """Summarize the following conversation between a service rep and a customer in a few sentences. Use only the information from the conversation. 
    Then we provide the conversation: 
    Service Rep: How may I assist you today? 
    Customer: I need to change the shipping address for an order. 
    Service Rep: Ok, I can help you with that if the order has not been fulfilled from our warehouse yet. But if it has already shipped, then you will need to contact the shipping provider. Do you have the order ID? 
    Customer: Yes, it\'s 88986367. 
    Service Rep: One minute please while I pull up your order information. 
    Customer: No problem 
    Service Rep: Ok, it looks like your order was shipped from our warehouse 2 days ago. It is now in the hands of the shipping provider, so you will need to contact them to update your delivery details. You can track your order with the shipping provider here: https://www.shippingprovider.com 
    Customer: Sigh, ok. 
    Service Rep: Is there anything else I can help you with today? 
    Customer: No, thanks.""", 
    **parameters
)
```

*   `model.predict()` fonksiyonu, modele bir diyalogu özetleme görevi verir. Diyalog, bir müşteri temsilcisi ile bir müşteri arasında gerçekleşen bir konuşmayı içerir.
*   `**parameters` ifadesi, daha önce tanımlanan parametreleri modele aktarır.

```python
# print(f"Response from Model: {response.text}")
wrapped_text = textwrap.fill(response.text, width=40)
print(wrapped_text)
```

*   Yukarıdaki kod, modelin cevabını alır ve `textwrap.fill()` fonksiyonu ile 40 karakter genişliğinde satırlara böler.
*   `print(wrapped_text)` ifadesi, biçimlendirilmiş cevabı yazdırır.

Modelin cevabı kabul edilebilir:

Müşteri, bir sipariş için kargo adresini değiştirmek istiyor. 
Müşteri temsilcisi, siparişin zaten gönderildiğini ve teslimat detaylarını güncellemek için kargo sağlayıcıyla iletişime geçmeleri gerektiğini bildirir. 
Müşteri memnun değildir ancak kargo sağlayıcıyla iletişime geçmeyi kabul eder.

Bu işlevselliği toplantılara, destek hattı diyaloglarına ve birçok türdeki değişimlere genişletebiliriz. Ayrıca gelişmiş duygu analizi yapabiliriz.

---

