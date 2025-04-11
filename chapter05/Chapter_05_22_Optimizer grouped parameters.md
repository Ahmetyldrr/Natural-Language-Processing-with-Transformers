# Programın Model Parametreleri için Optimizasyonunu Başlatma

Program şimdi modelin parametreleri için optimizasyonu başlatacaktır. Bir modeli fine-tuning işlemi, önceden eğitilmiş model parametre değerlerinin (isimleri değil) başlatılmasıyla başlar. Optimizasyonun parametreleri arasında aşırı uyumu önlemek için bir ağırlık azaltma oranı bulunur ve bazı parametreler filtrelenir. Amaç, modelin parametrelerini eğitim döngüsü için hazırlamaktır.

Bu kod şu kaynaktan alınmıştır: https://github.com/huggingface/transformers/blob/5bfcd0485ece086ebcbed2d008813037968a9e58/examples/run_glue.py#L102

İsimlerinde belirtilen tokenleri içeren parametrelere ağırlık azaltma uygulanmaz. (Burada, BERT'nin 'gamma' veya 'beta' parametreleri yoktur, sadece 'bias' terimleri vardır)

```python
param_optimizer = list(model.named_parameters())
no_decay = ['bias', 'LayerNorm.weight']
```

### Parametreleri Filtreleme

*   'weight' parametreleri için ağırlık azaltma oranı 0.01 olarak belirlenir.
*   'bias' parametreleri için ağırlık azaltma oranı 0.0'dır.

```python
optimizer_grouped_parameters = [
    # 'bias', 'gamma', 'beta' içermeyen tüm parametreler için filtre uygula.
    {'params': [p for n, p in param_optimizer if not any(nd in n for nd in no_decay)], 'weight_decay_rate': 0.1},
    # Bu tokenleri içeren parametreler için filtre uygula.
    {'params': [p for n, p in param_optimizer if any(nd in n for nd in no_decay)], 'weight_decay_rate': 0.0}
]
```

`optimizer_grouped_parameters` yalnızca parametre değerlerini içerir, isimlerini değil.

### Parametrelerin İncelenmesi

`param_optimizer`'ün 3. katmanına bakıldığında, modelin tüm parametreleri ve isimleri `param_optimizer` içinde toplanmıştır. Bu fonksiyon bir iterator üretir. Iterator, tuple'lar içerir. Her bir tuple, bir parametrenin ismini ve genellikle PyTorch tensörleri olan parametreleri içerir.

Aşağıdaki kod, 3. katmanın parametrelerinin isimlerini (`n`) ve değerlerini (`p`) gösterir:

```python
layer_parameters = [p for n, p in model.named_parameters() if 'layer.3' in n]
```

Çıktının bir kısmı aşağıdaki gibidir:

```
'module.bert.embeddings.word_embeddings.weight', Parameter containing:
tensor([[-0.0102, -0.0615, -0.0265, ..., -0.0199, -0.0372, -0.0098],
        [-0.0117, -0.0600, -0.0323, ..., -0.0168, -0.0401, -0.0107],
        [-0.0198, -0.0627, -0.0326, ..., -0.0165, -0.0420, -0.0032],
        ...,
        [-0.0218, -0.0556, -0.0135, ..., -0.0043, -0.0151, -0.0249],
        [-0.0462, -0.0565, -0.0019, ..., 0.0157, -0.0139, -0.0095],
        [ 0.0015, -0.0821, -0.0160, ..., -0.0081, -0.0475, 0.0753]],
       device='cuda:0', requires_grad=True))
```

Ek bilgiler de görüntülenir. `cuda:0`, ilk CUDA etkin GPU'nun etkinleştirildiğini gösterir. `requires_grad=True`, gradyanların hesaplanacağını ve tensörlerin eğitim süreci sırasında güncelleneceğini belirtir. Model "öğreniyor".

### `no_decay` Listesinin İncelenmesi

```python
no_decay = ['bias', 'LayerNorm.weight']
```

Ağırlık azaltma regularizasyonu, `bias` ve `LayerNorm.weight` parametrelerine aşırı uyumu önlemek için uygulanmaz.

### `optimizer_grouped_parameters` Değişkeninin İncelenmesi

`optimizer_grouped_parameters` değişkeni iki sözlük içerir. Bu iki grup parametre, ağırlık azaltma oranını içerir:

#### Grup 1:

*   Ağırlık azaltma oranı: 0.1
*   Parametre 1: İçerir: tensor([[-0.0102, -0.0615, -0.0265, ..., -0.0199, -0.0372,…

#### Grup 2:

*   Ağırlık azaltma oranı: 0.0
*   Parametre 1: İçerir: tensor([0.9257, 0.8852, 0.8587, 0.8617, 0.8934, 0.8964, 0.9290,…

Parametre isimleri dahil değildir çünkü optimizasyon bu isimleri gerektirmez. Parametreler alınmıştır ve model eğitim döngüsü için hazırdır.

---

