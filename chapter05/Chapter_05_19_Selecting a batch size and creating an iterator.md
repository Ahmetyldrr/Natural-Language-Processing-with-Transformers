# Program Veri Yükleme ve İşleme

Program, bu hücrede bir batch boyutunu seçer ve bir yineleyici (iterator) oluşturur. Yineleyici, veriler arasında döngü yapmanın ve tüm verileri belleğe yüklemek yerine batch'leri yüklemenin verimli bir yoludur. Yineleyici, `torch DataLoader` ile birlikte, makinenin belleğini çökertmeden büyük veri kümelerini batch'e göre eğitmeye olanak tanır. Bu modelde, batch boyutu 32'dir:

# Eğitim için bir batch boyutu seçin. BERT'i belirli bir görev için fine-tuning yaparken, yazarlar 16 veya 32 batch boyutu önerir.
```python
batch_size = 32
```

# Verilerimizin yineleyicisini `torch DataLoader` ile oluşturun. Bu, eğitim sırasında bellekte tasarruf etmeye yardımcı olur çünkü, bir for döngüsü gibi değil,
# yineleyici ile tüm veri kümesi belleğe yüklenmek zorunda değildir.
```python
train_data = TensorDataset(train_inputs, train_masks, train_labels)
train_sampler = RandomSampler(train_data)
train_dataloader = DataLoader(train_data, sampler=train_sampler, batch_size=batch_size)

validation_data = TensorDataset(validation_inputs, validation_masks, validation_labels)
validation_sampler = SequentialSampler(validation_data)
validation_dataloader = DataLoader(validation_data, sampler=validation_sampler, batch_size=batch_size)
```

Veriler işlenmiş ve hazır hale getirilmiştir. Program şimdi BERT modelini yükleyebilir ve yapılandırabilir.

### Kod Açıklamaları:

1. `batch_size = 32`: Batch boyutunu 32 olarak ayarlar.
2. `train_data = TensorDataset(train_inputs, train_masks, train_labels)`: Eğitim verilerini `TensorDataset` olarak birleştirir.
   - `train_inputs`: Eğitim giriş verileri.
   - `train_masks`: Eğitim maskeleri.
   - `train_labels`: Eğitim etiketleri.

3. `train_sampler = RandomSampler(train_data)`: Eğitim verileri için rastgele bir örnekleyici oluşturur.

4. `train_dataloader = DataLoader(train_data, sampler=train_sampler, batch_size=batch_size)`: Eğitim verileri için bir `DataLoader` oluşturur.
   - `train_data`: Eğitim verileri.
   - `sampler=train_sampler`: Örnekleyici olarak `train_sampler` kullanılır.
   - `batch_size=batch_size`: Batch boyutu olarak `batch_size` kullanılır.

5. `validation_data = TensorDataset(validation_inputs, validation_masks, validation_labels)`: Doğrulama verilerini `TensorDataset` olarak birleştirir.

6. `validation_sampler = SequentialSampler(validation_data)`: Doğrulama verileri için sırayla örnekleyen bir örnekleyici oluşturur.

7. `validation_dataloader = DataLoader(validation_data, sampler=validation_sampler, batch_size=batch_size)`: Doğrulama verileri için bir `DataLoader` oluşturur.

Bu kod parçacıkları, derin öğrenme modelinin eğitimi için verilerin nasıl yükleneceğini, işleneceğini ve yapılandırılacağını gösterir.

---

