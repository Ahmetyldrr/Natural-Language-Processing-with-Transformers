# Ada, Veri Kümesinin Birleştirilmiş Sütununu Gömer ve Gömmeleri Depolayacaktır

Ada şimdi veri kümesinin birleştirilmiş sütununu gömecek ve gömme vektörlerini embedding sütununda depolayacaktır:

# README'ye göre API anahtarınızı ortamınızda ayarladığınızdan emin olun: https://github.com/openai/openai-python#usage
# Bu işlem birkaç dakika sürebilir
```python
df["embedding"] = df.combined.apply(lambda x: get_embedding(x, engine=embedding_model))
```
Yukarıdaki Python kodu, `df` adlı DataFrame'in `combined` sütunundaki her bir metni `get_embedding` fonksiyonu ile gömer ve sonuçları `embedding` sütununa yazar. 
- `df["embedding"]`: DataFrame'de "embedding" adlı yeni bir sütun oluşturur veya mevcutsa üzerine yazar.
- `df.combined.apply()`: `combined` sütunundaki her bir öğeye bir fonksiyonu uygular.
- `lambda x: get_embedding(x, engine=embedding_model)`: Uygulanacak anonim fonksiyondur. Her bir `x` değeri için `get_embedding` fonksiyonunu çağırır ve `engine` parametresi olarak `embedding_model`'i kullanır.

```python
df.to_csv("fine_food_reviews_with_embeddings_1k.csv")
```
Bu satır, güncellenmiş DataFrame'i (`df`) "fine_food_reviews_with_embeddings_1k.csv" adlı bir CSV dosyasına kaydeder.

Bu işlemdeki ilginç nokta, Ada'nın sadece bir kelime değil, uzun bir metin dizesini gömmesidir. Ada, gömme vektörlerini üretmek için tam bir diziyi ve bağlamı dikkate almıştır. Şimdi gömme vektörlerimizi ileride kullanmak üzere kaydediyoruz:

# Dosya işlemleri için örnek kod, fakat yorum satırına alınmış:
```python
# f = open("drive/MyDrive/files/api_key.txt", "r")
```
Bu satır, "drive/MyDrive/files/api_key.txt" dosyasını okuma modunda açar. Ancak yorum satırına alındığından çalıştırılmaz.

```python
!cp /content/fine_food_reviews_with_embeddings_1k.csv drive/MyDrive/files/fine_food_reviews_with_embeddings_1k.csv
```
Bu satır, `/content/fine_food_reviews_with_embeddings_1k.csv` dosyasını `drive/MyDrive/files/` dizinine kopyalar. `!` işareti, Jupyter Notebook'ta kabuk komutu olarak çalıştırılacağını belirtir.

# Kümeleme Uygulaması

Şimdi elde ettiğimiz vektör uzayına bir kümeleme algoritması uygulayacağız.

---

