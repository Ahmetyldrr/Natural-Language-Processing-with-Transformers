# Programın Başlatılması ve BERT Konfigürasyonu

Program şimdi bir BERT uncased konfigürasyonu başlatıyor:

```python
from transformers import BertModel, BertConfig
configuration = BertConfig()  # BERT bert-base-uncased stilinde bir konfigürasyon başlatma
model = BertModel(configuration)  # BERT bert-base-uncased stilinde bir model başlatma
configuration = model.config  # Model konfigürasyonuna erişme
print(configuration)  # Model konfigürasyonunu yazdırma
```

Yukarıdaki kod, `transformers` kütüphanesinden `BertModel` ve `BertConfig` sınıflarını içe aktarır. 
- `BertConfig()` ile varsayılan bir BERT konfigürasyonu oluşturulur.
- `BertModel(configuration)` ile bu konfigürasyona göre bir BERT modeli oluşturulur.
- `model.config` ile modelin konfigürasyonuna erişilir ve `configuration` değişkenine atanır.
- `print(configuration)` ile konfigürasyon yazdırılır.

Çıktı, aşağıdaki gibi ana Hugging Face parametrelerini gösterir (kütüphane sıklıkla güncellenir):

```json
BertConfig {
  "attention_probs_dropout_prob": 0.1,
  "hidden_act": "gelu",
  "hidden_dropout_prob": 0.1,
  "hidden_size": 768,
  "initializer_range": 0.02,
  "intermediate_size": 3072,
  "layer_norm_eps": 1e-12,
  "max_position_embeddings": 512,
  "model_type": "bert",
  "num_attention_heads": 12,
  "num_hidden_layers": 12,
  "pad_token_id": 0,
  "type_vocab_size": 2,
  "vocab_size": 30522
}
```

# Ana Parametrelerin Açıklaması

Gösterilen ana parametrelerden bazılarını inceleyelim:

- **attention_probs_dropout_prob: 0.1** - Dikkat olasılıklarına 0.1 dropout oranı uygular.
- **hidden_act: "gelu"** - Kodlayıcıda doğrusal olmayan bir aktivasyon fonksiyonudur. Gaussian Error Linear Unit aktivasyon fonksiyonudur. Girdi, büyüklüğü ile ağırlıklandırılır, bu da onu doğrusal olmayan yapar.
- **hidden_dropout_prob: 0.1** - Tam bağlı katmanlara uygulanan dropout olasılığıdır. Tam bağlantılar, gömme, kodlayıcı ve havuzcu katmanlarında bulunabilir. Çıktı, her zaman bir dizinin içeriğinin iyi bir yansıması değildir. Gizli durumların dizisini havuzlamak, çıktı dizisini iyileştirir.
- **hidden_size: 768** - Kodlanmış katmanların ve havuzcu katmanın boyutudur.
- **initializer_range: 0.02** - Ağırlık matrislerini başlatırken standart sapma değeridir.
- **intermediate_size: 3072** - Kodlayıcının ileri beslemeli katmanının boyutudur.
- **layer_norm_eps: 1e-12** - Katman normalizasyon katmanları için epsilon değeridir.
- **max_position_embeddings: 512** - Modelin kullandığı maksimum uzunluktur.
- **model_type: "bert"** - Modelin adıdır.
- **num_attention_heads: 12** - Kafaların sayısıdır.
- **num_hidden_layers: 12** - Katmanların sayısıdır.
- **pad_token_id: 0** - Eğitim dolgu tokenlarından kaçınmak için dolgu tokenının ID'sidir.
- **type_vocab_size: 2** - Dizileri tanımlayan `token_type_ids` boyutudur. Örneğin, "the dog[SEP] The cat[SEP]" token ID'leri [0,0,0, 1,1,1] ile temsil edilebilir.
- **vocab_size: 30522** - Modelin girdi ID'lerini temsil etmek için kullandığı token sayısıdır.

Bu parametreleri akılda tutarak, önceden eğitilmiş modeli yükleyebiliriz.

---

