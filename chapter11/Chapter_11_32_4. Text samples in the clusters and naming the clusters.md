# İngilizce Paragrafın Türkçe Çevirisi

Her bir küme için 5 inceleme seçeceğiz, onlara bir başlık vereceğiz ve davinci-002'ye ortak noktalarını bulmasını soracağız:

```python
import openai  # Her bir gruba ait bir incelemeyi okumak.
rev_per_cluster = 5
for i in range(n_clusters):
    print(f"Küme {i} Teması:", end=" ")
    reviews = "\n".join(
        df[df.Cluster == i]
        .combined.str.replace("Title: ", "")
        .str.replace("\n\nContent: ", ":  ")
        .sample(rev_per_cluster, random_state=42)
        .values
    )
    response = openai.Completion.create(
        engine="davinci-002",
        prompt=f'Aşağıdaki müşteri yorumlarının ortak noktası nedir?\n\nMüşteri Yorumları:\n"""\n{reviews}\n"""\n\nTema:',
        temperature=0,
        max_tokens=64,
        top_p=1,
        frequency_penalty=0,
        presence_penalty=0,
    )
    print(response["choices"][0]["text"].replace("\n", ""))
    sample_cluster_rows = df[df.Cluster == i].sample(rev_per_cluster, random_state=42)
    for j in range(rev_per_cluster):
        print(sample_cluster_rows.Score.values[j], end=", ")
        print(sample_cluster_rows.Summary.values[j], end=":   ")
        print(sample_cluster_rows.Text.str[:70].values[j])
        print("-" * 100)
```

OpenAI davinci, her bir kümenin teması için ilginç bilgiler üretiyor:

Küme 0 Teması:  Tüm yorumlar pozitiftir ve çay kalitesini tartışmaktadır.
5, breakfast tea:   Gece için bu decaf çaya geçiyoruz ve harika bir çay içiyoruz ve hiç uyku
5, It is awesome.:   Partnerim çayı çok seviyor ve o zamandan beri çok daha iyi hissediyor
4, Chike!:   Bu sabah turuncu ve buzlu kahveyi denedim ve gerçekten beğendim
5, FAVORITE tea...:   Lipton en iyi French Vanilla çayını yapıyor... Başkalarını denedim ve bu
5, Twinings---a good cup of tea:   Yıllardır Twining's çayını içiyorum. İngiltere'de üretilirdi.

# Kod Açıklaması

1. `import openai`: OpenAI kütüphanesini içe aktarır.
2. `rev_per_cluster = 5`: Her bir küme için seçilecek inceleme sayısını belirler.
3. `for i in range(n_clusters):`: Küme sayısı kadar döngü oluşturur.
4. `print(f"Küme {i} Teması:", end=" ")`: Küme numarasını ve temasını yazdırır.
5. `reviews = "\n".join(...)`: Seçilen incelemeleri birleştirir ve `reviews` değişkenine atar.
   - `df[df.Cluster == i]`: i. kümeye ait satırları seçer.
   - `.combined.str.replace("Title: ", "")`: "Title: " ifadesini boşlukla değiştirir.
   - `.str.replace("\n\nContent: ", ":  ")`: "\n\nContent: " ifadesini ":  " ile değiştirir.
   - `.sample(rev_per_cluster, random_state=42)`: Rastgele `rev_per_cluster` kadar örnek seçer.
   - `.values`: Seçilen değerleri döndürür.
6. `response = openai.Completion.create(...)`: OpenAI'den tamamlama görevi oluşturur.
   - `engine="davinci-002"`: Kullanılacak modeli belirler.
   - `prompt=...`: Giriş metnini belirler.
   - `temperature=0`: Çıktının yaratıcılığını belirler (0: daha deterministik).
   - `max_tokens=64`: Çıktının maksimum uzunluğunu belirler.
   - `top_p=1`: Çıktının olasılık dağılımını belirler.
   - `frequency_penalty=0` ve `presence_penalty=0`: Tekrarları cezalandırma parametreleridir.
7. `print(response["choices"][0]["text"].replace("\n", ""))`: OpenAI'den gelen yanıtı yazdırır.
8. `sample_cluster_rows = df[df.Cluster == i].sample(rev_per_cluster, random_state=42)`: i. kümeden örnek satırları seçer.
9. İç içe döngüde:
   - `print(sample_cluster_rows.Score.values[j], end=", ")`: Seçilen satırın puanını yazdırır.
   - `print(sample_cluster_rows.Summary.values[j], end=":   ")`: Seçilen satırın özetini yazdırır.
   - `print(sample_cluster_rows.Text.str[:70].values[j])`: Seçilen satırın metninin ilk 70 karakterini yazdırır.
   - `print("-" * 100)`: Ayırıcı çizgi yazdırır.

Büyük veri kümelerindeki müşteri yorumlarını anlamanın pazarlama potansiyeli çok büyüktür! Yenilikçi arama sistemlerinden geçtik. Yolculuğumuzu özetleyelim ve bir sonraki maceraya geçelim!

---

