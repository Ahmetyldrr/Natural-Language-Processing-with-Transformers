# Eğitim Döngüsü için Hiperparametreler

Eğitim döngüsü için hiperparametreler kritik öneme sahiptir, ancak zararsız görünürler. Örneğin, Adam optimizasyon algoritması ağırlık azalmasını etkinleştirecek ve bir ısınma fazı geçirecektir. Devir ve adım sayısı, modelin ne kadar "öğreneceğini" belirleyecektir. Birkaç çalıştırma, optimum eğitim seviyesini belirlemede yardımcı olabilir. Öğrenme oranı (lr) ve ısınma oranı (warmup) optimizasyon fazının erken döneminde çok küçük bir değere ayarlanmalı ve belirli bir sayıda yinelemeden sonra kademeli olarak artırılmalıdır. Bu, büyük gradyanlardan ve optimizasyon hedeflerinin aşılmasından kaçınılmasını sağlar. Bazı araştırmacılar, katman normalleştirmeden önceki alt katmanların çıktı seviyesindeki gradyanların bir ısınma oranına ihtiyaç duymadığını savunurlar. Ancak, bu sorunun çözülmesi birçok deneysel çalışma gerektirir.

# Optimizasyon Algoritmasının Tanımlanması

Optimizasyon algoritması, BertAdam adlı bir Adam sürümüdür: 
```python
optimizer = BertAdam(optimizer_grouped_parameters,
                     lr=2e-5,
                     warmup=.1)
```
Bu kodda:
- `BertAdam` sınıfı, Adam optimizasyon algoritmasının BERT için özel bir sürümüdür.
- `optimizer_grouped_parameters`, optimize edilecek parametrelerin gruplanmış halidir.
- `lr=2e-5`, öğrenme oranını 2e-5 olarak ayarlar.
- `warmup=.1`, ısınma oranını 0.1 olarak ayarlar.

# Doğruluk Ölçüm Fonksiyonunun Oluşturulması

Program, tahminleri etiketlerle karşılaştırmak için bir doğruluk ölçüm fonksiyonu ekler:
```python
# Doğruluk Ölçüm Fonksiyonu Oluşturma
# Tahminlerimizin doğruluğunu etiketlere göre hesaplamak için fonksiyon
def flat_accuracy(preds, labels):
    pred_flat = np.argmax(preds, axis=1).flatten()
    labels_flat = labels.flatten()
    return np.sum(pred_flat == labels_flat) / len(labels_flat)
```
Bu kodda:
- `flat_accuracy` fonksiyonu, tahminlerin doğruluğunu hesaplar.
- `np.argmax(preds, axis=1)`, tahminlerin en büyük değerinin indeksini döndürür.
- `.flatten()`, çok boyutlu diziyi düzleştirir.
- `np.sum(pred_flat == labels_flat)`, doğru tahminlerin sayısını hesaplar.
- `len(labels_flat)`, toplam etiket sayısını verir.

Veriler hazır. Parametreler hazırlanmış durumda. Eğitim döngüsünü etkinleştirmek için gereken her şey hazır!

---

