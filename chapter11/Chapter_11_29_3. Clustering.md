# K-MEANS KÜMELEME ALGORİTMASI İLE YORUMLARIN KÜMELENMESİ

Bu bölümde, k-means kümeleme algoritması kullanarak yorumların kümelerini oluşturacağız. Yorum setlerinin genel bir görünümünü elde edeceğiz. Az önce oluşturduğumuz embedding'lerle birlikte ince gıda yorumlarını yükleyelim. Eğer not defterini yeniden çalıştırırsanız, gerekli kütüphaneleri kurduktan sonra buradan çalıştırabilirsiniz. Embedding bölümünü yeniden çalıştırmak zorunda kalmayacaksınız. Aşağıdaki kod, verileri bir pandas DataFrame'e yükler ve varsa hatalı satırları filtreler:

```python
# İçe aktarmalar
import numpy as np 
import pandas as pd 

# Veri yükleme
datafile_path = "fine_food_reviews_with_embeddings_1k.csv"
# df = pd.read_csv(datafile_path)  # csv dosyasını oku, hatalı satırları atla
df = pd.read_csv('fine_food_reviews_with_embeddings_1k.csv', error_bad_lines=False)

# Dataframe'deki satır sayısını say
df_line_count = len(df)

# csv dosyasındaki toplam satır sayısını say
with open('fine_food_reviews_with_embeddings_1k.csv') as f:
    total_line_count = sum(1 for _ in enumerate(f))

# Hatalı satır sayısını hesapla
bad_lines = total_line_count - df_line_count
print(f'Hatalı satır sayısı: {bad_lines}')
```

Çıktı, bir satırın filtrelendiğini gösterir: 
Hatalı satır sayısı: 1

Program şimdi embedding sütununu bir NumPy dizisine dönüştürür:
```python
df["embedding"] = df.embedding.apply(eval).apply(np.array)  # string'i numpy dizisine çevir
matrix = np.vstack(df.embedding.values)
matrix.shape
```

Matrix'in şekli, 1.000 satırımız olduğunu ve Ada embedding'lerinin 1.536 boyutlu olduğunu gösterir: (1000, 1536)

Artık k-means kümeleme ile kümeleri bulmaya hazırız.

---

