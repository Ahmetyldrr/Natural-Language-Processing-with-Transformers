
## 📚 Chapter 1 – Hello Transformers: Detaylı Notlar ve Kodlar

### 1. Transformer’ın Doğuşu
- 2017 yılında Google tarafından yayınlanan "Attention Is All You Need" makalesiyle transformer mimarisi tanıtıldı.
- Bu model, RNN (Recurrent Neural Networks) yapısından farklı olarak tamamen attention mekanizmasına dayalıydı.
- RNN'lerin sıralı işleme zorunluluğuna karşılık, transformer paralel çalışabilir ve daha hızlıdır.

### 2. GPT ve BERT’in Ortaya Çıkışı
- GPT (Generative Pretrained Transformer): Decoder tarafını kullanır, "language modeling" yapar.
- BERT (Bidirectional Encoder Representations from Transformers): Encoder yapısını kullanır, "masked language modeling" uygular.
- Her ikisi de transfer learning kullanarak farklı NLP görevlerinde state-of-the-art sonuçlar verdi.

### 3. Encoder-Decoder Framework
- Encoder, giriş metnini bir gizli temsil (hidden state) haline getirir.
- Decoder bu temsili kullanarak çıktı metnini oluşturur.
- Örnek kod (RNN yerine transformer olmasını temsilen):
```python
from transformers import MarianMTModel, MarianTokenizer
model_name = "Helsinki-NLP/opus-mt-en-de"
tokenizer = MarianTokenizer.from_pretrained(model_name)
model = MarianMTModel.from_pretrained(model_name)
```

### 4. Attention Mechanism
- Decoder, encoder’ın her adımdaki gizli durumuna erişerek daha doğru çeviriler yapabilir.
- Attention, her encoder çıktısına ağırlık vererek hangi kelimenin daha önemli olduğunu belirler.
- Visualization çok kullanılır: "alignment heatmaps"

### 5. Transformer Mimarisi
- RNN yok, tamamen self-attention katmanları var.
- Encoder ve decoder kendi içinde attention uygular.
- Paralel çalışabilir, bu da eğitimi çok daha hızlı hale getirir.

### 6. Transfer Learning in NLP
- ULMFiT: İlk olarak büyük corpus ile pretraining, sonra hedef domain'e (IMDb vs.) adaptasyon.
- Son adımda ince ayar (fine-tuning) ile hedef göreve uyarlama.
- Örnek:
```python
from transformers import AutoModelForSequenceClassification, AutoTokenizer
model = AutoModelForSequenceClassification.from_pretrained("distilbert-base-uncased")
tokenizer = AutoTokenizer.from_pretrained("distilbert-base-uncased")
```

### 7. Hugging Face Transformers Kütüphanesi
- PyTorch, TensorFlow ve JAX uyumlu
- Pipeline API ile kullanım çok kolay
- Model, tokenizer ve pipeline tek satırda çalıştırılabilir
- Örnek:
```python
from transformers import pipeline
classifier = pipeline("text-classification")
```

### 8. Uygulama Örnekleri (Pipeline API ile)

#### ✔️ Text Classification
```python
classifier = pipeline("text-classification")
print(classifier("I love Hugging Face Transformers!"))
```

#### ✔️ Named Entity Recognition (NER)
```python
ner = pipeline("ner", aggregation_strategy="simple")
print(ner("Barack Obama was born in Hawaii."))
```

#### ✔️ Question Answering
```python
qa = pipeline("question-answering")
qa(question="Who founded Apple?", context="Apple was founded by Steve Jobs and Steve Wozniak.")
```

#### ✔️ Summarization
```python
summarizer = pipeline("summarization")
text = "Transformers allow parallel computation. They work better than RNNs in many NLP tasks."
summarizer(text)
```

#### ✔️ Translation
```python
translator = pipeline("translation_en_to_de", model="Helsinki-NLP/opus-mt-en-de")
print(translator("Hello, how are you?"))
```

#### ✔️ Text Generation
```python
generator = pipeline("text-generation")
prompt = "Once upon a time"
print(generator(prompt, max_length=50))
```

### 9. Hugging Face Ekosistemi
- **Transformers**: modeller
- **Tokenizers**: hızlı metin bölüleyici
- **Datasets**: veri yükleme, önişleme
- **Accelerate**: GPU/çoklu cihaz eğitimi
- **Hub**: 20.000+ model/dataset merkezi

### 10. Transformer Kullanımındaki Zorluklar
- İngilizce dışı dillerde veri/model azlığı
- Uzun belgelerde self-attention maliyeti
- Modelin neden belirli sonuçlar verdiği anlaşılamaz (black box)
- İnternetteki verilerden gelen bias etkisi

### 11. Bölüm Özeti ve Gelecek Aşama
- Transformer mimarisi, attention mekanizması, encoder-decoder yapısı tanındı
- Hugging Face ile pratik yapıldı
- Bir sonraki adım: **kendi verinle model fine-tune etmek (Text Classification)**
