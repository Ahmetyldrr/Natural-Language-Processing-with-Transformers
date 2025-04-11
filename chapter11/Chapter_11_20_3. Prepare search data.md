# Bu Bölümün Çevirisi
Bu bölümde, hala bir bilgi tabanı kullanacağız. Ancak, doğrudan metin verileri üzerinde bir sorgu oluşturmak yerine, verileri bilgi tabanının gömülü vektörleriyle çalışmak üzere hazırlayacağız. Arama verilerini bu bölümün "Ada embeddings ile Transfer öğrenme" kısmında gömeceğiz. Bu not defterinde, OpenAI'ın birkaç adımda hazırladığı veri setini kullanacağız: 
- Toplama: 2022 Olimpiyatları hakkında birkaç yüz Wikipedia makalesini indirme 
- Parçalama: Dokümanları kısa, neredeyse kendi kendine yeterli bölümlere ayırma 
- Gömme: Her bölümü OpenAI API ile gömme 
- Depolama: Verileri bir dosyada saklama. Büyük veri setleri bir vektör veritabanında depolanmalıdır. Gömülü vektörler bir vektör veritabanında indekslenebilir ve güçlü arama işlevleriyle erişilebilir. Birkaç platform vektör veritabanı hizmetleri sunar, örneğin Amazon Web Services (AWS): https://aws.amazon.com/what-is/vector-databases/. OpenAI'ın bu not defterindeki veri setini nasıl oluşturduğunu görmek için aşağıdaki not defterini inceleyebilirsiniz: https://github.com/openai/openai-cookbook/blob/950246dd0810470291aa9728c404a01aeab5a1e9/examples/Embedding_Wikipedia_articles_for_search.ipynb. Ham verilerin gömme işlemini de "Ada embeddings ile Transfer öğrenme" bölümünün bir sonraki kısmında inceleyeceksiniz. Bu bölümde, OpenAI tarafından sağlanan gömülü vektörleri yükleyeceğiz:

### Kod Açıklaması
```python
# önceden parçalanmış metin ve önceden hesaplanmış gömülü vektörleri indirme
# bu dosya ~200 MB boyutundadır, bağlantı hızınıza bağlı olarak bir dakika sürebilir
embeddings_path = "https://cdn.openai.com/API/examples/data/winter_olympics_2022.csv"
df = pd.read_csv(embeddings_path)
```
- `embeddings_path` değişkeni, OpenAI tarafından sağlanan veri setinin URL'sini içerir.
- `pd.read_csv()` fonksiyonu, belirtilen URL'den CSV dosyasını okur ve bir pandas DataFrame'e yükler.

Daha sonra, gömülü vektörleri string tipinden liste tipine çeviririz:
```python
# gömülü vektörleri CSV'deki string tipinden liste tipine çevirme
df['embedding'] = df['embedding'].apply(ast.literal_eval)
```
- `df['embedding']` gömülü vektörleri içeren sütunu seçer.
- `apply()` fonksiyonu, her bir gömülü vektöre `ast.literal_eval()` fonksiyonunu uygular.
- `ast.literal_eval()` fonksiyonu, string tipindeki gömülü vektörü liste tipine çevirir.

Pandas DataFrame iki sütun içerir: metin ve gömülü vektör:
```python
# DataFrame iki sütun içerir: "text" ve "embedding"
df
```
- `df` DataFrame'ini görüntüler.

Çıktı aşağıdaki gibidir:
# Şekil 11.8: Gömülü Vektörler Verisi

Gömülü vektör sütunundaki bir vektörün uzunluğunu yazdırabiliriz:
```python
embedding_size = len(df['embedding'].iloc[0])
print(embedding_size)
```
- `df['embedding'].iloc[0]` ilk gömülü vektörü seçer.
- `len()` fonksiyonu, gömülü vektörün uzunluğunu hesaplar.

Çıktı, "text-embedding-ada-002" modelinin 1.536 boyutlu bir gömülü vektör ürettiğini doğrular:
```
1536
```
Not defteri şimdi arama işlevselliğini uygular.

---

