# 13. Bölüm: T5 ve ChatGPT ile Özetleme
13. Bölüm, özetleme görevlerinde bizi adım adım yönlendirdi. Soru-Cevap (QA), modelin bir metni anladığını görmek için başka bir yoldur. Soru sormak için chat-bison@001 modelini kullanacağız. Öncelikle gerekli modülleri içe aktarıyoruz: 
```python
import vertexai
from vertexai.preview.language_models import ChatModel, InputOutputTextPair
```
Ardından, projemizi ("aiex-57523") ve konumumuzu ("us-central1") başlatıyoruz. Proje ve konum adlarını kendi değerlerinizle değiştirdiğinizden emin olun. Bu örnekler için, çok güçlü bir PaLM 2 genel amaçlı Generative AI transformer olan chat-bison@001 modelini kullanacağız:
```python
vertexai.init(project="aiex-57523", location="us-central1")
chat_model = ChatModel.from_pretrained("chat-bison@001")
parameters = {"temperature": 0.2, "max_output_tokens": 256, "top_p": 0.8, "top_k": 40}
```
Parametreleri değiştirebilir ve isteğin bağlamını değiştirebilirsiniz. Şimdi isteğimizi yapabiliriz. Soru, Büyük Dil Modelleri'nin (LLM) mevcut metinleri kelimesi kelimesine tekrarladığında karşılaştıkları bir ezberleme sorunuyla ilgilidir:
```python
chat = chat_model.start_chat(
    context="""Gönderilen metin üzerinde bir soruyu cevaplayın""",
)
response = chat.send_message("""Aşağıdaki metne göre, Gemini mevcut metni tekrarlıyor mu? "Gemini, metin, kod, resim ve daha fazlasını anlayan ve oluşturan çok modlu bir LLM'dir. Büyük miktarda bilgi üzerinde akıl yürütmede, karmaşık problemleri çözmede ve ince ayar yoluyla çeşitli görevlere uyum sağlamada mükemmeldir.""" , **parameters)
```
Yanıt sarılır ve görüntülenir:
```python
wrapped_text = textwrap.fill(response.text, width=40)
print(wrapped_text)
```
Yanıt iyi niyetlidir:
```
Hayır, Gemini mevcut metni tekrarlamaz.
O, metin, kod, resim ve daha fazlasını
anlayabilen ve oluşturabilen çok modlu
bir LLM'dir. Büyük miktarda bilgi
üzerinde akıl yürütmede, karmaşık
problemleri çözmede ve ince ayar
aracılığıyla çeşitli görevlere uyum
sağlamada mükemmeldir.
```
Ayrıca, Gemini hakkında Gemini'ye API aracılığıyla soru sormak ve çıktıları PaLM 2 modeli ile karşılaştırmak için aşağıdaki hücreyi çalıştırabilirsiniz. Sonuç olarak, kalite ve maliyetleri dikkate alarak ihtiyaçlarınıza uygun modeli seçmek size kalmıştır. Metin sağlamadan da soru sorabiliriz.

---

