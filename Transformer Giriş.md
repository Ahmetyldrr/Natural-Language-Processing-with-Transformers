
# 📘 Chapter 1 – Hello Transformers (Derinlemesine Teknik Açıklamalar + Kod + Kaynak)

Bu belge, Transformer mimarisinin temel yapı taşlarını, dikkat mekanizmasını, encoder-decoder yapısını ve Hugging Face ekosistemini kapsamlı bir şekilde açıklamaktadır. Özellikle matematiksel ve yapısal bileşenlere odaklanılmıştır.

---

## 1. Transformer’ın Ortaya Çıkışı

Transformer modeli, RNN ve LSTM'in sıralı doğasından farklı olarak tüm girdiyi aynı anda işleyebilen self-attention mekanizmasına dayanır. Bu sayede paralel eğitim, daha iyi bağlam yakalama ve uzun dizilerle başa çıkma imkânı doğar.

📄 Makale: [Attention Is All You Need](https://arxiv.org/abs/1706.03762)

---

## 2. Encoder ve Matematiksel Temeli

Transformer mimarisinde **encoder**, giriş dizisini (örneğin bir cümle) sabit boyutta temsillere (embedding'ler) çevirir.

### ✨ Encoder'ın Bileşenleri:

1. **Token Embedding**: Her kelime için vektör temsili.
2. **Positional Encoding**: Kelime sırasını modele kazandıran sabit trigonometrik fonksiyonlar.
3. **Multi-Head Self-Attention**: Her kelimenin diğer tüm kelimelerle bağını hesaba katması.
4. **Feed Forward Network**: İki tam bağlantılı katmandan oluşur.

### 📐 Matematiksel Formülasyon:

#### a. Self-Attention:
Her kelime embedding'i `x` için 3 vektör oluşturulur:
- Query (Q), Key (K), Value (V)

Bu vektörler bir ağırlık matrisiyle çarpılır:
```
Q = XW^Q,    K = XW^K,    V = XW^V
```

Ardından benzerlik hesaplanır:
```
Attention(Q, K, V) = softmax(QKᵀ / √d_k) V
```
Burada `d_k`, boyut sayısıdır (ölçeklendirme için kullanılır).

#### b. Multi-Head Attention:
Aynı işlemi farklı parametrelerle `h` kez uygular:
```
MultiHead(Q, K, V) = Concat(head_1, ..., head_h) W^O
```

#### c. Feed-Forward Network:
İki katmanlı MLP:
```
FFN(x) = max(0, xW₁ + b₁)W₂ + b₂
```

#### d. Residual + Layer Norm:
Her katman şu şekilde paketlenir:
```
LayerNorm(x + Sublayer(x))
```

---

## 3. Decoder Nasıl Çalışır?

Decoder, encoder çıktısını kullanarak sırayla yeni kelimeler üretir.

Ek olarak:
- **Masked Self-Attention**: Model gelecekteki kelimelere bakamaz (dil üretimi için).
- Encoder-decoder attention katmanı bulunur.

---

## 4. Positional Encoding Detayı

Transformer dizideki sıralamayı doğal olarak anlamaz. Bu nedenle positional encoding (konum kodlaması) uygulanır:

```
PE(pos, 2i) = sin(pos / 10000^(2i/d_model))
PE(pos, 2i+1) = cos(pos / 10000^(2i/d_model))
```

Bu sayede model mutlak konum bilgisi edinir.

---

## 5. Hugging Face Transformers ile Uygulama

### Text Classification:
```python
from transformers import pipeline
classifier = pipeline("text-classification")
classifier("Transformers are amazing!")
```

### Soru-Cevap:
```python
qa = pipeline("question-answering")
qa(question="What is self-attention?", context="Self-attention allows a model to consider other words in the input.")
```

### NER:
```python
ner = pipeline("ner", aggregation_strategy="simple")
ner("Elon Musk founded SpaceX in California.")
```

---

## 6. Eğitim Zorlukları

- **Quadratic Attention**: Hesaplama karmaşıklığı O(n²), uzun dizilerde pahalıdır.
- **Önyargı**: Modelin eğitildiği veri kümesindeki önyargılar çıktılara yansıyabilir.
- **Yorumlanabilirlik**: Attention haritaları sınırlı içgörü sağlar.

---

## 7. Gelişmiş Versiyonlar

- **BERT** (sadece encoder): Masked language modeling
- **GPT** (sadece decoder): Causal language modeling
- **T5/UL2**: Encoder-decoder tabanlı, çok amaçlı modeller

---

## 8. Hugging Face Ekosistemi

- **Transformers**: Model eğitimi ve önceden eğitilmiş modeller
- **Datasets**: 1000+ hazır NLP veri kümesi
- **Tokenizers**: Hızlı ve özelleştirilebilir tokenizer’lar
- **Accelerate**: Kolay çoklu GPU/TPU eğitimi

🔗 https://huggingface.co/docs

---

## 🔚 Sonuç

Transformer, NLP’de devrim yaratmıştır. Hem teorik hem uygulamalı olarak bu bölümde:
- Mimarinin temelleri
- Encoder-decoder yapısı
- Attention matematiği
- Hugging Face ile uygulama örnekleri

detaylı olarak sunulmuştur.

