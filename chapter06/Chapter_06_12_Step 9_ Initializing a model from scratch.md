# Bu Bölümde Modelin Başlangıçtan Oluşturulması ve Boyutunun İncelenmesi
Bu bölümde, sıfırdan bir model başlatacağız ve modelin boyutunu inceleyeceğiz. Program önce dil modelleme için bir RoBERTa maskeli modeli içe aktarır: 
```python
from transformers import RobertaForMaskedLM
```
Model, 7. Adımda tanımlanan yapılandırma ile başlatılır:
```python
model = RobertaForMaskedLM(config=config)
```
Modeli yazdırdığımızda, 6 katmanlı ve 12 başlıklı bir BERT modeli olduğunu görebiliriz:
```python
print(model)
```
Orijinal Transformer modelinin kodlayıcısının yapı taşları, bu çıktı alıntısında gösterildiği gibi farklı boyutlarla mevcuttur:
```
RobertaForMaskedLM(
  (roberta): RobertaModel(
    (embeddings): RobertaEmbeddings(
      (word_embeddings): Embedding(52000, 768, padding_idx=1)
      (position_embeddings): Embedding(514, 768, padding_idx=1)
      (token_type_embeddings): Embedding(1, 768)
      (LayerNorm): LayerNorm((768,), eps=1e-12, elementwise_affine=True)
      (dropout): Dropout(p=0.1, inplace=False)
    )
    (encoder): BertEncoder(
      (layer): ModuleList(
        (0): BertLayer(
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
          )
          (output): BertOutput(
            (dense): Linear(in_features=3072, out_features=768, bias=True)
            (LayerNorm): LayerNorm((768,), eps=1e-12, elementwise_affine=True)
            (dropout): Dropout(p=0.1, inplace=False)
          )
        )
```
Devam etmeden önce yapılandırma çıktısının ayrıntılarını incelemek için biraz zaman ayırın. Modeli içeriden tanıyacaksınız. Transformer'ların LEGO® tipi yapı taşları analizi eğlenceli hale getirir. Örneğin, klasik sinir ağlarında olduğu gibi, dropout düzenlileştirmesinin alt katmanlar boyunca mevcut olduğunu fark edeceksiniz. Şimdi, parametreleri inceleyelim.

## Python Kodlarının Satır Satır Açıklaması

1. `from transformers import RobertaForMaskedLM`: Bu satır, `transformers` kütüphanesinden `RobertaForMaskedLM` sınıfını içe aktarır. Bu sınıf, maskeli dil modelleme görevi için RoBERTa modelini temsil eder.

2. `model = RobertaForMaskedLM(config=config)`: Bu satır, `RobertaForMaskedLM` sınıfının bir örneğini oluşturur ve `config` parametresi ile yapılandırır. `config`, modelin hiperparametrelerini ve diğer yapılandırma ayarlarını içerir.

3. `print(model)`: Bu satır, modelin temsilini yazdırır. Bu, modelin katmanlarını ve yapı taşlarını gösterir.

Modelin temsilinde görülen bazı önemli katmanlar ve işlevleri:

- `RobertaEmbeddings`: Giriş tokenlarını vektör temsillerine dönüştürür.
- `BertEncoder`: Giriş vektörlerini işler ve bağlamlı temsiller üretir.
- `BertLayer`: Kodlayıcının temel yapı taşıdır ve dikkat mekanizması, feed-forward ağ ve layer normalization içerir.
- `BertSelfAttention`: Kendine dikkat mekanizmasını uygular.
- `BertSelfOutput`, `BertIntermediate`, `BertOutput`: Dikkkat mekanizması ve feed-forward ağın çıktısını işler ve layer normalization uygular.
- `Dropout`: Overfitting'i önlemek için dropout düzenlileştirmesini uygular.

Bu katmanlar ve işlevler, modelin dil modelleme görevini yerine getirmesini sağlar.

---

