# MCC Değerlendirmesi
MCC, bir sınıflandırma modelini değerlendirmek için pratik bir yoldur. Program şimdi tüm veri kümesi için gerçek değerleri toplayacaktır: 
# Tahminleri ve gerçek değerleri tüm veri kümesi için Matthew'un değerlendirmesini toplamak üzere düzleştirin
```python
# İçiçe listeleri düzleştirerek tahminleri tek bir liste haline getir
flat_predictions = [item for sublist in predictions for item in sublist]
# Düzleştirilen tahminlerin her birinin en yüksek olasılık değerinin indeksini al ve flatten et
flat_predictions = np.argmax(flat_predictions, axis=1).flatten()
# Gerçek etiketleri de aynı şekilde düzleştir
flat_true_labels = [item for sublist in true_labels for item in sublist]
# Düzleştirilen gerçek etiketler ve tahminler üzerinde matthews_corrcoef hesapla
matthews_corrcoef(flat_true_labels, flat_predictions)
```
Bu metrik, değerlendirme veri kümesi tarafından sağlanan etiketleri (0 veya 1) ve MCC kullanılarak tahmin tarafından üretilen etiketleri karşılaştırır. Sonuç, model tahminlerinin stokastik doğası nedeniyle bir çalışmadan diğerine değişebilir. Bu durumda sonuç: MCC: 0.524309707232222

# Matthews Korelasyon Katsayısı
Matthews korelasyon katsayısı, ikili sınıflandırmaların kalitesini -1 ile +1 arasında değişen bir çıktı değeri ile ölçer: +1, tahminlerin %100 doğru olduğu anlamına gelir. 0, rastgele bir hesaplama ile aynıdır. -1, tahminlerin tamamen yanlış olduğunu gösterir. Bu durumda, 0.54'lük bir MCC nispeten verimlidir. Model önemli miktarda bilgi öğrenmiştir ancak geliştirilebilir.

# Sonuç
BERT modelinin ince ayarının bu son değerlendirmesi ile ince ayar çerçevesinin genel bir görünümünü elde ettik. Şimdi modelin kapsamını ve sınırlarını keşfetmek için onunla etkileşim kuracağız.

---

