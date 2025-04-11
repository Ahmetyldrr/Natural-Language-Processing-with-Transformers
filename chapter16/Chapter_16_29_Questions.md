# Doğruluk Değerlendirmeleri

Aşağıdaki ifadelerin doğruluğunu değerlendiriniz.

DALL-E 2 görüntülere sınıflandırma yapar. (Doğru/Yanlış)
ViT görüntülere sınıflandırma yapar. (Doğru/Yanlış)
BERT başlangıçta görüntüler oluşturmak için tasarlandı. (Doğru/Yanlış)
CLIP bir görüntü kırpma uygulamasıdır. (Doğru/Yanlış)
BERT görüntülere tanımlama yapmak için CLIP'i kullanır. (Doğru/Yanlış)
DALL-E 3 API ile erişilemez. (Doğru/Yanlış)
Gradio bir transformer modelidir. (Doğru/Yanlış)
ViT, etiket listesinde olmayan görüntülere sınıflandırma yapabilir. (Doğru/Yanlış)
ViT yanıt vermek için bir ipucuna ihtiyaç duyar. (Doğru/Yanlış)
GPT-4V muhtemelen daha çok modlu bir sisteme dönüşecektir. (Doğru/Yanlış)

İfadelerin doğruluğunu değerlendirmek için ilgili alanlardaki bilgilere başvurmak gerekir.

Python kodu bulunmamaktadır, sadece verilen ingilizce paragrafın birebir türkçeye çevirisi yapılmıştır. 

Eğer doğruluğunu değerlendirmek isterseniz, her bir ifade için ayrı ayrı araştırma yapmanız gerekir.

Örnek bir python kodu ile değerlendirme yapmak istersek:

```python
# Doğruluk değerlendirmeleri için bir sözlük oluşturalım
degerlendirmeler = {
    "DALL-E 2 görüntülere sınıflandırma yapar.": False,
    "ViT görüntülere sınıflandırma yapar.": True,
    "BERT başlangıçta görüntüler oluşturmak için tasarlandı.": False,
    "CLIP bir görüntü kırpma uygulamasıdır.": False,
    "BERT görüntülere tanımlama yapmak için CLIP'i kullanır.": False,
    "DALL-E 3 API ile erişilemez.": True,
    "Gradio bir transformer modelidir.": False,
    "ViT, etiket listesinde olmayan görüntülere sınıflandırma yapabilir.": True,
    "ViT yanıt vermek için bir ipucuna ihtiyaç duyar.": False,
    "GPT-4V muhtemelen daha çok modlu bir sisteme dönüşecektir.": True
}

# Değerlendirmeleri yazdıralım
for ifade, deger in degerlendirmeler.items():
    if deger:
        print(f"{ifade} (Doğru)")
    else:
        print(f"{ifade} (Yanlış)")
```

Bu kod, doğruluğunu değerlendirdiğimiz ifadeleri bir sözlükte saklar ve daha sonra bu sözlüğü yazdırır. Doğruluk değerleri ilgili alanlardaki bilgilere göre belirlenmiştir.

---

