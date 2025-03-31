
# 📘 Chapter 1 – Hello Transformers (Genişletilmiş Açıklama + Kod + Kaynak)

Bu bölümde, Transformer mimarisinin tarihsel gelişimi, neden devrimsel olduğu, öncüllerinden farkları, uygulama örnekleri ve Hugging Face ekosistemi ile nasıl kolayca çalışabileceğimiz detaylı olarak ele alınmıştır.

---

## 1. Transformer’ın Ortaya Çıkışı

2017 yılında Google tarafından yayımlanan “Attention Is All You Need” adlı makale, RNN ve LSTM tabanlı sıralı modellemelere alternatif olarak sadece attention mekanizmasına dayalı bir yapı sundu.

### ✔️ Neden önemli?
- Eğitim süresi daha kısa, daha ucuz GPU maliyeti
- Zaman serilerine göre paralel işlem yapabilir
- Uzun bağlamlarda bilgi kaybı daha az

### 🧠 Referanslar:
- [Makale](https://arxiv.org/abs/1706.03762)
- [Görselli anlatım – Jay Alammar](https://jalammar.github.io/illustrated-transformer/)
- [Transformer Ailesi – Ruder](https://sebastianruder.com/the-transformer-family/)

---

## 2. ULMFiT ve Transfer Öğrenme

ULMFiT, LSTM üzerine kurulu olmasına rağmen, geniş çaplı bir gözetimsiz eğitim sonrası, küçük etiketli veri setlerinde bile çok başarılı sonuçlar elde etmeyi sağlamıştır.

### 🧠 Kaynaklar:
- [Makale](https://arxiv.org/abs/1801.06146)
- [FastAI Belgeleri](https://docs.fast.ai/text.learner.html)

Bu yöntem, Transformer tabanlı modellerin önünü açtı çünkü aynı "önce büyük veriyle eğit, sonra uyum sağla" mantığı GPT ve BERT ile kullanılacaktır.

---

## 3. GPT ve BERT’in Doğuşu

- **GPT (Generative Pretrained Transformer):** Yalnızca decoder kısmı kullanılır. Dil modeli olarak eğitim alır.
- **BERT (Bidirectional Encoder Representations from Transformers):** Yalnızca encoder kısmı kullanılır. Cümle içindeki rastgele maskelenmiş kelimeleri tahmin etmeye çalışır.

### 🧪 GPT2 ile Metin Üretimi
```python
from transformers import pipeline
generator = pipeline("text-generation", model="gpt2")
print(generator("Transformers are", max_length=20))
```

---

## 4. Encoder-Decoder Yapısı

Bu yapı, makine çevirisi gibi "girdi-seviyesi dizi → çıktı-seviyesi dizi" işlemleri için uygundur.

- Encoder, tüm girdiyi sabit boyutlu bir vektöre kodlar.
- Decoder, bu vektörden anlam çıkararak çıktı üretir.

### 🧠 Kaynaklar:
- [Sequence-to-Sequence Yapılar](https://machinelearningmastery.com/encoder-decoder-attention-sequence-to-sequence-prediction-keras/)
- [Colah’s LSTM Anlatımı](https://colah.github.io/posts/2015-08-Understanding-LSTMs/)

---

## 5. Attention Mekanizması

Attention, modelin farklı giriş öğelerine farklı dikkat vermesini sağlar. Bu, çeviri gibi eşleşme (alignment) gereken görevlerde büyük avantaj sağlar.

### 🧠 Kaynaklar:
- [Bahdanau Attention](https://arxiv.org/abs/1409.0473)
- [Jay Alammar Görselleştirme](https://jalammar.github.io/visualizing-neural-machine-translation-mechanics-of-seq2seq-models-with-attention/)

---

## 6. Transformer Mimarisi

Transformer, encoder ve decoder katmanlarının her birinde self-attention + feed-forward katmanlar bulundurur. Her katman kendi başına bir blok gibi çalışır.

### 🔧 Kod:
```python
from transformers import AutoTokenizer, AutoModel
tokenizer = AutoTokenizer.from_pretrained("bert-base-uncased")
model = AutoModel.from_pretrained("bert-base-uncased")
```

---

## 7. Hugging Face Transformers Kütüphanesi

Bu Python kütüphanesi, önceden eğitilmiş modellerle çalışma ve kendi verinizle model eğitme işlemlerini çok kolay hale getirir.

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

### 🚀 Bileşenler:
- **Transformers:** Model eğitimi ve uygulaması
- **Tokenizers:** Tokenize işlemi
- **Datasets:** Geniş veri kümesi koleksiyonu
- **Accelerate:** Multi-GPU ve kolay eğitim arayüzü
- **Hub:** Hazır modellerin merkezi

### 🔗 Bağlantılar:
- https://huggingface.co/models
- https://huggingface.co/datasets
- https://huggingface.co/docs/transformers/index

---

## 10. Transformer’ların Zorlukları

- 🔁 Uzun dokümanlarda performans problemi (quadratic attention)
- 🔍 Açıklanabilirlik hâlâ sınırlı
- ⚖️ Modelin eğitildiği verilerdeki önyargılar (bias) modele yansıyabilir
- 🌍 Düşük kaynaklı dillerde veri azlığı

---

## 🔚 Sonuç ve Sonraki Adımlar

Bu bölümde:
- Transformer mimarisinin nasıl ortaya çıktığı
- GPT ve BERT gibi modellerin nasıl bu yapıya dayandığı
- Hugging Face ile pratikte nasıl kullanılacağı
- Kod örnekleri ve kaynaklarla birlikte öğrenildi.

> 🚀 Devam etmek için: Chapter 2 – Text Classification!


