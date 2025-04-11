# Bommansani ve diğerleri, 2021, Temel Modellerin Fırsatları ve Riskleri Üzerine
Aşağıdaki metin birebir çevrilmiştir.

Bommansani ve diğerleri, 2021, Temel Modellerin Fırsatları ve Riskleri Üzerine : https://arxiv.org/abs/2108.07258  
Bommansani ve diğerleri, 2023, Ekosistem Grafikleri: Temel Modellerin Sosyal Ayak İzi, https://arxiv.org/abs/2303.15772  
Vaswani ve diğerleri, 2017, İhtiyacınız Olan Tek Şey Dikkat : https://arxiv.org/abs/1706.03762  
Chen ve diğerleri, 2021, Kod Üzerinde Eğitilen Büyük Dil Modellerinin Değerlendirilmesi : https://arxiv.org/abs/2107.03374  
Microsoft AI: https://innovation.microsoft.com/en-us/ai-at-scale  
OpenAI: https://openai.com/  
Google AI: https://ai.google/  
Google Trax: https://github.com/google/trax  
AllenNLP: https://allennlp.org/  
Hugging Face: https://huggingface.co/  
Google Cloud TPU: https://cloud.google.com/tpu/docs/intro-to-tpu

Bu metin bir dizi akademik makaleye ve yapay zeka ile ilgili bazı şirketlerin ve projelerin web sayfalarına atıfta bulunmaktadır. 

Python kodu bulunmamaktadır. 

Eğer bu referansları ayrıştırmak isteseydik basit bir python kodu yazabilirdik. Aşağıda örnek bir kod verilmiştir.

```python
# Referansları içeren metin
referanslar = """
Bommansani et al. , 2021, On the Opportunities and Risks of Foundation Models : https://arxiv.org/abs/2108.07258 Bommansani et al. , 2023, Ecosystem Graphs: The Social Footprint of Foundation Models, https://arxiv.org/abs/2303.15772 Vaswani et al. , 2017, Attention is All You Need : https://arxiv.org/abs/1706.03762 Chen et al. , 2021, Evaluating Large Language Models Trained on Code : https://arxiv.org/abs/2107.03374 Microsoft AI: https://innovation.microsoft.com/en-us/ai-at-scale OpenAI: https://openai.com/ Google AI: https://ai.google/ Google Trax: https://github.com/google/trax AllenNLP: https://allennlp.org/ Hugging Face: https://huggingface.co/ Google Cloud TPU: https://cloud.google.com/tpu/docs/intro-to-tpu
"""

# Referansları ayırma
referans_listesi = referanslar.strip().split()

# Referansları işleme
sonuc = []
gecici = []
for kelime in referans_listesi:
    if kelime.startswith("http"):
        gecici.append(kelime)
        sonuc.append(" ".join(gecici))
        gecici = []
    else:
        gecici.append(kelime)

# Sonuçları yazdırma
for indeks, referans in enumerate(sonuc):
    print(f"# Referans {indeks+1}: {referans}")
```

Bu kod, referansları içeren metni satır satır işler ve her bir referansı ayrı bir şekilde ele alır. Referansları ayırırken `http` ile başlayan kelimeleri baz alarak ayırma işlemini gerçekleştirir. 

Örnek çıktı:

```
# Referans 1: Bommansani et al. , 2021, On the Opportunities and Risks of Foundation Models : https://arxiv.org/abs/2108.07258
# Referans 2: Bommansani et al. , 2023, Ecosystem Graphs: The Social Footprint of Foundation Models, https://arxiv.org/abs/2303.15772
# Referans 3: Vaswani et al. , 2017, Attention is All You Need : https://arxiv.org/abs/1706.03762
# Referans 4: Chen et al. , 2021, Evaluating Large Language Models Trained on Code : https://arxiv.org/abs/2107.03374
# Referans 5: Microsoft AI: https://innovation.microsoft.com/en-us/ai-at-scale
# Referans 6: OpenAI: https://openai.com/
# Referans 7: Google AI: https://ai.google/
# Referans 8: Google Trax: https://github.com/google/trax
# Referans 9: AllenNLP: https://allennlp.org/
# Referans 10: Hugging Face: https://huggingface.co/
# Referans 11: Google Cloud TPU: https://cloud.google.com/tpu/docs/intro-to-tpu
```

---

