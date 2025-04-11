# Kaynaklar

Aşağıda listelenen kaynakların birebir Türkçe çevirisi aşağıda verilmiştir.

## Kaynak Listesi

* Barham et al. , 2022, Pathways: Asynchronous Distributed Dataflow for ML : https://arxiv.org/abs/2203.12533
* Chowdhery et al. , 2022, PaLM: Scaling Language Modeling with Pathways: https://arxiv.org/pdf/2204.02311.pdf
* Anil et al. , 2023, PaLM 2 Technical Report: https://arxiv.org/abs/2305.10403
* Google Cloud Vertex AI documentation: https://cloud.google.com/vertex-ai/docs/generative-ai/learn/overview

## Çeviri

Barham ve diğerleri, 2022, Pathways: ML için Asenkron Dağıtılmış Veri Akışı: https://arxiv.org/abs/2203.12533  
Chowdhery ve diğerleri, 2022, PaLM: Pathways ile Dil Modellemeyi Ölçeklendirme: https://arxiv.org/pdf/2204.02311.pdf  
Anil ve diğerleri, 2023, PaLM 2 Teknik Raporu: https://arxiv.org/abs/2305.10403  
Google Cloud Vertex AI belgeleri: https://cloud.google.com/vertex-ai/docs/generative-ai/learn/overview

Burada Python kodu bulunmamaktadır, sadece metin çevirisi yapılmıştır.

Eğer kaynak listesini işlemek için bir Python kodu yazmak isteseydik, aşağıdaki gibi bir kod yazabilirdik:

```python
# Kaynak listesi
kaynaklar = [
    {"ad": "Barham et al.", "yil": 2022, "baslik": "Pathways: Asynchronous Distributed Dataflow for ML", "link": "https://arxiv.org/abs/2203.12533"},
    {"ad": "Chowdhery et al.", "yil": 2022, "baslik": "PaLM: Scaling Language Modeling with Pathways", "link": "https://arxiv.org/pdf/2204.02311.pdf"},
    {"ad": "Anil et al.", "yil": 2023, "baslik": "PaLM 2 Technical Report", "link": "https://arxiv.org/abs/2305.10403"},
    {"ad": "Google Cloud Vertex AI documentation", "yil": None, "baslik": None, "link": "https://cloud.google.com/vertex-ai/docs/generative-ai/learn/overview"}
]

# Çeviri fonksiyonu
def cevir(kaynak):
    ad = kaynak["ad"]
    yil = kaynak["yil"]
    baslik = kaynak["baslik"]
    link = kaynak["link"]
    
    if yil and baslik:
        return f"{ad}, {yil}, {baslik}: {link}"
    else:
        return f"{ad}: {link}"

# Çeviri işlemi
ceviriler = [cevir(kaynak) for kaynak in kaynaklar]

# Çevirilerin yazdırılması
for ceviri in ceviriler:
    print(ceviri)
```

Bu kod, kaynak listesini alır ve her bir kaynağı belirtilen formatta çevirir. Çeviri işlemi `cevir` fonksiyonu içinde yapılır.

---

