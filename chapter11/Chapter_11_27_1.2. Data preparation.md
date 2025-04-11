# Pandas, Tiktoken ve OpenAI Embeddings Modülünü İçe Aktarma

Pandas ve tiktoken ile OpenAI embeddings modülünü içe aktarıyoruz: 
```python
import pandas as pd 
import tiktoken 
from openai.embeddings_utils import get_embedding
```

# Embedding Model Parametrelerini Seçme

"text-embedding-ada-002" modelini seçiyoruz:
```python
embedding_model = "text-embedding-ada-002"
embedding_encoding = "cl100k_base"  # bu, text-embedding-ada-002 için kodlama
max_tokens = 8000  # text-embedding-ada-002 için maksimum değer 8191
```
Tokenler, Ada'nın 8.191 token sınırının altında kalmak için dikkatlice 8.000 olarak ayarlandı. Sınırı aşarsanız, bir yanıt kesilebilir. 
"Text-embedding-ada-002" modelinin kendi kodlama tabanı yoktur. "cl100K base" üzerine kuruludur. 
"cl100K base", "text-embedding-ada-002" modelini belirli bir göreve uyarlamak için kullanılan önceden eğitilmiş kelime vektörleri kümesidir.

# Veri Kümesini Yükleme ve Birleştirilmiş Sütun Oluşturma

Veri kümesini yüklüyoruz ve bir özet ve bir incelemenin içeriğini içeren birleştirilmiş sütun oluşturuyoruz:
```python
input_datapath = "/content/Reviews.csv"  # yer kazanmak için, önceden filtrelenmiş bir veri kümesi sağlıyoruz
df = pd.read_csv(input_datapath, index_col=0)
df = df[["Time", "ProductId", "UserId", "Score", "Summary", "Text"]]
df = df.dropna()
df["combined"] = ("Title: " + df.Summary.str.strip() + "; Content: " + df.Text.str.strip())
```
DataFrame'in birkaç kaydını görüntüleyerek birleştirilmiş alanın kabul edilebilir görünüp görünmediğini kontrol edebiliriz:
```python
df.head(10)
```
Çıktı doğru ve aşağıdaki alıntıda gösterildiği gibi görünür:
# DataFrame Çıktısı

Şekil 11.9: DataFrame Çıktısı

# Veri Kümesini Hazırlama ve Kodlama

Şimdi, 1.000 en yeni incelemeyi içeren bir alt küme hazırlıyoruz ve bunları "tiktoken" ile kodluyoruz:
```python
top_n = 1000
df = df.sort_values("Time").tail(top_n * 2)  # ilk 2k girişi kes, yarısından azının filtreleneceği varsayılarak
df.drop("Time", axis=1, inplace=True)
encoding = tiktoken.get_encoding(embedding_encoding)
# yerleştirmek için çok uzun olan incelemeleri atla
df["n_tokens"] = df.combined.apply(lambda x: len(encoding.encode(x)))
df = df[df.n_tokens <= max_tokens].tail(top_n)
len(df)
```
Çıktı, verileri başarıyla çıkardığımızı ve kodladığımızı gösteriyor: 1000

# Veri Kümesini Yerleştirme

Şimdi, veri kümesini yerleştireceğiz.

---

