# İnce Ayar (Fine-Tuning) ve Uygulama Seçenekleri

İnce ayar, yanıtlar kabul edilebilir bir sonuç ürettiğinde veya istem tasarımı beklentileri karşılamadığında bir seçenek haline gelir. Ya da değil! Bölüm 11'de, İnce Ayar yerine LLM Gömme (Embeddings) Kullanımı'nda, OpenAI LLM Ada'nın gömme (embeddings) özelliklerinden yararlanarak gelişmiş istem mühendisliğinin iyi sonuçlar üretebildiğini gördük. Peki, ne yapmalıyız? Hazır bir modelle iyi istemler tasarlayarak istem tasarımı mı yapmalıyız? Bir gömme modeli ile istem mühendisliği mi yapmalıyız? Bir modeli ihtiyaçlarımıza göre ince ayar yaparak mı kullanmalıyız? Bu seçeneklerin her biri bir maliyete sahiptir. Bilgisayar bilimlerinde en iyi ampirik yöntem şudur: Güvenilir ve optimize edilmiş (hacim, kalite) bir değerlendirme veri setine güvenmek. Farklı modelleri ve yaklaşımları test etmek. Bu durumda, istem tasarımı, mühendisliği ve ince ayar yoluyla elde edilen çıktıları değerlendirmek. Riskleri ve maliyetleri değerlendirmek.

Tıpkı Amazon Web Services (AWS), Microsoft Azure, IBM Cloud ve diğerleri gibi, Google Cloud da bir bulut platformunda makine öğrenimi (ML) görevlerini gerçekleştirmek için sağlam ve basit bir yaklaşım sunar. Bir modeli ince ayar yapmanın ilk adımı bir bucket oluşturmaktır.

Python kodu bulunmamaktadır, bu nedenle satır satır açıklama gerekmemektedir. Çeviri birebir yapılmıştır.

---

