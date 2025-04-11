# Roberta Tipi Transformer Modeli Ön Eğitimi

Aşağıdaki paragrafın birebir Türkçe çevirisi aşağıda verilmiştir.

DistilBERT transformer modeli ile aynı sayıda katman ve başlık kullanarak bir RoBERTa tipi transformer modeli ön eğitimi yapacağız. Modelin kelime hazinesi boyutu 52.000 olacak, 12 dikkat başlığı ve 6 katmanı olacak: 
```python
from transformers import RobertaConfig
config = RobertaConfig(
    vocab_size= 52_000 ,  # Kelime hazinesi boyutu 52.000 olarak ayarlandı
    max_position_embeddings= 514 ,  # Maksimum pozisyon gömme boyutu 514 olarak ayarlandı
    num_attention_heads= 12 ,  # Dikkat başlık sayısı 12 olarak ayarlandı
    num_hidden_layers= 6 ,  # Gizli katman sayısı 6 olarak ayarlandı
    type_vocab_size= 1 ,  # Tip kelime hazinesi boyutu 1 olarak ayarlandı
)
```
# Model Konfigürasyonunun İncelenmesi

Model konfigürasyonunu 9. Adım: Sıfırdan Model Başlatma bölümünde daha ayrıntılı olarak inceleyeceğiz. Öncelikle modelimizdeki tokenleştiriciyi yeniden oluşturalım.

Çevirideki python kodları satır satır açıklanmıştır:

1. `from transformers import RobertaConfig`: Bu satır, `transformers` kütüphanesinden `RobertaConfig` sınıfını içe aktarır. `RobertaConfig` sınıfı, RoBERTa modelleri için konfigürasyon ayarlarını tanımlamak için kullanılır.

2. `config = RobertaConfig(...)`: Bu satır, `RobertaConfig` sınıfının bir örneğini oluşturur ve `config` değişkenine atar.

3. `vocab_size= 52_000`: Bu parametre, modelin kelime hazinesi boyutunu 52.000 olarak ayarlar.

4. `max_position_embeddings= 514`: Bu parametre, modelin maksimum pozisyon gömme boyutunu 514 olarak ayarlar.

5. `num_attention_heads= 12`: Bu parametre, modelin dikkat başlık sayısını 12 olarak ayarlar.

6. `num_hidden_layers= 6`: Bu parametre, modelin gizli katman sayısını 6 olarak ayarlar.

7. `type_vocab_size= 1`: Bu parametre, modelin tip kelime hazinesi boyutunu 1 olarak ayarlar.

---

