# Transformers ve Doğal Dil İşleme (NLP)

Transformers, son birkaç yılda, bir önceki neslin Doğal Dil İşleme (NLP) alanındaki ilerlemelerinden daha fazla ilerleme kaydetti. Eski NLP modelleri, Anlamsal Rol Etiketleme (SRL) çalıştırmadan önce bir dilin temel sözdizimini anlamak için eğitilirdi. NLP yazılımı, sözdizim ağaçları, kural tabanları ve ayrıştırıcılar içeriyordu. Bu tür sistemlerin performansı, sonsuz bağlamlara yol açan kelime kombinasyonlarının sayısıyla sınırlıydı. Shi ve Lin (2019), makalelerine ön sözdizimi ve sözcük eğitiminin atlanıp atlanamayacağını sorarak başladı. Bir sistem "sözdizimden bağımsız" hale gelebilir ve önceden tasarlanmış sözdizim ağaçlarına güvenmeden dili anlayabilir mi? BERT tabanlı bir model, klasik eğitim aşamalarından geçmeden SRL gerçekleştirebilir mi? Cevap evet! Shi ve Lin (2019), SRL'nin dizi etiketleme olarak kabul edilebileceğini ve standart bir girdi formatı sağlayabileceğini önerdi. O zamandan beri, OpenAI insan düzeyine yakın sözdizimden bağımsız SRL'ye ulaştı.

GPT-4, bir modeli SRL gerçekleştirmek için eğitmenin ötesine geçer, hatta sözdizimden bağımsız etiketleme yapar. GPT-4 ile ChatGPT, açıkça eğitilmemiş olsalar da SRL gerçekleştirebilir. GPT-4 ile ChatGPT, Bölüm 1'de gördüğümüz gibi, Üretken Yapay Zeka otoregresif Büyük Dil Modeli (LLM)'dir. Bu nedenle, GPT-4 stokastiktir; bir dizideki en olası tokenleri üretir, ancak her zaman kendini tekrar etmez. Bu evrimler, yapay zekada tamamen yeni bir zihniyetle bizi karşı karşıya getiriyor. GPT-4 sözdizimden bağımsızdır (kural tabanlarına güvenmez) ve stokastiktir (çoğu zaman kendini tekrar etmez).

## Paradigma Değişimi

Paradigma değişimi, AI'nın geleceğine kuantum sıçraması yapmaktır. Kendini tekrar eden veya her çalıştırma için tutarlı çıktı veren bir sistem aramayın. İlgiye bakın! Kritik soru, cevabın güvenilir olup olmadığını değerlendirmek için kalır, kendini tekrar edip etmediğine değil! ChatGPT'nin rastgele doğası, onu çekici ve insan benzeri yapan şeydir!

## Bu Bölümde Neler Öğreneceğiz?

- Görev tabanlı ve genel amaçlı modellerin (SRL dahil) karşılaştırılması
- Kendin yap ve geliştirme ile dağıtımın karşılaştırılması
- SRL'nin tanımlanması
- SRL için girdi formatının standartlaştırılması
- Temel örnekler üzerinde cümle etiketleme testi
- Karmaşık örnekler üzerinde SRL testi ve sonuçların açıklanması
- SRL'nin sınırlarına transformer modelini zorlamak ve nasıl yapıldığını açıklamak
- GPT-4 aracılığıyla temel ve karmaşık SRL örneklerini çalıştırmak için bir not defteri oluşturma

## Kod Örnekleri ve Kurulum

Bu alandaki tüm yenilikler ve kütüphane güncellemeleri ile paketler ve modeller düzenli olarak değişmektedir. Lütfen en son kurulum ve kod örnekleri için GitHub deposuna gidin: https://github.com/Denis2054/Transformers-for-NLP-and-Computer-Vision-3rd-Edition/tree/main/Chapter12 . Bu veya herhangi bir bölümdeki kodu çalıştırırken sorun yaşıyorsanız, Discord topluluğumuza bir mesaj gönderin: https://www.packt.link/Transformers .

İlk adımımız, en son SRL ile başlamak olacak.

Python kodları bulunmamaktadır, ancak ileriki adımlarda Google Colab not defteri kurulumu ve OpenAI kurulumu yapılacaktır. Bu adımların açıklamaları aşağıda verilmiştir:

1. **Google Colab Not Defteri Kurulumu**: Bu adımda, Google Colab'de bir not defteri oluşturulacak ve temel ve karmaşık SRL örneklerini çalıştırmak için GPT-4 ile kullanılacaktır.
2. **OpenAI Kurulumu**: Bu adımda, OpenAI kütüphanesi kurulacak ve GPT-4 modeline ne beklendiği açıklanacaktır.

Bu adımların her biri, SRL'nin sınırlarını zorlamak ve transformer modelinin gerçek hayattaki uygulamalarını gerçekçi ve pragmatik tutmak için önemli olacaktır.

---

