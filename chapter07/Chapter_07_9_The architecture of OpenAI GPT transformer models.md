# 2020 Yılında OpenAI GPT-3 Modelinin Eğitimi

2020 yılında Brown ve ekibi (2020), 175 milyar parametre içeren ve Common Crawl verilerinden çıkarılan 400 milyar byte-pair-encoded token gibi devasa veri kümeleri üzerinde eğitilen bir OpenAI GPT-3 modelinin eğitimini anlattı. OpenAI, eğitimi 285.000 CPU ve 10.000 GPU içeren bir Microsoft Azure süper bilgisayarında gerçekleştirdi. OpenAI'ın GPT-3 modellerinin makine zekası ve süper bilgisayarları, Brown ve ekibi (2020) tarafından sıfır-shot deneylerine yol açtı. Fikir, eğitilen bir modeli parametreleri daha fazla eğitmeden downstream görevler için kullanmaktı. Hedef, eğitilen bir modelin doğrudan çoklu görev üretimine API ile girmesi ve hatta eğitilmediği görevleri bile gerçekleştirebilmesiydi. Suprahuman bulut AI modelleri çağı doğdu. OpenAI'ın API'si yüksek seviyeli yazılım becerileri veya AI bilgisi gerektirmez.

# Suprahuman Teriminin Kullanımı

GPT-3 ve GPT-4 modeli (ve yakında daha güçlü olanlar) birçok görevi en azından bir insan kadar iyi bir şekilde gerçekleştirebilmektedir. Şu an için, sihri takdir etmek için GPT modellerinin nasıl inşa edildiğini ve çalıştırıldığını anlamak önemlidir. Transformer'lar 2017 sonu ile 2020 ilk yarısı arasındaki üç yıldan kısa sürede eğitimden ince ayara ve nihayetinde sıfır-shot modellere geçtiler. Sıfır-shot GPT-3 transformer modeli ince ayar gerektirmez. Eğitilen model parametreleri downstream çoklu görevler için güncellenmez, bu da NLP/NLU görevleri için yeni bir çağın kapılarını açar.

# OpenAI GPT Modellerinin Gelişimi

Bu bölümde, önce OpenAI ekibinin GPT modellerini tasarlamak için motivasyonunu öğreneceğiz. OpenAI ekibinin oluşturma sürecini inceleyerek başlayacağız.

Python kodları bulunmamaktadır, sadece metin çevirisi yapılmıştır.

---

