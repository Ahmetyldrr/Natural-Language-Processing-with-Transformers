# Programın Veri Hazırlama Adımları

Program şimdi, alan içi veri kümesi verilerini eğitim ve doğrulama kümelerine ayırma standardı işlemini gerçekleştirir:

# Eğitim ve Doğrulama Kümelerine Ayırma

Eğitim için verilerimizi eğitim ve doğrulama kümelerine ayırmak üzere `train_test_split` kullanıyoruz:
```python
train_inputs, validation_inputs, train_labels, validation_labels = train_test_split(input_ids, labels, random_state=2018, test_size=0.1)
```
Bu kod satırı, `input_ids` ve `labels` değişkenlerini sırasıyla `train_inputs`, `validation_inputs` ve `train_labels`, `validation_labels` olarak ayırır.

- `input_ids`: Modelin girdi kimliklerini temsil eder.
- `labels`: Girdi verilerinin etiketlerini temsil eder.
- `random_state=2018`: Sonuçların tekrarlanabilir olmasını sağlar, yani her çalıştırdığınızda aynı sonucu alırsınız.
- `test_size=0.1`: Verinin %10'unun doğrulama kümesi olarak ayrılacağını belirtir.

Benzer şekilde, dikkat maskeleri de eğitim ve doğrulama kümelerine ayrılır:
```python
train_masks, validation_masks, _, _ = train_test_split(attention_masks, input_ids, random_state=2018, test_size=0.1)
```
Bu satırda:
- `attention_masks`: Modelin dikkat maskelerini temsil eder.
- `input_ids` burada sadece boyut uyumu için kullanılmıştır, gerçek ayrım `attention_masks` üzerinde yapılır.
- `_` değişkeni, Python'da kullanılmayan değerler için bir konvansiyondur. Burada `train_test_split` fonksiyonu dört değer döndürür, ancak son iki değer (`input_ids`'in eğitim ve doğrulama kümeleri) kullanılmaz, bu nedenle `_` ile atlanır.

# Torch'a Uygun Hale Getirme

Veri hazır, ancak Torch'a uyarlanması gerekiyor.

---

