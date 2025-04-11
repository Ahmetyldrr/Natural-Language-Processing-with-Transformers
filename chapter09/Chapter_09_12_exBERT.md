# Bölüm Çevirisi

Bu bölümde, bert-base-uncased modelinin dikkat katmanının iç işleyişini nispeten düşük bir seviyede analiz ettik. Bert-base-uncased modelinin iç işleyişini exBERT ile de inceleyebilirsiniz. Bu araç, Hoover ve diğerleri (2021) tarafından geliştirilen "exBERT: Transformers Modellerinde Öğrenilen Gösterimleri Keşfetmek için Görsel Analiz Araçları"ndan türetilmiştir. Hugging Face, exBERT için kullanıcı dostu bir arayüz uyguladı. Bert-base-uncased modelinin dikkat başlıklarını yüksek bir seviyede görselleştirebilirsiniz. Bu yüksek seviyeli arayüz, Şekil 9.10'da gösterildiği gibi iyi tasarlanmış ve sezgiseldir:

# Şekil 9.10: Bert-base-uncased modelinin dikkat başlıklarının görselleştirilmesi

Katmanları, başlıkları ve diğer sezgisel seçenekleri seçebilirsiniz. Hugging Face exBERT ile diğer modelleri de keşfedebilirsiniz: https://huggingface.co/spaces/simon-clmtd/exbert. Sunucu her zaman kullanılabilir olmayabilir, ancak sistem keşfetmeye değer. Şimdi Hugging Face transformer'lar için heyecan verici SHAP açıklayıcısını keşfedeceğiz.

Python kodları bulunmamaktadır, sadece bir ingilizce paragraf çevirisi yapılmıştır. 

Eğer python kodları olsaydı, kodların her bir satırını `# Satır Açıklaması` şeklinde açıklardım. Örneğin:

```python
# Örnek bir python kodu
x = 5  # x değişkenine 5 değerini atıyoruz
y = x * 2  # x değişkenini 2 ile çarpıp y değişkenine atıyoruz
print(y)  # y değişkenini yazdırıyoruz
```

---

