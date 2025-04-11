# BERT Hakkında Doğru/Yanlış Soruları ve Cevapları

BERT, Transformers'dan Bidirectional Encoder Representations anlamına gelir. (Doğru/Yanlış) Doğru.

BERT iki aşamalı bir çerçevedir. 1. Adım ön eğitimdir (pretraining). 2. Adım ise ince ayardır (fine-tuning). (Doğru/Yanlış) Doğru.

Bir BERT modelinin ince ayarını yapmak, sıfırdan parametreleri eğitmek anlamına gelir. (Doğru/Yanlış) Yanlış.

BERT ince ayarı, ön eğitimin eğitilmiş parametreleri ile başlatılır.

BERT yalnızca tüm alt görevleri kullanarak ön eğitim yapar. (Doğru/Yanlış) Yanlış.

BERT, Maskeli Dil Modelleme (MLM) ile ön eğitim yapar. (Doğru/Yanlış) Doğru.

BERT, Sonraki Cümle Tahmini (NSP) ile ön eğitim yapar. (Doğru/Yanlış) Doğru.

BERT, matematiksel fonksiyonlar üzerinde ön eğitim yapar. (Doğru/Yanlış) Yanlış.

Soru-cevap görevi bir alt görevdir. (Doğru/Yanlış) Doğru.

Bir BERT ön eğitim modeli tokenizasyon gerektirmez. (Doğru/Yanlış) Yanlış.

Bir BERT modelinin ince ayarı, ön eğitimden daha az zaman alır. (Doğru/Yanlış) Doğru.

Bu çeviride herhangi bir python kodu bulunmamaktadır. 

Eğer BERT ile alakalı python kodları verilseydi, satır satır açıklamalar yapılırdı. Örneğin aşağıdaki kodda olduğu gibi:

```python
# Örnek kod
from transformers import BertTokenizer, BertModel

# Tokenizer ve model yükleme
tokenizer = BertTokenizer.from_pretrained('bert-base-uncased')
model = BertModel.from_pretrained('bert-base-uncased')

# Giriş metnini tokenleştirme
inputs = tokenizer("Hello, how are you?", return_tensors="pt")

# Modeli kullanarak çıktı alma
outputs = model(**inputs)

# Çıktıları yazdırma
print(outputs.last_hidden_state[:, 0, :])
```

Bu kodda:

1. `from transformers import BertTokenizer, BertModel`: Transformers kütüphanesinden BERT tokenleştiricisini ve modelini içe aktarır.
2. `tokenizer = BertTokenizer.from_pretrained('bert-base-uncased')`: Önceden eğitilmiş BERT tokenleştiricisini yükler.
3. `model = BertModel.from_pretrained('bert-base-uncased')`: Önceden eğitilmiş BERT modelini yükler.
4. `inputs = tokenizer("Hello, how are you?", return_tensors="pt")`: Giriş metnini tokenleştirir ve tensör olarak döndürür.
5. `outputs = model(**inputs)`: Yüklenen modeli kullanarak tokenleştirilmiş giriş metninin çıktısını alır.
6. `print(outputs.last_hidden_state[:, 0, :])`: Modelin son gizli katmanının çıktısını yazdırır.

---

