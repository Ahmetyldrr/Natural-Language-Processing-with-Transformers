# İnce Ayar Modeli ve Torch Tensörleri

İnce ayar modeli torch tensörleri kullanır. PyTorch tensörleri: 
- GPU'ların kullanımını optimize eder.
- GPU/CPU kontrolünü kolaylaştırır.

Bu not defterinde, Hugging Face modelinin ve veri kümelerimizin GPU'ya aktarılacağını fark edeceksiniz. Bu işlem, eğer GPU mevcutsa, bu bölümün ve not defterinin "torch için cihaz olarak CUDA belirtme" kısmında tanımlandığı gibi, eğitim döngüsü kodundaki `to-device` komutu aracılığıyla gerçekleşir. Program böylece verileri torch tensörlerine dönüştürecektir:

# Torch tensörleri modelimiz için gerekli veri tipidir
```python
train_inputs = torch.tensor(train_inputs)
validation_inputs = torch.tensor(validation_inputs)
train_labels = torch.tensor(train_labels)
validation_labels = torch.tensor(validation_labels)
train_masks = torch.tensor(train_masks)
validation_masks = torch.tensor(validation_masks)
```
Dönüştürme tamamlandı. Şimdi, bir iteratör oluşturmamız gerekiyor.

## Kod Açıklaması

1. `train_inputs = torch.tensor(train_inputs)`: Eğitim girdi verilerini torch tensörüne dönüştürür.
2. `validation_inputs = torch.tensor(validation_inputs)`: Doğrulama girdi verilerini torch tensörüne dönüştürür.
3. `train_labels = torch.tensor(train_labels)`: Eğitim etiket verilerini torch tensörüne dönüştürür.
4. `validation_labels = torch.tensor(validation_labels)`: Doğrulama etiket verilerini torch tensörüne dönüştürür.
5. `train_masks = torch.tensor(train_masks)`: Eğitim maskeleme verilerini torch tensörüne dönüştürür.
6. `validation_masks = torch.tensor(validation_masks)`: Doğrulama maskeleme verilerini torch tensörüne dönüştürür.

Bu kod satırları, ilgili verileri PyTorch'un tensör veri yapısına dönüştürerek, ileriki işlemler için uygun hale getirir.

---

