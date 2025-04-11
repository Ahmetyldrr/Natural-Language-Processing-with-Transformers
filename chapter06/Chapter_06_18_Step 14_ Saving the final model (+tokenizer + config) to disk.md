# Modeli ve Konfigürasyonu Kaydetme

Şimdi modeli ve konfigürasyonu kaydedeceğiz: 
```python
trainer.save_model("./KantaiBERT")
```
Dosya yöneticisinde Yenile (Refresh) düğmesine tıklayın, ve dosyalar görünmelidir:

### Şekil 6.4: Tüm KantaiBERT model dosyalarının bulunduğu Colab dosya yöneticisi

`config.json`, `pytorch_model.bin` ve `training_args.bin` şimdi dosya yöneticisinde görünmelidir. `merges.txt` ve `vocab.json` önceden eğitilmiş veri kümesinin tokenizasyonunu içerir. 
Modeli sıfırdan oluşturduk. 
Önceden eğitilmiş model ve tokenizer ile bir dil modelleme görevi gerçekleştirmek için pipeline'ı içe aktaralım. 

Not: 
- `trainer.save_model("./KantaiBERT")` satırı, eğitilen modeli "./KantaiBERT" dizinine kaydeder.
- `config.json`, model konfigürasyonunu içerir.
- `pytorch_model.bin`, modelin ağırlıklarını içerir.
- `training_args.bin`, eğitim sırasında kullanılan argümanları içerir.
- `merges.txt` ve `vocab.json`, önceden eğitilmiş tokenizasyon bilgilerini içerir.

---

