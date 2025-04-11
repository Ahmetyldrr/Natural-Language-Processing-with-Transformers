# Eğiticiyi Başlatmak için Gerekli Adımlar

Önceki adımlar, eğiticiyi başlatmak için gereken bilgileri hazırladı. Veri kümesi tokenleştirildi ve yüklendi. Modelimiz oluşturuldu. Veri toplayıcı oluşturuldu. Program şimdi eğiticiyi başlatabilir. Eğitici amaçlar için, program modeli hızlı bir şekilde eğitir. Epoch sayısı bir ile sınırlıdır. GPU, batch'leri paylaşabildiğimiz ve eğitim görevlerini çoklu işlem yapabildiğimiz için işimize yarar:

```python
from transformers import Trainer, TrainingArguments

training_args = TrainingArguments(
    output_dir="./KantaiBERT",
    overwrite_output_dir=True,
    num_train_epochs=1,
    per_device_train_batch_size=64,
    save_steps=10_000,
    save_total_limit=2,
)

trainer = Trainer(
    model=model,
    args=training_args,
    data_collator=data_collator,
    train_dataset=dataset,
)
```

## Eğitim Argümanları ve Eğitici Açıklaması

Eğitim argümanlarının ve eğitici'nin her satırını inceleyelim:

- `training_args = TrainingArguments(...)` : `TrainingArguments` sınıfının bir örneğini oluşturur. Burada, eğitim için hiperparametreleri ve diğer argümanları depolamak üzere `TrainingArguments` sınıfının bir örneğini oluşturuyoruz.

  - `output_dir="./KantaiBERT"` : kontrol noktası dizinidir.
  - `overwrite_output_dir=True` : çıktı dizinindeki içeriğin üzerine yazar.
  - `num_train_epochs=1` : eğitim epoch'larının sayısıdır.
  - `per_device_train_batch_size=64` : eğitim için örnek sayısının batch büyüklüğüdür. Bu durumda, 64 örnek aynı anda eğitilecektir.
  - `save_steps=10_000` : her 10.000 adımda bir kontrol noktası kaydedilir.
  - `save_total_limit=2` : kaydedilebilecek maksimum kontrol noktası sayısıdır, eski olanlar silinmeden önce.

Cihaz üzerinde batch işleme, Orijinal Transformer'ın dikkat katmanının mimarisini optimize eder. Bölüm 2'de, Transformer Modelinin Mimarisine Başlarken, dikkati "Ölçekli Nokta Ürün Dikkati" olarak tanımladık, bu aşağıdaki denklem ile temsil edilir, burada Q, K ve V'yi takıyoruz:

Q = [per_device_train_batch_size=64, d_model, d_k]  
K = [per_device_train_batch_size=64, d_model, d_k]  
V = [per_device_train_batch_size=64, d_model, d_k]

Gerekirse, dikkat katmanı bölümünü yeniden okumak ve Q, K, V, d_model ve d_k dahil olmak üzere her bir parametrenin rolünü gözden geçirmek için birkaç dakika ayırın.

Batch işleme, bir modelin performansını artırır. Ancak, büyük bir batch işlemi süreci hızlandırabilir, ancak öğrenme kalitesini sınırlayabilir, oysa daha küçük batch'ler modelin daha fazla ilişki öğrenmesini zorlar. Farklı batch büyüklükleri ile deney yapın ve modelin performansını ölçün.

- `trainer = Trainer(...)` : `Trainer` sınıfının örneğini oluşturur.
  - `model=model` : eğitilecek modeldir. Bu durumda, model daha önce kodumuzda tanımlanmıştır, notebook'un 7. Adımında konfigürasyonu tanımlarken gösterildiği gibi: `model_type: "roberta"`.
  - `args=training_args` : yukarıda oluşturduğumuz `TrainingArguments` nesnesini geçirir.
  - `data_collator=data_collator` : notebook'un 11. adımında tanımlanan `data_collator`, veri kümesinden örnekleri alır ve bir batch döndürür.
  - `train_dataset=dataset` : bu notebook'ta `kant.txt` olan eğitim veri kümesidir.

Model şimdi eğitim için hazırdır.

---

