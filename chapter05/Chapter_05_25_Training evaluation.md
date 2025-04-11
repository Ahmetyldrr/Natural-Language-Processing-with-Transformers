# Kayip ve Doğruluk Değerlerinin Değerlendirilmesi

Kayıp ve doğruluk değerleri, eğitim döngüsünün başında tanımlandığı gibi `train_loss_set` içinde saklandı. Program şimdi ölçümleri çizer:

```python
plt.figure(figsize=(15, 8))  # Grafik boyutunu 15x8 olarak ayarlar
plt.title("Training loss")  # Grafiğin başlığını "Eğitim Kaybı" olarak ayarlar
plt.xlabel("Batch")  # X ekseninin etiketini "Toplu İş" olarak ayarlar
plt.ylabel("Loss")  # Y ekseninin etiketini "Kayıp" olarak ayarlar
plt.plot(train_loss_set)  # train_loss_set listesindeki değerleri grafikte çizer
plt.show()  # Grafiği gösterir
```

Çıktı, eğitim sürecinin iyi gittiğini ve nispeten verimli olduğunu gösteren bir grafiktir:

# Şekil 5.8: Toplu İş Başına Eğitim Kaybı

Model ince ayar yapılmıştır. Şimdi tahminleri çalıştırabiliriz.

---

