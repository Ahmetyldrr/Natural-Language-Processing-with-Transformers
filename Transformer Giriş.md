
# 📚 Chapter 1 – Hello Transformers (Detaylı Açıklamalar ve Kodlarla)

## 1. Transformer’ın Doğuşu
2017’de Google’ın yayımladığı “Attention Is All You Need” makalesiyle Transformer mimarisi tanıtıldı. Bu yapı RNN’lere göre çok daha hızlı ve paralel çalışabiliyor.

**Avantajlar:**
- Paralel hesaplama
- Daha uzun bağlam bilgisi
- Daha hızlı eğitim

![Transformer Timeline](https://jalammar.github.io/images/t/transformers-timeline.png)  
*Transformer modellerinin gelişim süreci*

---

## 2. GPT ve BERT’in Ortaya Çıkışı

| Model | Mimarisi | Yönlülük | Eğitim Türü |
|-------|----------|----------|--------------|
| GPT   | Decoder | Tek yönlü | Language Modeling |
| BERT  | Encoder | Çift yönlü | Masked Language Modeling |

```python
from transformers import pipeline
generator = pipeline("text-generation", model="gpt2")
print(generator("Transformers are", max_length=20))
```

---

## 3. Encoder-Decoder Framework

Makine çevirisi gibi görevlerde kullanılır. Encoder giriş metnini sayısal forma çevirir, decoder çıktıyı üretir.

```python
from transformers import MarianMTModel, MarianTokenizer

model_name = "Helsinki-NLP/opus-mt-en-de"
tokenizer = MarianTokenizer.from_pretrained(model_name)
model = MarianMTModel.from_pretrained(model_name)

inputs = tokenizer("Hello world", return_tensors="pt")
translated = model.generate(**inputs)
print(tokenizer.decode(translated[0], skip_special_tokens=True))
```

![Encoder Decoder](https://jalammar.github.io/images/seq2seq_2.png)

---

## 4. Attention Mekanizması

Attention, modelin her kelimeye farklı odaklanmasını sağlar.

![Attention](https://jalammar.github.io/images/transformer/transformer-self-attention.png)

```python
# Bu görseldeki yapı transformer mimarisinin temelidir
```

---

## 5. Transformer Mimarisi

Transformer, self-attention + feed-forward ağlardan oluşur. Katman katman işlemler yapılır.

![Transformer Architecture](https://jalammar.github.io/images/transformer/transformer.png)

---

## 6. Transfer Learning in NLP

Büyük veri ile ön eğitim yapıldıktan sonra küçük görev verileriyle ince ayar yapılır (fine-tuning).

```python
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("distilbert-base-uncased")
tokenizer = AutoTokenizer.from_pretrained("distilbert-base-uncased")
```

---

## 7. Hugging Face Transformers Kütüphanesi

```python
from transformers import pipeline
classifier = pipeline("text-classification")
print(classifier("Transformers are amazing!"))
```

---

## 8. Uygulama Örnekleri

### 🧠 Sentiment Analysis
```python
classifier("I hate waiting for packages.")
```

### 🔍 Named Entity Recognition
```python
ner = pipeline("ner", aggregation_strategy="simple")
ner("Elon Musk founded SpaceX in California.")
```

### ❓ Question Answering
```python
qa = pipeline("question-answering")
qa(question="Who founded Apple?", context="Apple was founded by Steve Jobs and Steve Wozniak.")
```

### ✂️ Summarization
```python
summarizer = pipeline("summarization")
summarizer("Transformers are powerful NLP models. They outperform RNNs in many tasks.")
```

---

## 9. Hugging Face Ekosistemi

- 🤖 **Transformers**: modeller
- ✂️ **Tokenizers**: hızlı parçalama
- 🧺 **Datasets**: veri setleri
- 🚀 **Accelerate**: eğitim hızlandırma
- ☁️ **Hub**: model havuzu

---

## 10. Zorluklar

- İngilizce dışı dillerde veri sıkıntısı
- Uzun dokümanlarda performans kaybı
- Model iç yapısının açıklanamaması
- Önyargı (bias) taşıma riski

---

## 11. Bölüm Özeti

Transformer mimarisi NLP’de devrim yaratmıştır. GPT ve BERT ile başlayan bu çağ, Hugging Face sayesinde pratik olarak erişilebilir hale gelmiştir.

---

📌 *Not: Görseller [Jay Alammar](https://jalammar.github.io/illustrated-transformer/) tarafından hazırlanmıştır.*
