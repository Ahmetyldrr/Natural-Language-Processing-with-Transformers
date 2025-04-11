# Model için Sabit Maksimum Uzunluk Belirleme ve Veri İşleme

Model için verileri işlemek üzere sabit bir maksimum uzunluk belirlememiz gerekiyor. Bunun nedeni, veri kümelerindeki cümlelerin kısa olmasıdır. Ancak bundan emin olmak için, program bir dizinin maksimum uzunluğunu 128 olarak ayarlar ve diziler doldurulur:

# Maksimum Dizi Uzunluğunu Ayarlama
Eğitim setimizdeki en uzun dizi 47, ancak yine de sonuna boşluk bırakacağız. 
Orijinal makalede yazarlar 512 uzunluğu kullanmışlardır. 
```python
MAX_LEN = 128
```
BERT tokenleştiricisini kullanarak tokenleri BERT sözlüğündeki indeks numaralarına dönüştürüyoruz:
```python
input_ids = [tokenizer.convert_tokens_to_ids(x) for x in tokenized_texts]
```
Bu kod satırında, `tokenizer.convert_tokens_to_ids()` fonksiyonu tokenleri BERT sözlüğündeki indeks numaralarına çevirir. 
- `tokenized_texts`: Önceden tokenleştirilmiş metinler listesi
- `x`: Tokenleştirilmiş metinler listesindeki her bir eleman
- `tokenizer.convert_tokens_to_ids(x)`: Her bir tokenleştirilmiş metni BERT sözlüğündeki indeks numaralarına çevirir

Giriş tokenlerimizi dolduruyoruz:
```python
input_ids = pad_sequences(input_ids, maxlen=MAX_LEN, dtype="long", truncating="post", padding="post")
```
Bu kod satırında, `pad_sequences()` fonksiyonu giriş tokenlerimizi doldurur veya kırpar.
- `input_ids`: Doldurulacak veya kırpılacak diziler listesi
- `maxlen=MAX_LEN`: Doldurulacak veya kırpılacak maksimum uzunluk
- `dtype="long"`: Dizi veri tipi
- `truncating="post"`: Kırpma işlemi sona doğru yapılır
- `padding="post"`: Doldurma işlemi sona doğru yapılır

Diziler işlendikten sonra, program dikkat maskelerini oluşturur.

---

