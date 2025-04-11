# Bu Bölümde Yapılacaklar
Bu bölümde, Hugging Face RobertaForCausalLM modelini, X (eski adıyla Twitter) için bir Generative AI müşteri destek sohbet ajanı olarak önceden eğitmek istiyoruz. RoBERTa, yalnızca kodlayıcı (encoder) olan bir modeldir. Bu nedenle, temel olarak girdileri anlamak ve kodlamak için tasarlanmıştır. Bölüm 2'de, Transformer Modelinin Mimarisine Başlarken, kodlayıcının (encoder) nasıl öğrenip daha sonra içeriği oluşturmak için bu bilgiyi kod çözücüye (decoder) gönderdiğini gördük. Ancak, bu bölümde, Hugging Face işlevselliğini kullanarak bir RoBERTa modelini otoregresif (autoregressive) bir Generative AI görevi yürütmek üzere uyarlayacağız. Deneyin sınırlamaları vardır, ancak içerik oluşturmanın iç işleyişini gösterir. Bu bölümde, KantaiBERT'i sıfırdan oluşturarak edindiğiniz bilgi, bu yolculuğun keyifli olmasını sağlayacaktır! Üretken model ve veri seti ücretsizdir, bu da egzersizi özellikle ilginç kılmaktadır. Bazı çalışmalar ile, alanına özgü Generative AI ajanları, kendi modellerine sahip olmak isteyen şirketlere yardımcı olabilir. ChatGPT'nin ortaya çıkışından bu yana Generative AI hızla yayıldı. Bu bölümde bir prototip sohbet ajenti oluşturma deneyiminiz, otomatik diyalogların bu yeni çağı hakkında size içgörü sağlayacaktır.

# Adımlara Başlarken
KantaiBERT oluştururken gittiğimiz not defterinin tüm ayrıntılarını tekrarlamayacağız. Bu bölümde kazandığınız deneyimi kullanarak not defterini hücre hücre çalıştırın, böylece hiçbir şeyi kaçırmazsınız. Not defterindeki adımların başlıkları bu bölümdeki başlıklarla eşleşiyor. Customer_Support_for_X.ipynb dosyasını GitHub'daki bölümün dizininde açın ve işe koyulalım! Generative AI prototipimizi sadece 10 adımda çalışır hale getirebiliriz.

Python kodları bulunmamaktadır, bu nedenle açıklama yapmaya gerek yoktur. Çeviri birebir yapılmıştır.

---

