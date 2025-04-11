# Vaswani ve Takımı'nın Başarıları

Vaswani ve takımı (2017) Orijinal Transformer'ın başarılarını Statistical Machine Çalıştayında (WMT-06) 2014 İngilizce-Almanca çeviri görevi ve WMT 2014 İngilizce-Fransızca çeviri görevi üzerinde sundu. Orijinal Transformer state-of-the-art bir BLEU skoru elde etti. BLEU, bu bölümün "BLEU ile Makine Çevirisini Değerlendirme" kısmında açıklanacaktır. Ancak, önce inceleyeceğimiz WMT veri setini ön işlemeden geçirmeliyiz.

Python kodları bulunmamaktadır, ancak çeviri aşağıdaki gibidir:

İngilizce paragraf:
```
Vaswani et al . (2017) presented the Original Transformer’s achievements in the Workshop on Statistical Machine ( WMT-06 ) 2014 English-to-German translation task and the WMT 2014 English-to-French translation task. The Original Transformer achieved a state-of-the-art BLEU score. BLEU will be described in the Evaluating machine translation with BLEU section of this chapter. However, we must begin by preprocessing the WMT dataset we will examine.
```

Türkçe çevirisi:
```
Vaswani ve takımı (2017) Orijinal Transformer'ın başarılarını Statistical Machine Çalıştayında (WMT-06) 2014 İngilizce-Almanca çeviri görevi ve WMT 2014 İngilizce-Fransızca çeviri görevi üzerinde sundu. Orijinal Transformer state-of-the-art bir BLEU skoru elde etti. BLEU, bu bölümün "BLEU ile Makine Çevirisini Değerlendirme" kısmında açıklanacaktır. Ancak, önce inceleyeceğimiz WMT veri setini ön işlemeden geçirmeliyiz.
```

Eğer bir python kodu olsaydı, onu satır satır açıklardım. Örneğin, eğer aşağıdaki gibi bir kod olsaydı:
```python
# Vaswani ve Takımı'nın Başarıları
ingilizce_paragraf = "Vaswani et al . (2017) presented the Original Transformer’s achievements in the Workshop on Statistical Machine ( WMT-06 ) 2014 English-to-German translation task and the WMT 2014 English-to-French translation task. The Original Transformer achieved a state-of-the-art BLEU score. BLEU will be described in the Evaluating machine translation with BLEU section of this chapter. However, we must begin by preprocessing the WMT dataset we will examine."

# Çeviri işlemi
turkce_cevirisi = ingilizce_paragraf.replace("Vaswani et al", "Vaswani ve takımı").replace("Original Transformer’s", "Orijinal Transformer'ın").replace("Workshop on Statistical Machine", "Statistical Machine Çalıştayında").replace("English-to-German", "İngilizce-Almanca").replace("English-to-French", "İngilizce-Fransızca").replace("state-of-the-art", "state-of-the-art").replace("BLEU score", "BLEU skoru").replace("Evaluating machine translation with BLEU", "BLEU ile Makine Çevirisini Değerlendirme").replace("However", "Ancak").replace("preprocessing", "ön işlemeden").replace("WMT dataset", "WMT veri setini")

# Çıktı
print(turkce_cevirisi)
```
Bu kodda:
1. `ingilizce_paragraf` değişkenine ingilizce paragraf atanır.
2. `turkce_cevirisi` değişkenine `ingilizce_paragraf`ın çevirisi atanır. Bu işlem `replace()` fonksiyonu ile yapılır. Bu fonksiyon, ilk parametre olarak aldığı stringi, ikinci parametre olarak aldığı string ile değiştirir.
3. `print(turkce_cevirisi)` ile türkçe çevirisi çıktı olarak verilir.

---

