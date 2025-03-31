
# 📚 Bölüm 1 – Transformer'lara Merhaba (Geliştirilmiş Versiyon)

## 1. Transformer’ın Doğuşu

2017 yılında Google tarafından yayımlanan “Attention Is All You Need” makalesiyle, sıralı modellerin yerini paralel çalışan Transformer mimarisi aldı. Bu mimari, NLP'de devrim yarattı.

### 🧠 Özellikler:
- RNN yerine tamamen paralel yapı
- Self-attention ile bağlam öğrenme
- Uzun dizilerde daha etkin performans

### 🔗 Kaynaklar:
- [Makale – Attention Is All You Need (arXiv)](https://arxiv.org/abs/1706.03762)
- [Jay Alammar – Illustrated Transformer](https://jalammar.github.io/illustrated-transformer/)
- [Türkçe: Transformer Mimarisi Nedir?](https://blog.openzeka.com/ai/transformer-modeli-nedir/)
- [Sebastian Ruder – Transformer Family](https://sebastianruder.com/the-transformer-family/)

### 🖼️ Görseller:
![Transformer Timeline](https://jalammar.github.io/images/t/transformers-timeline.png)

---

## 2. GPT ve BERT’in Ortaya Çıkışı

GPT ve BERT, Transformer yapısının farklı bölümlerine (decoder ve encoder) odaklanan iki model ailesidir.

| Model | Katman | Yön | Eğitim | Görev |
|-------|--------|-----|--------|-------|
| GPT   | Decoder | Tek yönlü | Language Modeling | Metin üretimi |
| BERT  | Encoder | Çift yönlü | Masked LM | Anlama ve sınıflandırma |

### 🔗 Kaynaklar:
- [GPT Paper (OpenAI)](https://openai.com/research/language-unsupervised)
- [BERT Paper](https://arxiv.org/abs/1810.04805)
- [Blog: BERT vs GPT](https://towardsdatascience.com/bert-vs-gpt-comparing-their-strengths-634f5b40e49e)
- [Türkçe: Transformer Mimarisine Giriş](https://medium.com/@selencodes/transformer-mimarisi-8b8da595a581)

### 🖼️ Görseller:
![BERT vs GPT](https://jalammar.github.io/images/gpt2/gpt2-architecture.png)

---

## 3. Encoder-Decoder Framework

Encoder girişi temsile çevirir, decoder bu temsilden çıktı üretir. Makine çevirisi gibi görevlerde kullanılır.

### 🔗 Kaynaklar:
- [Sequence to Sequence Models – Colah’s Blog](https://colah.github.io/posts/2015-08-Understanding-LSTMs/)
- [Encoder-Decoder w/ Attention](https://machinelearningmastery.com/encoder-decoder-attention-sequence-to-sequence-prediction-keras/)
- [Türkçe: Seq2Seq Nedir?](https://www.veribilimiokulu.com/seq2seq-ve-attention-mekanizmasi/)

### 🖼️ Görseller:
![Encoder Decoder Yapısı](https://jalammar.github.io/images/seq2seq_2.png)

---

## 4. Attention Mekanizması

Attention, modelin her kelimeye farklı dikkat vererek bağlamsal karar vermesini sağlar. Bu yapı hizalama (alignment) için de kullanılır.

### 🔗 Kaynaklar:
- [Bahdanau Attention (2014)](https://arxiv.org/abs/1409.0473)
- [Jay Alammar: Visual Attention](https://jalammar.github.io/visualizing-neural-machine-translation-mechanics-of-seq2seq-models-with-attention/)
- [Türkçe: Attention Nedir?](https://medium.com/@i_konak/transformer-mimarisi-türkçe-anlatım-part-2-self-attention-ab5e5eec32f)

### 🖼️ Görseller:
![Attention](https://jalammar.github.io/images/transformer/transformer-self-attention.png)

---

## 5. Transformer Mimarisi

Transformer, çok katmanlı self-attention + FFNN bloklarından oluşur. Eğitim paralelleştirilebilir, uzun bağlamlarla çalışabilir.

### 🔗 Kaynaklar:
- [Google AI Blog](https://ai.googleblog.com/2017/08/transformer-novel-neural-network.html)
- [A Visual Guide to Transformers](https://e2eml.school/transformers.html)
- [Türkçe: Transformer Mimarisi – Kodlama Zekası](https://kodlamazekasi.com/transformer-mimarisi-ve-attention/)

### 🖼️ Görseller:
![Transformer Architecture](https://jalammar.github.io/images/transformer/transformer.png)

---

## 6. Transfer Learning in NLP

ULMFiT ve BERT gibi modeller, büyük veriyle ön eğitimden geçirilip hedef göreve özel yeniden eğitilir (fine-tuning).

### 🔗 Kaynaklar:
- [ULMFiT Paper](https://arxiv.org/abs/1801.06146)
- [Transfer Learning in NLP](https://ruder.io/nlp-imagenet/)
- [Türkçe: Transfer Öğrenme Nedir?](https://medium.com/@merveaydinlar/transfer-%C3%B6%C4%9Frenme-nedir-nas%C4%B1l-%C3%A7al%C4%B1%C5%9F%C4%B1r-485ba3d9c1e8)

---

## 7. Hugging Face Transformers

Hugging Face, farklı görevler için hazır modeller sunar. PyTorch, TensorFlow desteklidir. Pipeline API çok pratiktir.

```python
from transformers import pipeline
classifier = pipeline("text-classification")
print(classifier("Transformers are awesome!"))
```

### 🔗 Kaynaklar:
- [Transformers GitHub](https://github.com/huggingface/transformers)
- [Hugging Face Docs](https://huggingface.co/docs/transformers/index)
- [Türkçe Hugging Face Eğitimi](https://github.com/firmai/machine-learning/blob/main/NLP/Huggingface-Turkce-Kaynaklar.md)

---

## 8. Uygulama Örnekleri ve Kodlar

### a. Sentiment Analysis
```python
pipeline("text-classification")("I love this!")
```
➡️ [Text Classification Repo](https://github.com/huggingface/transformers/tree/main/examples/pytorch/text-classification)

### b. Named Entity Recognition
```python
pipeline("ner", aggregation_strategy="simple")("Barack Obama was born in Hawaii.")
```
➡️ [NER Example](https://github.com/huggingface/transformers/tree/main/examples/pytorch/token-classification)

### c. Question Answering
```python
pipeline("question-answering")(
  question="Who founded Apple?", 
  context="Apple was founded by Steve Jobs and Steve Wozniak."
)
```
➡️ [QA Repo](https://github.com/huggingface/transformers/tree/main/examples/pytorch/question-answering)

---

## 9. Hugging Face Ekosistemi

- 🤖 Transformers
- ✂️ Tokenizers
- 📚 Datasets
- ⚡ Accelerate
- ☁️ Hugging Face Hub

🔗 [Hugging Face Hub](https://huggingface.co/models)

---

## 10. Zorluklar

- 📉 Veri dengesizliği ve dil çeşitliliği
- 🧠 Açıklanabilirlik zorlukları
- 💰 Eğitim maliyetleri
- ⚖️ Önyargılar (bias) ve etik sorunlar

---

## 11. Özet

Bu bölümde:
- Transformer mimarisi ve avantajları
- GPT ve BERT'in farkları
- Hugging Face ile uygulamalı NLP
- Kodlar, görseller ve Türkçe kaynaklarla destekli kavramsal anlatım
öğrenildi.

➡️ Sonraki adım: Kendi veri setinle model fine-tune etmek!

