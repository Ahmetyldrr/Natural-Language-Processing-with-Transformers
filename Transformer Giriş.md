
# 📘 Chapter 1 – Hello Transformers (Ayrıntılı Açıklama + Kod + Kaynak)

Bu bölüm, Transformer mimarisinin ortaya çıkışını, neden önemli olduğunu, önceki yöntemlere göre avantajlarını ve temel yapı taşlarını detaylı bir şekilde ele almaktadır. Aynı zamanda Hugging Face ekosistemi ile bu teknolojileri nasıl kolayca uygulayabileceğimizi gösterir.

---

## 1. Transformer’ın Ortaya Çıkışı

2017 yılında Google araştırmacıları tarafından yayımlanan “Attention Is All You Need” adlı makale, RNN (Recurrent Neural Network) tabanlı sıralı veri modellemeye karşı büyük bir alternatif sundu.

### ✔️ Neden önemli?
- Eğitim süresi daha kısa
- Paralelleştirilebilir
- Uzun bağlamları daha iyi işler

### 🧠 Referanslar:
- https://arxiv.org/abs/1706.03762
- https://jalammar.github.io/illustrated-transformer/
- https://sebastianruder.com/the-transformer-family/

---

## 2. ULMFiT ve Transfer Öğrenmenin Gücü

ULMFiT, LSTM temelli bir model ile transfer öğrenmeyi NLP'ye taşıdı. Bu, Transformer gibi modellerin daha az veriyle çok şey öğrenebilmesinin yolunu açtı.

### 🧠 Kaynak:
- https://arxiv.org/abs/1801.06146
- https://docs.fast.ai/text.learner.html

---

## 3. GPT ve BERT'in Doğuşu

- **GPT:** Sadece decoder katmanı ile çalışır. Language modeling görevine odaklanır.
- **BERT:** Sadece encoder katmanı ile çalışır. Masked Language Modeling kullanır.

### 🧪 Basit Örnek:
```python
from transformers import pipeline
generator = pipeline("text-generation", model="gpt2")
print(generator("Transformers are", max_length=20))
```

---

## 4. Encoder-Decoder Yapısı

Encoder girişi temsile çevirir, decoder bu temsilden çıktı üretir.

### 🧠 Okuma:
- https://machinelearningmastery.com/encoder-decoder-attention-sequence-to-sequence-prediction-keras/
- https://colah.github.io/posts/2015-08-Understanding-LSTMs/

---

## 5. Attention Mekanizması

Attention, decoder’ın her giriş token’ına farklı ağırlık vermesini sağlar. Bu sayede daha iyi çeviri ve özetleme yapılır.

### 🧠 Kaynaklar:
- https://arxiv.org/abs/1409.0473
- https://jalammar.github.io/visualizing-neural-machine-translation-mechanics-of-seq2seq-models-with-attention/

---

## 6. Transformer Mimarisi

Transformer mimarisi, katmanlı self-attention ve feedforward yapılarından oluşur. Encoder ve decoder blokları ayrı ayrı attention katmanları içerir.

```python
from transformers import AutoTokenizer, AutoModel
tokenizer = AutoTokenizer.from_pretrained("bert-base-uncased")
model = AutoModel.from_pretrained("bert-base-uncased")
```

---

## 7. Hugging Face Transformers Kütüphanesi

Bu kütüphane, model yükleme, ön işleme, eğitim ve ince ayar gibi işleri büyük ölçüde kolaylaştırır.

### 📦 Kurulum:
```bash
pip install transformers
```

### 👇 Text Classification Pipeline:
```python
from transformers import pipeline
classifier = pipeline("text-classification")
print(classifier("This product is awesome!"))
```

---

## 8. Uygulama Örnekleri

### ✅ Named Entity Recognition (NER)
```python
ner = pipeline("ner", aggregation_strategy="simple")
ner("Barack Obama was born in Hawaii.")
```

### ✅ Soru Cevaplama
```python
qa = pipeline("question-answering")
qa(question="Who founded Apple?", context="Apple was founded by Steve Jobs and Steve Wozniak.")
```

### ✅ Özetleme (Summarization)
```python
summarizer = pipeline("summarization")
summarizer("Transformers are the backbone of modern NLP.")
```

### ✅ Çeviri (Translation)
```python
translator = pipeline("translation_en_to_de", model="Helsinki-NLP/opus-mt-en-de")
translator("Hello, how are you?")
```

---

## 9. Hugging Face Ekosistemi

### 🚀 Ana Bileşenler:
- **Transformers:** Modellerin kalbi
- **Tokenizers:** Hızlı tokenizasyon
- **Datasets:** Büyük veri kümeleri
- **Accelerate:** Eğitim kolaylaştırıcı
- **Hub:** Modellerin ve veri kümelerinin merkezi

### 🔗 Bağlantılar:
- https://huggingface.co/models
- https://huggingface.co/datasets
- https://huggingface.co/docs/transformers/index

---

## 10. Transformer’ların Zorlukları

- 🔁 Uzun dokümanlarda self-attention maliyetlidir
- 🔍 Açıklanabilirlik problemi
- ⚖️ Önyargı (bias) riski
- 🌍 Düşük kaynaklı diller için model eksikliği

---

## 🔚 Sonuç ve Sonraki Adımlar

Transformer mimarisi, doğal dil işleme alanında ezber bozdu. Hugging Face ekosistemi sayesinde bu teknolojiler artık herkes için ulaşılabilir. Bu bölümde teoriden pratiğe geçen temel konuları işledik.

> 🔜 Chapter 2’de metin sınıflandırmayı derinlemesine işleyeceğiz!

