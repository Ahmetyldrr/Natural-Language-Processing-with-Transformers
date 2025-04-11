# Özel Bir Eğitim Sınıfı Oluşturma

İlk olarak, günlüklerde "step" anahtarının olup olmadığını kontrol eden ve eğer varsa, eğitim sırasında her eval_steps sayısı adımına ulaşıldığında mevcut zamanı yazdıran bir sınıf oluşturuyoruz: 
```python
class CustomTrainer(Trainer):
    def log(self, logs: Dict[str, Any]) -> None:
        super().log(logs)
        if "step" in logs:  # "step" anahtarının günlükler sözlüğünde olup olmadığını kontrol edin
            step = int(logs["step"])  # adım değerini alın
            if step % self.args.eval_steps == 0:  # adım değeri eval_steps sayısına bölünebiliyorsa
                print(f"Adım {step} 'deki mevcut zaman: {datetime.now()}")  # mevcut zamanı yazdırın
```
# Eğitim Argümanlarını Tanımlama

Ardından, eğitim argümanlarını tanımlıyoruz:
```python
training_args = TrainingArguments(
    output_dir="/content/model/model/",  # modelin kaydedileceği dizin
    overwrite_output_dir=True,  # mevcut çıktıların üzerine yaz
    num_train_epochs=2,  # eğitim epoch sayısı (doğruluk artırmak için artırılabilir)
    per_device_train_batch_size=64,  # cihaz başına eğitim batch boyutu
    save_steps=10_000,  # her 10.000 adımda bir kontrol noktası kaydet
    save_total_limit=2,  # saklanacak maksimum kontrol noktası sayısı
    logging_dir='/content/model/logs/',  # günlüklerin saklanacağı dizin
    logging_steps=100,  # her 100 adımda bir günlük yaz
    logging_first_step=True,  # ilk adımda günlük yaz
    evaluation_strategy="steps",  # her "eval_steps" adımda bir değerlendirme yap
    eval_steps=500,  # her 500 adımda bir değerlendirme yap
)
```
`TrainingArguments` nesnesi, Hugging Face transformers kütüphanesi için çeşitli eğitim parametrelerini ayarlamak için kullanılır. Modelin "/content/model/model/" dizinine kaydedileceğini ve bu dizindeki mevcut çıktıların üzerine yazılacağını belirtir. Eğitim, cihaz başına 64 batch boyutu ile iki epoch boyunca çalışacaktır. Günlük ayarları, günlüklerin "/content/model/logs/" dizinine kaydedileceğini, her 100 adımda bir yazılacağını ve her 500 adımda bir değerlendirme yapılacağını belirler. Model, iki kez kontrol noktası kaydedecektir.

# Eğitimciyi Tanımlama

Son olarak, önceki hücrede çalıştırdığımız adımlara atıfta bulunarak birkaç satırda eğitimciyi tanımlıyoruz:
```python
trainer = CustomTrainer(
    model=model,  # kullanılacak model
    args=training_args,  # eğitim argümanları
    data_collator=data_collator,  # veri düzenleyici
    train_dataset=tokenized_datasets["train"],  # eğitim veri seti
    eval_dataset=tokenized_datasets["test"]  # değerlendirme veri seti
)
```

---

