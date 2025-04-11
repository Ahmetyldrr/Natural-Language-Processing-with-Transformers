# FFN Alt Katmanının Yapısı ve Transformer Çıktısı

FFN alt katmanı, kodlayıcı yığınının FFN'si ile aynı yapıya sahiptir. FFN'nin katman normalizasyon sonrası çalışması, kodlayıcı yığınının katman normalizasyonu olarak işlev görür. Transformer, her seferinde yalnızca bir öğe olan bir çıktı dizisi üretir: Çıktı dizisi = (y1, y2, ... yn)

# Doğrusal Katman ve Çıktı Üretimi

Doğrusal katman, modele göre değişen ancak standart yönteme dayanan doğrusal bir işlevle bir çıktı dizisi üretir: y = w * x + b. w ve b öğrenilen parametrelerdir. Doğrusal katman, böylece bir softmax işlevinin muhtemel bir öğeye dönüştüreceği bir dizinin sonraki muhtemel öğelerini üretecektir.

# Kod Çözücü Katmanının Çalışması

Kod çözücü katmanı, kodlayıcı katmanı gibi, l katmanından l + 1 katmanına kadar, N = 6 katmanlı transformer yığınının üst katmanına kadar ilerleyecektir. Kod çözücünün üst katmanında, Transformer, modelin çıktılarını tahminin ham logitlerini üretmek için sözlüğün boyutuna eşleyecek olan çıktı katmanına ulaşacaktır.

# Çıktının İşlenmesi

Çıktının ham logitleri bir softmax işlevinden geçebilir, elde edilen değerleri sözlükteki tokenlere uygulayabilir ve istenen görev için en iyi muhtemel tokeni seçebilir. Veya, Bölüm 1'in "Bir Token'den Yapay Zeka Devrimine" bölümünde gösterildiği gibi, boru hattı bir API'den diğerine değişen örnekleme işlevleri uygulayabilir.

# Transformer'ın Eğitimi ve Performansı

Şimdi Transformer'ın nasıl eğitildiğini ve elde ettiği performansı görelim.

Python kodu bulunmamaktadır, eğer bir kod örneği istiyorsanız lütfen belirtiniz.

---

