# Hugging Face Veri Kütüphanesinin Kurulumu
Şimdi Hugging Face'in veri kütüphanesini kuruyoruz: 
```bash
!pip install datasets
```
Bu kütüphane ne işe yarıyor? İhtiyacımız olan her şeyi kısa sürede hallediyor.

## Kütüphanenin Özellikleri

### Veri Setinin Yüklenmesi
Kütüphane veri setini yükler:
```python
from datasets import load_dataset
dataset = load_dataset('csv', data_files='/content/model/dataset/processed_tweets.csv', column_names=["text"])
```
Bu kod, `/content/model/dataset/processed_tweets.csv` dosyasındaki verileri "text" sütunu altında yükler.

### Veri Setinin Eğitim ve Değerlendirme Setlerine Bölünmesi
Veri setini eğitim ve değerlendirme setlerine böler:
```python
from datasets import DatasetDict
dataset = dataset['train'].train_test_split(test_size=0.1)  # Değerlendirme için %10
dataset = DatasetDict(dataset)
```
Bu kod, veri setini %90 eğitim ve %10 değerlendirme setlerine böler.

### Veri Setinin Tokenleştirilmesi
Veri setini yararlı kurallarla tokenleştirir: 
Eğer bir kaydın uzunluğu "max_length" değerinden az ise, tüm kayıtların aynı uzunlukta olmasını sağlamak için doldurulur. 
Eğer bir kaydın uzunluğu "max_length" değerini aşarsa, belirtilen maksimum uzunluğa kısaltılır.
Kod kompakt bir şekilde, tek satırda doldurma ve kısaltma işlemlerini yapar:
```python
def tokenize_function(examples):
    return tokenizer(examples["text"], padding="max_length", truncation=True, max_length=128)

tokenized_datasets = dataset.map(tokenize_function, batched=True)
```
Bu kod, "text" sütunundaki verileri tokenleştirir, maksimum uzunluğu 128 olarak belirler ve gerekirse doldurma veya kısaltma yapar.

### Veri Collator Kullanımı
Verileri toplu hale getirmek için veri collator kullanır:
Veri collator birkaç satır kodla oluşturulur:
```python
data_collator = DataCollatorForLanguageModeling(
    tokenizer=tokenizer,
    mlm=False  # Otoregresif (nedensel) dil modellemesi için
)
```
Burada `mlm=False` ayarlanması, otoregresif, üretken dil modellemesi için MLM (Masked Language Modeling) özelliğini kapatır.

---

