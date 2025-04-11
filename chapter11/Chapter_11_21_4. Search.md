# Kullanıcı İsteği ve Metinlerin İlgililik Sıralaması

Bir kullanıcı metin formatında bir istek yapacaktır. Metin, embedding vektörleri ile aynı model kullanılarak gömülmelidir. Daha sonra, gömülü istek ile pandas DataFrame'deki gömülü kayıtlar arasındaki mesafe hesaplanır ve sıralanır. `strings_ranked_by_relatedness` fonksiyonu bir sorgu dizesi, pandas DataFrame ve `top_n` sayısını alır:

```python
def strings_ranked_by_relatedness(query: str, df: pd.DataFrame, relatedness_fn=lambda x, y: 1 - spatial.distance.cosine(x, y), top_n: int = 100) -> tuple[list[str], list[float]]:
```

Bu fonksiyon, iki liste içeren bir tuple döndürür: biri sorgu ile en ilgili `top_n` dizeyi içeren liste, diğeri ise ilgili skorları içeren listedir.

## Fonksiyonun Adımları

1. **Sorgu Dizesinin Gömülmesi**: Fonksiyon, sorgu dizesini, arama verilerini gömmek için kullanılan aynı modeli kullanarak gömer:
   ```python
from openai import OpenAI
client = OpenAI()
query_embedding_response = client.embeddings.create(model=EMBEDDING_MODEL, input=query)
```

2. **Sorgu Embedding Vektörünün Alınması**: Fonksiyon, sorgu için embedding vektörünü yanıttan alır:
   ```python
query_embedding = query_embedding_response.data[0].embedding
```

3. **DataFrame'deki Satırların İşlenmesi**: Fonksiyon, DataFrame'deki satırlar üzerinde döngü yapar. Her satır için, o satırdaki metni ve metnin (sorguya) ilgiliğini içeren bir tuple oluşturur:
   ```python
strings_and_relatednesses = [(row["text"], relatedness_fn(query_embedding, row["embedding"])) for i, row in df.iterrows()]
```

4. **İlgililiğe Göre Sıralama**: Elde edilen liste, ilgiliğe göre azalan sırada sıralanır:
   ```python
strings_and_relatednesses.sort(key=lambda x: x[1], reverse=True)
```

5. **Listelerin Ayrılması**: Son olarak, `zip` fonksiyonu kullanılarak tuple listesi, `strings` ve `relatedness` adlı iki ayrı listeye ayrılır:
   ```python
strings, relatednesses = zip(*strings_and_relatednesses)
```

6. **İlgili Sonuçların Döndürülmesi**: Fonksiyon, hem `strings` hem de `relatednesses` listelerinden `top_n` elemanı döndürür:
   ```python
return strings[:top_n], relatednesses[:top_n]
```

## Örnek Uygulama

Fonksiyonu test etmek için bir örnek çalıştırılır:
```python
# Örnekler
strings, relatednesses = strings_ranked_by_relatedness("curling gold medal", df, top_n=5)
for string, relatedness in zip(strings, relatednesses):
    print(f"{relatedness=: .3f}")
    display(string)
```

Bu, en ilgili ilk 5 metni ve onların ilgili skorlarını azalan sırada gösterir. Örneğin:
```
relatedness=0.879
'Curling at the 2022 Winter Olympics\n\n==Medal summary==\n\n===Medal table===\n\n{{Medals table\n | caption        = \n | host           = \n | flag_template  = flagIOC\n | event          = 2022 Winter\n | team           = \n | gold_CAN = 0 | silver_CAN = 0 | bronze_CAN = 1\n | gold_ITA = 1 | silver_ITA = 0 | bronze_ITA = 0\n | gold_NOR = 0 | silver_NOR = 1 | bronze_NOR = 0\n | gold_SWE = 1 | silver_SWE = 0 | bronze_SWE = 2\n | gold_GBR = 1 | silver_GBR = 1 | bronze_GBR = 0\n | gold_JPN = 0 | silver_JPN = 1 | bronze_JPN - 0\n}}'
relatedness=0.872
...
```

İlgilik fonksiyonunun çalıştığı doğrulanmıştır. Şimdi, en ilgili metni OpenAI GPT-3.5-turbo isteğinin mesajına eklememiz gerekiyor.

---

