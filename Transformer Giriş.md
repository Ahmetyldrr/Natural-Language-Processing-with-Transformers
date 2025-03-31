
# 📚 Chapter 1 – Hello Transformers (Genişletilmiş Anlatım + Kaynak Linkleri)

## 1. Transformer’ın Doğuşu

2017 yılında Google araştırmacıları tarafından yayımlanan “Attention Is All You Need” makalesiyle birlikte, RNN tabanlı sıralı modellemeler yerini paralel çalışan Transformer mimarisine bıraktı. Bu mimari, NLP'de devrim yarattı.

### 🧠 Temel Kavramlar:
- Paralel hesaplama yeteneği
- Self-Attention mekanizması ile bağlamsal öğrenme
- RNN'lerin sıralı bağımlılıklarının kaldırılması

### 🔗 Kaynaklar:
- [Original Paper – Attention Is All You Need (arXiv)](https://arxiv.org/abs/1706.03762)
- [Jay Alammar – Illustrated Transformer](https://jalammar.github.io/illustrated-transformer/)
- [Sebastian Ruder – The Transformer Family](https://sebastianruder.com/the-transformer-family/)

---

## 2. GPT ve BERT’in Ortaya Çıkışı

GPT ve BERT, Transformer mimarisinin iki farklı yönünü kullanarak NLP görevlerine odaklanır.

| Model | Kullanılan Katman | Eğitim Türü | Yönlülük |
|-------|-------------------|-------------|----------|
| GPT   | Decoder           | Language Modeling | Tek yönlü |
| BERT  | Encoder           | Masked Language Modeling | Çift yönlü |

### 🧪 Örnek Kod (GPT):
```python
from transformers import pipeline
generator = pipeline("text-generation", model="gpt2")
print(generator("Transformers are", max_length=20))
```

### 🔗 Kaynaklar:
- [BERT: Pre-training of Deep Bidirectional Transformers](https://arxiv.org/abs/1810.04805)
- [OpenAI GPT Paper](https://openai.com/research/language-unsupervised)
- [Blog: BERT vs GPT](https://towardsdatascience.com/bert-vs-gpt-comparing-their-strengths-634f5b40e49e)

---

## 3. Encoder-Decoder Framework

Encoder-Decoder mimarisi, çeviri gibi giriş-çıkış çiftleri olan görevlerde yaygındır. Encoder tüm girişi temsil eden bir vektöre çevirir, decoder bu vektörü kullanarak çıktı üretir.

### 🧪 Örnek Kod:
```python
from transformers import MarianMTModel, MarianTokenizer
model_name = "Helsinki-NLP/opus-mt-en-de"
tokenizer = MarianTokenizer.from_pretrained(model_name)
model = MarianMTModel.from_pretrained(model_name)

inputs = tokenizer("Hello world", return_tensors="pt")
translated = model.generate(**inputs)
print(tokenizer.decode(translated[0], skip_special_tokens=True))
```

### 🔗 Kaynaklar:
- [Sequence to Sequence Models (Colah Blog)](https://colah.github.io/posts/2015-08-Understanding-LSTMs/)
- [Encoder-Decoder in Machine Translation](https://machinelearningmastery.com/encoder-decoder-attention-sequence-to-sequence-prediction-keras/)

---

## 4. Attention Mekanizması

Attention, modelin her kelimeye farklı dikkat vermesini sağlar. Bu sayede bağlam bilgisini daha iyi yakalayabilir.

### 🔗 Kaynaklar:
- [Bahdanau Attention Paper](https://arxiv.org/abs/1409.0473)
- [The Illustrated Transformer (Jay Alammar)](https://jalammar.github.io/illustrated-transformer/)
- [Blog: Visualizing Attention](https://distill.pub/2016/augmented-rnns/)

---

## 5. Transformer Mimarisi

Transformer, çok katmanlı attention ve feed-forward ağlardan oluşur. Eğitim süresi kısalır, paralelleştirme yapılabilir.

### 🔗 Kaynaklar:
- [Google AI Blog on Transformer](https://ai.googleblog.com/2017/08/transformer-novel-neural-network.html)
- [Blog: A Visual Guide to Transformers](https://e2eml.school/transformers.html)

---

## 6. Transfer Learning in NLP

Transfer öğrenme sayesinde büyük veriyle eğitilmiş modeller, yeni görevlerde çok daha az veriyle başarılı olur. ULMFiT ve BERT bu stratejiyle eğitildi.

### 🧪 Hugging Face Fine-tuning:
```python
from transformers import AutoModelForSequenceClassification, AutoTokenizer
model = AutoModelForSequenceClassification.from_pretrained("distilbert-base-uncased")
tokenizer = AutoTokenizer.from_pretrained("distilbert-base-uncased")
```

### 🔗 Kaynaklar:
- [ULMFiT Paper](https://arxiv.org/abs/1801.06146)
- [Transfer Learning with Transformers](https://ruder.io/nlp-imagenet/)
- [Fast.ai ULMFiT Explanation](https://docs.fast.ai/text.learner.html)

---

## 7. Hugging Face Transformers Kütüphanesi

Hugging Face, model ve tokenizer yükleme, pipeline oluşturma gibi işleri kolaylaştırır.

### 🧪 Örnek:
```python
from transformers import pipeline
classifier = pipeline("text-classification")
print(classifier("Transformers are amazing!"))
```

### 🔗 Kaynaklar:
- [Transformers GitHub](https://github.com/huggingface/transformers)
- [Hugging Face Documentation](https://huggingface.co/docs/transformers/index)

---

## 8. Uygulama Örnekleri

### a. Sentiment Analysis
```python
pipeline("text-classification")("I love AI!")
```

### b. Named Entity Recognition
```python
pipeline("ner", aggregation_strategy="simple")("Barack Obama was born in Hawaii.")
```

### c. Question Answering
```python
pipeline("question-answering")(
  question="Who founded Apple?", 
  context="Apple was founded by Steve Jobs and Steve Wozniak."
)
```

### d. Summarization
```python
pipeline("summarization")("Transformers allow parallel computation and are powerful.")
```

### e. Translation
```python
pipeline("translation_en_to_de", model="Helsinki-NLP/opus-mt-en-de")("Hello, how are you?")
```

### f. Text Generation
```python
pipeline("text-generation", model="gpt2")("Once upon a time")
```

### 🔗 Örnek Projeler:
- [Text Classification Example](https://github.com/huggingface/transformers/tree/main/examples/pytorch/text-classification)
- [NER Example](https://github.com/huggingface/transformers/tree/main/examples/pytorch/token-classification)
- [Summarization Example](https://github.com/huggingface/transformers/tree/main/examples/pytorch/summarization)
- [Translation Example](https://github.com/huggingface/transformers/tree/main/examples/pytorch/translation)

---

## 9. Hugging Face Ekosistemi

- 🤖 Transformers: Modeller
- ✂️ Tokenizers: Metin parçalama
- 📚 Datasets: Veri kümesi
- ⚡ Accelerate: Eğitim hızlandırma
- ☁️ Hub: Model paylaşım platformu

🔗 [Hugging Face Hub](https://huggingface.co/models)

---

## 10. Zorluklar

- Dil çeşitliliği problemi (İngilizce dışı modeller az)
- Uzun metinlerde self-attention maliyeti yüksek
- Model kararları açıklanamıyor (black-box)
- İnternetten alınan verilerden gelen önyargı (bias)

---

## 11. Bölüm Özeti

Bu bölümde:
- Transformer mimarisi, encoder-decoder yapısı, attention, GPT ve BERT gibi modellerin doğuşu
- Hugging Face ile model kullanımı ve NLP görevleri
- Kod örnekleri ve uygulamalar
gibi temel yapı taşları öğrenildi.

🧭 Sonraki adım: Kendi veri kümenle model eğitmek ve optimize etmek.
