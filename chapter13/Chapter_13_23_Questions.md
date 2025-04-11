# T5 Modelleri Hakkında Doğru/Yanlış Soruları

Aşağıdaki İngilizce paragrafın birebir Türkçe çevirisi yapılmıştır.

T5 modelleri sadece BERT modelleri gibi kodlayıcı (encoder) yığınlarına sahiptir. (Doğru/Yanlış)
T5 modelleri hem kodlayıcı (encoder) hem de çözücü (decoder) yığınlarına sahiptir. (Doğru/Yanlış)
T5 modelleri mutlak pozisyonel kodlama yerine göreli pozisyonel kodlama kullanır. (Doğru/Yanlış)
Metin-metin (text-to-text) modelleri sadece özetleme için tasarlanmıştır. (Doğru/Yanlış)
Metin-metin modelleri, NLP görevini belirleyen bir önek (prefix) girişi dizisine uygular. (Doğru/Yanlış)
T5 modelleri her görev için özel hiperparametreler gerektirir. (Doğru/Yanlış)
Metin-metin modellerinin avantajlarından biri, tüm NLP görevleri için aynı hiperparametreleri kullanmasıdır. (Doğru/Yanlış)
T5 transformer'ları bir ileri beslemeli ağ (feedforward network) içermez. (Doğru/Yanlış)
Hugging Face, transformer'ları uygulamasını kolaylaştıran bir çerçevedir. (Doğru/Yanlış)
OpenAI'ın transformer modelleri özetleme görevleri için en iyisidir. (Doğru/Yanlış)

Bu sorulara Python kodları ile cevap aramıyoruz, sadece verilen İngilizce metnin birebir Türkçe çevirisini yapıyoruz.

Eğer bu sorulara cevap arıyor olsaydık, aşağıdaki gibi bir Python kodu kullanabilirdik:

```python
# Doğru/Yanlış sorularını cevaplamak için bir fonksiyon
def cevapla(soru):
    cevaplar = {
        "T5 modelleri sadece BERT modelleri gibi kodlayıcı (encoder) yığınlarına sahiptir.": False,
        "T5 modelleri hem kodlayıcı (encoder) hem de çözücü (decoder) yığınlarına sahiptir.": True,
        "T5 modelleri mutlak pozisyonel kodlama yerine göreli pozisyonel kodlama kullanır.": True,
        "Metin-metin (text-to-text) modelleri sadece özetleme için tasarlanmıştır.": False,
        "Metin-metin modelleri, NLP görevini belirleyen bir önek (prefix) girişi dizisine uygular.": True,
        "T5 modelleri her görev için özel hiperparametreler gerektirir.": False,
        "Metin-metin modellerinin avantajlarından biri, tüm NLP görevleri için aynı hiperparametreleri kullanmasıdır.": True,
        "T5 transformer'ları bir ileri beslemeli ağ (feedforward network) içermez.": False,
        "Hugging Face, transformer'ları uygulamasını kolaylaştıran bir çerçevedir.": True,
        "OpenAI'ın transformer modelleri özetleme görevleri için en iyisidir.": False  # Bu subjektif bir cevaptır
    }
    return cevaplar.get(soru, "Cevap bulunamadı")

# Örnek kullanım
sorular = [
    "T5 modelleri sadece BERT modelleri gibi kodlayıcı (encoder) yığınlarına sahiptir.",
    "T5 modelleri hem kodlayıcı (encoder) hem de çözücü (decoder) yığınlarına sahiptir.",
    "T5 modelleri mutlak pozisyonel kodlama yerine göreli pozisyonel kodlama kullanır.",
    "Metin-metin (text-to-text) modelleri sadece özetleme için tasarlanmıştır.",
    "Metin-metin modelleri, NLP görevini belirleyen bir önek (prefix) girişi dizisine uygular.",
    "T5 modelleri her görev için özel hiperparametreler gerektirir.",
    "Metin-metin modellerinin avantajlarından biri, tüm NLP görevleri için aynı hiperparametreleri kullanmasıdır.",
    "T5 transformer'ları bir ileri beslemeli ağ (feedforward network) içermez.",
    "Hugging Face, transformer'ları uygulamasını kolaylaştıran bir çerçevedir.",
    "OpenAI'ın transformer modelleri özetleme görevleri için en iyisidir."
]

for soru in sorular:
    print(f"Soru: {soru}")
    print(f"Cevap: {cevapla(soru)}")
    print("-" * 50)
```

Bu kod, her bir soru için önceden belirlenmiş cevapları içeren bir sözlük kullanır. Her soru için ilgili cevabı bu sözlükten alır ve yazdırır.

---

