# Bölüm Çevirisi

Bu bölümde, önce transformer mimarilerinin ortaya çıkarabileceği akıllara durgunluk veren uzun mesafeli bağımlılıkları inceleyerek başladık. Transformerlar, yazılı ve sözlü dizileri, Doğal Dil Anlama (NLU) tarihinde hiç olmadığı kadar anlamlı temsillere dönüştürebilir. Bu iki boyut, dönüşümün genişlemesi ve uygulamanın basitleştirilmesi, yapay zekayı daha önce görülmemiş bir seviyeye taşıyor. Dönüşüm problemlerinden ve dizi modellemeden RNN'leri, LSTM'leri ve CNN'leri kaldırarak Transformer mimarisini oluşturma cesur yaklaşımını keşfettik. Kodlayıcı ve kod çözücünün standartlaştırılmış boyutlarının simetrik tasarımı, bir alt katmandan diğerine geçişi neredeyse sorunsuz hale getirir. Tekrarlayan ağ modellerini kaldırmaya ek olarak, transformerların eğitme süresini azaltan paralel katmanlar tanıttığını gördük. Ayrıca, pozisyonel kodlama ve maskeli çoklu dikkat gibi diğer yenilikleri keşfettik. Esnek, Orijinal Transformer mimarisi, daha güçlü dönüşüm problemleri ve dil modellemesi için yol açan diğer birçok yenilikçi varyasyon için temel sağlar. Orijinal modelin birçok varyantını tanımlarken, sonraki bölümlerde Transformer'ın mimarisinin bazı yönlerine daha derinlemesine gireceğiz. Transformer'ın gelişi, kullanıma hazır yapay zeka modellerinin yeni bir neslinin başlangıcını işaret ediyor. Örneğin, Hugging Face ve Google Brain, birkaç satır kodla yapay zekayı kolayca uygulayabilir hale getiriyor. Sonraki bölüme devam etmeden önce, Orijinal Transformer'ın mimarisinin oluşturduğu paradigma değişiminin ayrıntılarını kavradığınızdan emin olun. Daha sonra herhangi bir mevcut ve gelecekteki transformer modeliyle yüzleşebileceksiniz. Bu bölümde, Orijinal Transformer'ın mimarisine daldık. Şimdi, neler yapabileceklerini göreceğiz. Bölüm 3'te, "Emergent vs. Downstream Görevleri: Transformerların Görünmeyen Derinlikleri", transformer modellerinin gerçekleştirebileceği geniş görev yelpazesini keşfedeceğiz.

# Python Kodları Yok

Bu metinde python kodları bulunmamaktadır. 

Eğer kod içeriyor olsaydı, her bir satırın açıklaması ayrı ayrı verilirdi. Örneğin:

```python
# örnek bir python kodu
def topla(a, b):
    return a + b  # bu satır a ve b sayılarını toplar

sonuc = topla(3, 5)  # bu satır topla fonksiyonunu çağırır
print(sonuc)  # bu satır sonucu yazdırır
```

---

