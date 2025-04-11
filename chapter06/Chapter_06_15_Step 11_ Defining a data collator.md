# Eğiticiyi Başlatmadan Önce Veri Toplayıcı Çalıştırma

Eğiticiyi başlatmadan önce bir veri toplayıcı çalıştırmamız gerekiyor. Bir veri toplama aracı, toplu işleme hazırlamak için veri kümesinden örnekleri toplayacaktır. Ayrıca `mlm=True` ayarlayarak MLM için toplu örnek işleme hazırlyoruz. Ayrıca, `mlm_probability=0.15` eğitmek için maskelenmiş token sayısını da ayarlıyoruz. Bu, ön eğitim süreci sırasında maskelenen tokenların yüzdesini belirleyecektir.

Şimdi `data_collator`'ı tokenizer, MLM, etkin ve maskelenmiş token oranını 0.15 olarak ayarlayarak başlatıyoruz:

```python
# transformers kütüphanesinden DataCollatorForLanguageModeling sınıfını içe aktarıyoruz
from transformers import DataCollatorForLanguageModeling

# DataCollatorForLanguageModeling örneğini oluşturuyoruz
data_collator = DataCollatorForLanguageModeling(
    # tokenizer'ı belirliyoruz
    tokenizer=tokenizer, 
    # MLM'i etkinleştiriyoruz
    mlm=True, 
    # Maskelenmiş token olasılığını ayarlıyoruz
    mlm_probability=0.15 
)
```

Artık eğiticiyi başlatmaya hazırız.

---

