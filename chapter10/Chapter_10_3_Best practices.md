# Raffel ve Ekibi (2019) Tarafından Tanımlanan T5 Transformer Modeli ve Ön İşleme

Raffel ve ark. (2019) standart bir metin-metin T5 transformer modeli tanımladılar. Ayrıca daha da ileri gittiler. Öncelikle ham verileri ön işlemeden kullanma mitini yıkmaya katkıda bulundular. Veri ön işleme, eğitim süresini azaltır. Örneğin, Common Crawl, web kazıma yoluyla elde edilen etiketlenmemiş metin içerir. Veri kümesinden metin olmayan içerik ve biçimlendirme kaldırılmıştır. Ancak, Google T5 ekibi, Common Crawl aracılığıyla elde edilen metinlerin çoğunun doğal dil veya İngilizce düzeyine ulaşmadığını tespit etti. Bu nedenle, veri kümelerinin kullanılmadan önce temizlenmesi gerektiğine karar verdiler.

Raffel ve ark. (2019) tarafından yapılan önerileri alacağız ve ön işleme ve kalite kontrol aşamalarına kurumsal kalite kontrol en iyi uygulamalarını uygulayacağız. Uygulanacak birçok kural arasında, açıklanan örnekler, kabul edilebilir gerçek hayat proje veri kümeleri elde etmek için gereken muazzam çalışmayı gösterir. Kalite kontrol, bir transformer'ı eğitirken ön işleme aşamasına (Adım 1) ve transformer üretimde olduğunda (Adım 2) kalite kontrolüne ayrılır. Üçüncü bir aşama (Adım 3) ise keskin teknoloji için zorunlu hale gelmiştir: Sürekli İnsan Kalite Kontrolü. Ön işleme aşamasının bazı ana yönlerine bakalım.

Python kodu bulunmamaktadır, bu nedenle satır satır açıklama yapılmamıştır. Çeviri tamamen birebir yapılmıştır.

---

