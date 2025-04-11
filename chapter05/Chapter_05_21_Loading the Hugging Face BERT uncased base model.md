# Önceden Eğitilmiş BERT Modelinin Yüklenmesi

Program şimdi önceden eğitilmiş BERT modelini yüklüyor: 
```python
model = BertForSequenceClassification.from_pretrained("bert-base-uncased", num_labels=2)
```
```python
model = nn.DataParallel(model)
```
```python
model.to(device)
```
Modeli tanımladık, paralel işlemeyi tanımladık ve modeli cihaza gönderdik. Bu önceden eğitilmiş model gerekirse daha fazla eğitilebilir. Her bir alt katmanın parametrelerini görselleştirmek için mimariyi ayrıntılı olarak incelemek ilginçtir, aşağıdaki alıntıda gösterildiği gibi:

```python
DataParallel(
  (module): BertForSequenceClassification(
    (bert): BertModel(
      (embeddings): BertEmbeddings(
        (word_embeddings): Embedding(30522, 768, padding_idx=0)
        (position_embeddings): Embedding(512, 768)
        (token_type_embeddings): Embedding(2, 768)
        (LayerNorm): LayerNorm((768,), eps=1e-12, elementwise_affine=True)
        (dropout): Dropout(p=0.1, inplace=False)
      )
      (encoder): BertEncoder(
        (layer): ModuleList(
          (0-11): 12 x BertLayer(
            (attention): BertAttention(
              (self): BertSelfAttention(
                (query): Linear(in_features=768, out_features=768, bias=True)
                (key): Linear(in_features=768, out_features=768, bias=True)
                (value): Linear(in_features=768, out_features=768, bias=True)
                (dropout): Dropout(p=0.1, inplace=False)
              )
              (output): BertSelfOutput(
                (dense): Linear(in_features=768, out_features=768, bias=True)
                (LayerNorm): LayerNorm((768,), eps=1e-12, elementwise_affine=True)
                (dropout): Dropout(p=0.1, inplace=False)
              )
            )
            (intermediate): BertIntermediate(
              (dense): Linear(in_features=768, out_features=3072, bias=True)
              (intermediate_act_fn): GELUActivation()
            )
            (output): BertOutput(
              (dense): Linear(in_features=3072, out_features=768, bias=True)
              (LayerNorm): LayerNorm((768,), eps=1e-12, elementwise_affine=True)
              (dropout): Dropout(p=0.1, inplace=False)
            )
          )
        )
      )
      (pooler): BertPooler(
        (dense): Linear(in_features=768, out_features=768, bias=True)
        (activation): Tanh()
      )
    )
    (dropout): Dropout(p=0.1, inplace=False)
    (classifier): Linear(in_features=768, out_features=2, bias=True)
  )
)
```

Şimdi optimizasyonun ana parametrelerine geçelim.

## Kod Açıklaması

1. `model = BertForSequenceClassification.from_pretrained("bert-base-uncased", num_labels=2)` 
   - Bu satır, önceden eğitilmiş "bert-base-uncased" modelini yükler ve `BertForSequenceClassification` sınıfı ile sequence classification görevi için yapılandırır. `num_labels=2` parametresi, sınıflandırma görevinin 2 sınıflı olduğunu belirtir.

2. `model = nn.DataParallel(model)`
   - Bu satır, modeli paralel işlemeye uygun hale getirir. Böylece model, birden fazla GPU üzerinde çalışabilir.

3. `model.to(device)`
   - Bu satır, modeli belirtilen cihaza (örneğin, GPU) gönderir.

## Model Mimarisi

Yukarıdaki kodda gösterilen model mimarisi, BERT modelinin detaylı yapısını gösterir. 
- `BertEmbeddings`: Giriş metninin embedding'lerini oluşturur.
  - `word_embeddings`: Kelime embedding'leri.
  - `position_embeddings`: Pozisyon embedding'leri.
  - `token_type_embeddings`: Token tipi embedding'leri.
- `BertEncoder`: Embedding'leri işler.
  - `BertLayer`: Her bir katmanda `BertAttention` ve `BertOutput` katmanları bulunur.
    - `BertAttention`: Self-attention mekanizması uygular.
    - `BertIntermediate` ve `BertOutput`: Feed-forward network (FFN) uygular.
- `BertPooler`: Havuzlama işlemi yapar.

Son olarak, `dropout` ve `classifier` katmanları sırasıyla dropout işlemini ve sınıflandırmayı gerçekleştirir.

---

