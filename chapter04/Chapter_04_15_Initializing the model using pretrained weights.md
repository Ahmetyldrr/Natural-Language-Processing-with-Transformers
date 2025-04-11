# Eğitilmiş Ağırlıkların Yüklenmesi

Önceden eğitilmiş ağırlıklar, Transformer'ın zekasını içerir. Ağırlıklar, Transformer'ın dil temsilini oluşturur. Ağırlıklar, bir tür makine zekası IQ'su üretecek bir dizi parametre olarak ifade edilebilir. Modele can verelim ve ağırlıkları başlatalım:

```python
model.init_from_file('gs://trax-ml/models/translation/ende_wmt32k.pkl.gz', 
                     weights_only=True)
```

Bu kod, ağırlıkları görüntüler ve modelin nasıl inşa edildiğini görmek için yararlıdır:

```
1.95107, 2.3058772, 1.9680263, 1.5733448, 1.7866848, 2.192197, 2.228089, 1.7842566, 2.2654603, 2.0060909, 1.2600263, 1.7945113, 1.1802608,
...
```

Makine konfigürasyonu ve zekası artık çalışmaya hazır. Bir cümleyi tokenize edelim.

# Kod Açıklaması

1. `model.init_from_file()` fonksiyonu, önceden eğitilmiş ağırlıkları bir dosyadan yükler.
   - `'gs://trax-ml/models/translation/ende_wmt32k.pkl.gz'`: Yüklenen ağırlıkların bulunduğu dosyanın yolu.
   - `weights_only=True`: Sadece ağırlıkların yüklenmesini sağlar.

Bu python kodu, Trax kütüphanesini kullanarak önceden eğitilmiş bir modelin ağırlıklarını yükler. Yüklenen ağırlıklar, modelin dil temsilini içerir ve makine zekası için kullanılır.

---

