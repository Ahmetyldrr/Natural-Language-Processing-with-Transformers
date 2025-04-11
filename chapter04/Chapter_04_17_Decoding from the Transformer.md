# Transformer Modeli ile Makine Çevirisi

Transformer modeli, İngilizce cümleyi kodlar ve Almancaya çevirir. Model ve ağırlıkları, yetenek setini oluşturur. Trax, kod çözme işlevini sezgisel hale getirmiştir: 

```python
tokenized = tokenized[None, :]  # Toplu boyut ekleyin.
```
# Kod Çözme İşlemi

Yukarıdaki kod satırı, `tokenized` değişkenine toplu boyut (batch dimension) ekler. Bu işlem, Trax kütüphanesinin otoregresif örnekleme işlevinin gerektirdiği bir adımdır.

```python
tokenized_translation = trax.supervised.decoding.autoregressive_sample(
    model, tokenized, temperature=0.0)  # Daha yüksek sıcaklık: daha çeşitli sonuçlar.
```
# Otoregresif Örnekleme

Bu kod satırı, `trax.supervised.decoding.autoregressive_sample` işlevini kullanarak `model` üzerinden otoregresif örnekleme yapar. `temperature` parametresi, sonuçların çeşitliliğini kontrol eder. Daha yüksek sıcaklık değerleri, insan çevirmenlerde olduğu gibi farklı sonuçlar üretecektir. Bu, bu bölümün Makine çevirisini tanımlama kısmında açıklanmıştır.

# Çeviri Sonuçlarının Gösterilmesi

Son olarak, program, çeviri sonucunu tokenlerden arındırarak (de-tokenize) görüntüler.

---

