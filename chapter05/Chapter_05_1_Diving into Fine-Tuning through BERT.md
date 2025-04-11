# 5. Bölüm: BERT Modelinin İncelenmesi ve İnce Ayarlanması

3. Bölüm'de, "Emergent vs Downstream Tasks: The Unseen Depths of Transformers", önceden eğitilmiş modeller aracılığıyla verimli bir şekilde gerçekleştirilebilecek görevleri inceledik. Ancak bazı durumlarda, önceden eğitilmiş bir model istenen çıktıları üretmeyebilir. 6. Bölüm'de, "Pretraining a Transformer from Scratch through RoBERTa", sıfırdan bir modelin önceden nasıl eğitileceğini göreceğiz. Ancak, bir modelin önceden eğitilmesi büyük miktarda makine, veri ve insan kaynağı gerektirebilir. Alternatif olarak, bir transformer modelinin ince ayarlanması olabilir. Bu bölüm, önceden eğitilmiş bir Hugging Face BERT modeli aracılığıyla transformer modellerinin ince ayarlanmasını inceleyecektir. Bölümün sonunda, GPT, T5, RoBERTa ve daha fazlası gibi diğer Hugging Face modellerini ince ayarlayabilmelisiniz. Bölüm iki kısma ayrılmıştır. Öncelikle BERT modellerinin mimarisini inceleyeceğiz. Ardından, BERT aracılığıyla bir transformer modelinin ince ayarlanmasını inceleyeceğiz.

## BERT Mimarisini İnceleme

Öncelikle, Transformers'den (BERT) Bidirectional Encoder Representations'ın mimarisini inceleyeceğiz. BERT, Transformer'ın encoder bloklarını yenilikçi bir şekilde kullanır ve decoder yığınıını kullanmaz. BERT, Transformer yapı taşına yeni bir parça ekledi: çift yönlü çoklu baş dikkat alt katmanı. İnsanlar bir cümleyi anlamakta zorlandığında, sadece geçmiş kelimelere bakmazlar. BERT, bizim gibi, bir cümledeki tüm kelimelere aynı anda bakar.

## BERT Modelinin İnce Ayarlanması

Ardından, üçüncü bir tarafça eğitilmiş ve Hugging Face'e yüklenmiş bir BERT modelini ince ayarlayacağız. Bu, transformerların önceden eğitilebileceğini gösterir. Örneğin, önceden eğitilmiş bir BERT, birkaç NLP görevi üzerinde ince ayarlanabilir. Hugging Face modüllerini kullanarak bir transformerın ince ayarlanması deneyimini yaşayacağız, ipywidgets ile eğitilmiş modelimizle etkileşim kurmak için bir arayüz oluşturma dahil.

Bu bölüm aşağıdaki konuları kapsar:
- BERT mimarisi
- Transformerların encoder yığını ve çift yönlü dikkat
- Kabul edilebilirlik yargılama görevi için ince ayar süreci
- Eğitim verileri, etiketler ve BERT tokenları oluşturma
- BERT tokenlaştırıcı ve dikkat maskeleri ile eğitim verilerini işleme
- Verileri eğitim ve doğrulama kümelerine ayırma
- Hugging Face BERT uncased base modelini kurma
- Parametreleri gruplama
- Hiperparametreleri ayarlama
- Eğitim döngüsünü çalıştırma
- Eğitim sonrası değerlendirme
- Modelle etkileşim kurmak için bir Python arayüzü oluşturma

Bu son teknoloji alanındaki tüm yenilikler ve kütüphane güncellemeleri ile paketler ve modeller düzenli olarak değişmektedir. Lütfen en son kurulum ve kod örnekleri için GitHub deposuna gidin: https://github.com/Denis2054/Transformers-for-NLP-and-Computer-Vision-3rd-Edition/tree/main/Chapter05 . Bu veya herhangi bir bölümdeki kodu çalıştırmakta zorluk yaşıyorsanız, Discord topluluğumuza bir mesaj gönderin (https://www.packt.link/Transformers).

İlk adımımız BERT modelinin arka planını incelemek olacaktır.

Python kodları ile ilgili açıklama istenmediğinden, sadece çeviri sağlandı. İleride kodlarla ilgili yardım isterseniz, lütfen ilgili Python kodlarını paylaşın.

---

