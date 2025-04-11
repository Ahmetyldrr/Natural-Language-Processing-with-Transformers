# Eğitimin Başlatılması ve İlerleme Çubuğu Bilgileri

`trainer.train()` komutu ön eğitim sürecini etkinleştirir. İlerleme çubuğu bilgileri, her çalıştırmada modelin iyileştirilmesi için izlenmesi gereken kritik bilgileri gösterir. Bu bilgiler, transformer modellerinin rastgele doğası nedeniyle çalıştırmalar arasında değişebilir. Örneğin:
- 218/3.216: 3.216 görevden 218'i tamamlandı
- 01:24: başlangıçtan bu yana geçen zaman
- < 19:39: tahmini kalan süre
- 2.54 it/s: saniyede 2.54 iterasyon işleme hızı
- Epoch 0.07/1: şu anda 1 tam epoch'un %7'sinde

# İlerleme Çubuğunun Altındaki Bilgiler

İlerleme çubuğunun altında şunları görselleştirebiliriz:
- **step**: adım sayısı
- **training loss**: eğitim kaybı (azalmalıdır)
- **validation loss**: doğrulama kaybı (eğitim kaybından daha düşük olmalı veya yakınsamalıdır). Eğer daha yüksekse, model aşırı uyum (overfitting) gösterebilir.

Python kodu bulunmamaktadır, sadece bir ingilizce paragrafın türkçeye çevirisi yapılmıştır. Eğer python kodunun açıklaması istenseydi, kod satırları ile birlikte açıklama yapılacaktı. 

Örneğin, eğer `trainer.train()` komutu bir python kodu olsaydı ve aşağıdaki gibi bir yapıya sahip olsaydı:

```python
class Trainer:
    def train(self):
        # eğitim sürecini başlat
        for epoch in range(num_epochs):
            # her epoch için işlemleri yap
            for step, batch in enumerate(data_loader):
                # her adım için işlemleri yap
                # loss hesapla
                # geriye yayılım yap
                # ilerleme çubuğunu güncelle
                print(f"Epoch {epoch+1}/{num_epochs}, Step {step+1}, Loss: {loss.item():.4f}")
```

Bu kodun açıklaması şu şekilde olabilirdi:

1. `class Trainer:` Trainer adlı bir sınıf tanımlanıyor.
2. `def train(self):` bu sınıfın train adlı bir metodu tanımlanıyor.
3. `for epoch in range(num_epochs):` num_epochs kadar epoch döngüsü başlıyor.
4. `for step, batch in enumerate(data_loader):` veri yükleyicisindeki (data_loader) her bir batch için işlemleri yapıyor.
5. `print(f"Epoch {epoch+1}/{num_epochs}, Step {step+1}, Loss: {loss.item():.4f}")` her adımda epoch, adım sayısı ve loss değerini yazdırıyor.

Ancak, verdiğiniz metinde python kodu bulunmamaktadır.

---

