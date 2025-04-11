# Orijinal Transformer Modelinin Mimarisine Başlarken
2. Bölüm'de, Orijinal Transformer Modelinin mimarisinin yapı taşlarını tanımladık. Orijinal Transformer'ı LEGO ® tuğlalarıyla inşa edilmiş bir model olarak düşünün. İnşaat seti, kodlayıcılar, kod çözücüler, gömme katmanları, pozisyonel kodlama yöntemleri, çoklu baş dikkat katmanları, maskeli çoklu baş dikkat katmanları, katman normalizasyonu sonrası, ileri beslemeli alt katmanlar ve doğrusal çıktı katmanları gibi tuğlalar içerir. Tuğlalar çeşitli boyut ve şekillerde gelir. Sonuç olarak, aynı yapı taşlarını kullanarak her türlü modeli inşa etmek için saatler harcayabilirsiniz! Bazı yapılar sadece bazı tuğlaları gerektirir. Diğer yapılar, LEGO ® bileşenleri kullanılarak inşa edilmiş bir model için ek tuğlalar elde ettiğimizde olduğu gibi, yeni bir parça ekler. BERT, transformer modellerine çift yönlü dikkat ekler. Çift yönlü dikkat, Orijinal Transformer modelinde birçok başka değişikliği gerektirir.

Biz, 2. Bölüm'de, Orijinal Transformer Modelinin mimarisinin yapı taşlarını anlatmayacağız. Transformerların yapı taşlarının bir yönünü gözden geçirmek için istediğiniz zaman 2. Bölüm'e başvurabilirsiniz. Bunun yerine, bu bölüm BERT modellerinin özel yönlerine odaklanacaktır. Devlin ve ekibi (2018) tarafından tasarlanan evrimleri, kodlayıcı yığınına odaklanarak açıklayacağız. Öncelikle kodlayıcı yığınına, ardından ön eğitim girdi ortamının hazırlanmasına bakacağız. Daha sonra BERT'in iki aşamalı çerçevesini açıklayacağız: ön eğitim ve ince ayar. Öncelikle kodlayıcı yığınına bakalım.

Python kodu bulunmamaktadır, bu nedenle satır satır açıklama gerekmemektedir. Yukarıdaki çeviri birebir yapılmıştır.

---

