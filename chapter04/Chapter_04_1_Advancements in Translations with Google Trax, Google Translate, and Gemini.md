# Transformers ile Makine Çevirisi

Transformers, birçok dilde kelime dizilerinin anlamını yakalama konusundaki benzersiz yetenekleri ile çeviriyi geliştirmiştir. Bu bölümde, bazı önemli çeviri kavramlarını inceleyeceğiz ve Google Trax, Google Translate ve Gemini'deki kapsamlarını keşfedeceğiz. İnsanlar, bir dilden diğerine bilgi aktarmada ustadır. Bir kelime dizisinin zihinsel bir temsilini kolayca hayal edebiliriz. Örneğin, birisi "Bahçemdeki çiçekler güzel" derse, çiçeklerle dolu bir bahçeyi kolayca görselleştirebiliriz. Bahçenin görüntülerini görürüz, ancak o bahçeyi hiç görmemiş olabiliriz. Hatta cıvıldayan kuşları ve çiçeklerin kokusunu bile hayal edebiliriz. Bir makine, sayısal temsillerle sıfırdan transdüksiyon öğrenmelidir. Tekrarlayan veya evrişimsel yaklaşımlar heyecan verici sonuçlar üretmiştir, ancak önemli Bilingual Evaluation Understudy (BLEU) çeviri değerlendirme puanlarına ulaşmamıştır. Çeviri, A dilinin B diline aktarılmasını gerektirir. Transformer modelinin kendi dikkat inovasyonu, makine zekasının analitik yeteneğini arttırır. Örneğin, A dilindeki bir dizi, B diline çevirmeye çalışmadan önce yeterince temsil edilir. Kendi dikkat, bir makinenin daha iyi BLEU puanları elde etmesi için gereken dil anlama düzeyini sağlar. 2017 yılında, çığır açan "Attention Is All You Need" Transformer, İngilizce-Almanca ve İngilizce-Fransızca çeviriler için en iyi sonuçları sergiledi. O zamandan beri, puanlar diğer transformers tarafından geliştirildi.

## Makine Çevirisini Tanımlama

Bu bölümde, makine çevirisini üç adımda inceleyeceğiz. Öncelikle makine çevirisinin ne olduğunu tanımlayacağız. Ardından, bir Workshop on Machine Translation (WMT) veri kümesini ön işleme tabi tutacağız. Son olarak, makine çevirilerini nasıl uygulayacağımızı göreceğiz. Bu bölüm, aşağıdaki konuları kapsar:
- Makine çevirisini tanımlama
- İnsan transdüksiyonları ve çevirileri
- Makine transdüksiyonları ve çevirileri
- Makine çevirilerini değerlendirme
- Bir WMT veri kümesini ön işleme tabi tutma
- BLEU ile makine çevirilerini değerlendirme
- Google Trax ile çeviriler
- Orijinal Transformer modelini oluşturma
- Bir cümleyi tokenleştirme
- Transformer'dan kod çözme
- Çeviriyi tokenleştirmeden çıkarma ve görüntüleme
- Google Translate ile çeviri
- Google Translate AJAX API Wrapper ile çeviri
- Gemini ile çeviri

Bu son teknoloji alanında yapılan yenilikler ve kütüphane güncellemeleri nedeniyle, paketler ve modeller düzenli olarak değişmektedir. Lütfen en son kurulum ve kod örnekleri için GitHub deposuna gidin: https://github.com/Denis2054/Transformers-for-NLP-and-Computer-Vision-3rd-Edition/tree/main/Chapter04 . Bu veya herhangi bir bölümdeki kodu çalıştırırken sorun yaşarsanız, Discord topluluğumuza bir mesaj gönderebilirsiniz (https://www.packt.link/Transformers). İlk adımımız makine çevirisini tanımlamak olacaktır.

Python kodları bulunmamaktadır, ancak ilerleyen kısımlarda kodlar eklenecek olursa, satır satır açıklama yapılacaktır.

---

