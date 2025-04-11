# Gensim'in Word2Vec Modülü ile Çok Boyutlu Uzay Oluşturma

Gensim'in Word2Vec modülü embeddings, yüzlerce boyut içeren çok boyutlu bir uzay oluşturacaktır. Aşağıdaki kod, Word2Vec modülünü içe aktarır, tokenleri gömülü hale getirir ve modeli gelecekte kullanmak üzere kaydeder:

```python
from gensim.models import Word2Vec
```

## Word2Vec Modelinin Eğitilmesi

```python
# Word2Vec modelini eğit
model = Word2Vec([tokens], compute_loss=True, vector_size=300, min_count=1)
```

*   `Word2Vec`: Gensim kütüphanesinden Word2Vec sınıfını kullanarak bir model oluşturur.
*   `[tokens]`: Eğitilecek token listesini içeren bir liste. Burada `tokens` değişkeninin içeriği belirtilmemiştir, ancak tokenleştirilmiş metin verilerini içermelidir.
*   `compute_loss=True`: Eğitim sırasında kayıp fonksiyonunu hesaplar.
*   `vector_size=300`: Oluşturulacak kelime vektörlerinin boyutunu belirler. Bu örnekte 300 boyutlu vektörler oluşturulur.
*   `min_count=1`: Modelin öğrenmesi için bir kelimenin en az kaç kez geçmesi gerektiğini belirler. Burada en az 1 kez geçen kelimeler dikkate alınır.

## Modelin Kaydedilmesi

```python
# Modeli daha sonra kullanmak üzere kaydet
model.save("descartes_word2vec.model")
```

*   `model.save()`: Eğitilen modeli belirtilen dosya yoluna kaydeder.
*   `"descartes_word2vec.model"`: Modelin kaydedileceği dosya adı.

## Eğitilen Modelin Bileşenleri

Eğitilen ve kaydedilen Gensim Word2Vec modeli birkaç önemli bölüm içerir:

*   **Model Parametreleri**: Modeli oluştururken belirlenen ayarları içerir, örneğin kelime vektörlerinin boyutu ve pencere boyutu gibi.
*   **Söz Varlığı (Vocabulary)**: Modelin öğrendiği tüm benzersiz kelimelerin bir listesini içerir. Her kelime, modelin embedding matrisinde belirli bir dizine karşılık gelir.
*   **Kelime Vektörleri (Embeddings)**: Modelin eğitim sırasında öğrendiği gerçek kelime vektörleridir, bir matris içinde depolanır ve her satır söz varlığındaki bir kelimeyi temsil eder.
*   **Eğitim Kaybı**: Kayıp fonksiyonu, eğitim sürecinin doğruluğunu ölçer.

Kaydedilen model, orijinal eğitim verilerini (eğitim için kullanılan metni) içermez, yalnızca verilerden öğrendiği bilgileri (kelime vektörleri) kaydeder, verilerin kendisini değil.

## Model Açıklamasını İnceleme

Model açıklamasını bir widget ile inceleyebiliriz.

---

