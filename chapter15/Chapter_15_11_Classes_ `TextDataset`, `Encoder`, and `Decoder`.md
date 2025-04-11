# Metin Veri Seti ve Model Bileşenleri

TextDataset: Veri setini saran PyTorch veri seti sınıfı. 
Encoder: Bir gömme katmanı, çok başlı kendi kendine dikkat mekanizması, ileri beslemeli sinir ağı, katman normalizasyonu ve dropout içeren bir Encoder modülü tanımlar. 
Decoder: Encoder'a benzer, ancak ek bir çıktı doğrusal katmanı içeren bir Decoder modülü tanımlar.

Python kodu bulunmamaktadır, sadece ingilizce paragrafın türkçeye birebir çevirisi yapılmıştır.

Eğer ilgili PyTorch kodlarını açıklamak isterseniz, lütfen ilgili kodu bana veriniz, satır satır açıklama yapabilirim. Örneğin Encoder ve Decoder modüllerinin PyTorch implementasyonu aşağıdaki gibi olabilir:

```python
import torch
import torch.nn as nn
import torch.nn.functional as F

# Encoder Modülü
class Encoder(nn.Module):
    def __init__(self, vocab_size, embedding_dim, hidden_dim, output_dim, n_heads, dropout):
        super(Encoder, self).__init__()
        self.embedding = nn.Embedding(vocab_size, embedding_dim)
        self.self_attn = nn.MultiHeadAttention(n_heads, hidden_dim, dropout=dropout)
        self.feed_forward = nn.Linear(hidden_dim, hidden_dim)
        self.layer_norm = nn.LayerNorm(hidden_dim)
        self.dropout = nn.Dropout(dropout)

    def forward(self, x):
        x = self.embedding(x)
        x, _ = self.self_attn(x, x)
        x = self.feed_forward(x)
        x = self.layer_norm(x)
        x = self.dropout(x)
        return x

# Decoder Modülü
class Decoder(nn.Module):
    def __init__(self, vocab_size, embedding_dim, hidden_dim, output_dim, n_heads, dropout):
        super(Decoder, self).__init__()
        self.embedding = nn.Embedding(vocab_size, embedding_dim)
        self.self_attn = nn.MultiHeadAttention(n_heads, hidden_dim, dropout=dropout)
        self.feed_forward = nn.Linear(hidden_dim, hidden_dim)
        self.layer_norm = nn.LayerNorm(hidden_dim)
        self.dropout = nn.Dropout(dropout)
        self.output_linear = nn.Linear(hidden_dim, output_dim)

    def forward(self, x):
        x = self.embedding(x)
        x, _ = self.self_attn(x, x)
        x = self.feed_forward(x)
        x = self.layer_norm(x)
        x = self.dropout(x)
        x = self.output_linear(x)
        return x

# TextDataset Sınıfı
class TextDataset(torch.utils.data.Dataset):
    def __init__(self, texts, labels):
        self.texts = texts
        self.labels = labels

    def __getitem__(self, idx):
        text = self.texts[idx]
        label = self.labels[idx]
        return {
            'text': text,
            'label': label
        }

    def __len__(self):
        return len(self.texts)
```

Bu kodları satır satır açıklayabilirim:

# Encoder Modülü
## Tanımlama
```python
class Encoder(nn.Module):
```
Encoder sınıfını nn.Module'den türeterek tanımlıyoruz.

## Başlatma
```python
def __init__(self, vocab_size, embedding_dim, hidden_dim, output_dim, n_heads, dropout):
```
Encoder sınıfının başlatma metodunu tanımlıyoruz. Burada vocab_size: kelime haznesi boyutu, embedding_dim: gömme boyutu, hidden_dim: gizli durum boyutu, output_dim: çıktı boyutu, n_heads: çok başlı dikkat mekanizması baş sayısı, dropout: dropout oranı.

```python
super(Encoder, self).__init__()
```
Üst sınıfın (nn.Module) başlatma metodunu çağırıyoruz.

```python
self.embedding = nn.Embedding(vocab_size, embedding_dim)
```
Gömme katmanını tanımlıyoruz.

```python
self.self_attn = nn.MultiHeadAttention(n_heads, hidden_dim, dropout=dropout)
```
Çok başlı kendi kendine dikkat mekanizması katmanını tanımlıyoruz.

```python
self.feed_forward = nn.Linear(hidden_dim, hidden_dim)
```
İleri beslemeli sinir ağı katmanını tanımlıyoruz.

```python
self.layer_norm = nn.LayerNorm(hidden_dim)
```
Katman normalizasyonu katmanını tanımlıyoruz.

```python
self.dropout = nn.Dropout(dropout)
```
Dropout katmanını tanımlıyoruz.

## İleri Besleme
```python
def forward(self, x):
```
Encoder'ın ileri besleme metodunu tanımlıyoruz.

```python
x = self.embedding(x)
```
Girdiyi gömme katmanından geçiriyoruz.

```python
x, _ = self.self_attn(x, x)
```
Gömülü girdiyi kendi kendine dikkat mekanizması katmanından geçiriyoruz.

```python
x = self.feed_forward(x)
```
Dikkat mekanizması çıktısını ileri beslemeli sinir ağından geçiriyoruz.

```python
x = self.layer_norm(x)
```
İleri beslemeli sinir ağı çıktısını katman normalizasyonu katmanından geçiriyoruz.

```python
x = self.dropout(x)
```
Normalizasyon çıktısını dropout katmanından geçiriyoruz.

```python
return x
```
Encoder çıktısını döndürüyoruz.

Decoder ve TextDataset sınıflarının açıklamaları da benzer şekilde yapılabilir.

---

