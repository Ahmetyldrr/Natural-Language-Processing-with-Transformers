# MRPC Görevi ve Hugging Face BERT Modeli ile Uygulama

MRPC, GLUE görevi kapsamında, web üzerindeki yeni kaynaklardan çıkarılan cümle çiftlerini içerir. Bir insan, iki cümleyi birbirine eşdeğer olup olmadığını belirlemek için her bir çifti işaretlemiştir. Bu eşdeğerlik iki yakın ilgili özellik temel alınarak yapılmıştır: 
- Eşdeğer Anlamlı (Paraphrase equivalent)
- Anlamsal Eşdeğerlik (Semantic equivalent)

Şimdi, Hugging Face BERT modelini kullanarak bir örnek çalıştıralım.

## Kodları Açıklama

Aşağıdaki kod, `Transformer_tasks_with_Hugging_Face.ipynb` dosyasındaki ilgili hücrede bulunmaktadır.

```python
# Gerekli kütüphanelerin import edilmesi
from transformers import AutoTokenizer, TFAutoModelForSequenceClassification
import tensorflow as tf

# Önceden eğitilmiş BERT modelinin ve tokenizer'ın yüklenmesi
tokenizer = AutoTokenizer.from_pretrained("bert-base-cased-finetuned-mrpc")
model = TFAutoModelForSequenceClassification.from_pretrained("bert-base-cased-finetuned-mrpc")

# Sınıflandırma sınıfları
classes = ["not paraphrase", "is paraphrase"]

# İki örnek cümlenin tanımlanması
sequence_A = "The DVD-CCA then appealed to the state Supreme Court."
sequence_B = "The DVD CCA appealed that decision to the U.S. Supreme Court."

# Cümlelerin tokenize edilmesi ve modele uygun formatta hazırlanması
paraphrase = tokenizer.encode_plus(sequence_A, sequence_B, return_tensors="tf")

# Hazırlanan girdinin modele verilmesi ve sınıflandırma sonuçlarının alınması
paraphrase_classification_logits = model(paraphrase)[0]

# Sınıflandırma sonuçlarının softmax fonksiyonundan geçirilmesi ve numpy formatına dönüştürülmesi
paraphrase_results = tf.nn.softmax(paraphrase_classification_logits, axis=1).numpy()[0]

# Sonuçların yazdırılması
print(sequence_B, "should be a paraphrase")
for i in range(len(classes)):
    print(f"{classes[i]} : {round(paraphrase_results[i] * 100)}%")
```

## Çıktı ve Değerlendirme

Kodun çıktısı aşağıdaki gibidir:
```
The DVD CCA appealed that decision to the U.S. Supreme Court. should be a paraphrase
not paraphrase : 8%
is paraphrase : 92%
```

Bu sonuç, `sequence_B` cümlesinin `sequence_A` cümlesinin bir eşdeğeri (parafrasi) olduğunu göstermektedir. MRPC görevi, F1/doğruluk puanı yöntemi ile ölçülmektedir.

## İlerleyen Adımlar

Şimdi, bir Winograd şemasını çalıştıralım.

---

