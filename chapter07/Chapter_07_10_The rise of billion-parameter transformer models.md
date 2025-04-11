# Trafo Modellerinin Hızlı Gelişimi

Trafo modellerinin NLP görevleri için eğitilen küçük modellerden ince ayar gerektirmeyen modellere geçiş hızı şaşırtıcıdır. Vaswani ve diğerleri (2017) BLEU görevlerinde CNN ve RNN'leri geride bırakan Orijinal Trafo'yu tanıttı. Radford ve diğerleri (2018) ince ayar ile alt görevleri gerçekleştirebilen GPT modelini tanıttı. Devlin ve diğerleri (2019) BERT modeli ile ince ayarı mükemmelleştirdi. Radford ve diğerleri (2019) GPT-2 modelleri ile daha da ileri gitti. Brown ve diğerleri (2020) ince ayar gerektirmeyen GPT-3 sıfır-shot yaklaşımını tanımladı! Aynı zamanda, Wang ve diğerleri (2019) NLP modellerini kıyaslamak için GLUE'yi oluşturdu. Ancak trafo modelleri o kadar hızlı gelişti ki insan bazlarını geride bıraktı! Wang ve diğerleri (2019 2) hızla SuperGLUE'yi oluşturdu, insan bazlarını çok daha yüksek ayarladı ve NLU/NLP görevlerini daha zor hale getirdi. Trafo modelleri hızla ilerliyor ve bazıları yazının yazıldığı sırada SuperGLUE liderlik tablosunda İnsan Bazlarını zaten geride bıraktı. Bu nasıl bu kadar hızlı oldu? Bu evrimin nasıl gerçekleştiğini anlamak için modellerin boyutlarına bir göz atacağız.

Python kodları bulunmamaktadır, ancak metinde geçen bazı önemli noktaları Python kodları ile ilişkilendirebiliriz. Örneğin, metinde geçen bazı önemli makalelere ve onların yılına ilişkin bir liste oluşturmak için aşağıdaki Python kodunu kullanabiliriz:

```python
# Makalelerin listesi
makaleler = [
    {"yazar": "Vaswani et al.", "yıl": 2017, "makale": "Original Transformer"},
    {"yazar": "Radford et al.", "yıl": 2018, "makale": "GPT"},
    {"yazar": "Devlin et al.", "yıl": 2019, "makale": "BERT"},
    {"yazar": "Radford et al.", "yıl": 2019, "makale": "GPT-2"},
    {"yazar": "Brown et al.", "yıl": 2020, "makale": "GPT-3 zero-shot"},
    {"yazar": "Wang et al.", "yıl": 2019, "makale": "GLUE"},
    {"yazar": "Wang et al.", "yıl": 2019, "makale": "SuperGLUE"}
]

# Makaleleri yıla göre sıralama
makaleler.sort(key=lambda x: x["yıl"])

# Makaleleri yazdırma
for makale in makaleler:
    print(f'{makale["yazar"]} ({makale["yıl"]}) - {makale["makale"]}')
```

Bu kod, makalelerin listesini oluşturur, onları yıla göre sıralar ve daha sonra yazar, yıl ve makale adıyla birlikte yazdırır.

Satır satır açıklama:

1. `makaleler` listesi oluşturulur ve makalelere ilişkin bilgiler sözlükler halinde bu listeye eklenir.
2. `makaleler.sort(key=lambda x: x["yıl"])` satırı, makaleleri yıla göre sıralar. `lambda` fonksiyonu, her bir sözlük için "yıl" anahtarına karşılık gelen değeri döndürür.
3. `for` döngüsü, sıralanmış makaleleri yazar, yıl ve makale adıyla birlikte yazdırır.

---

