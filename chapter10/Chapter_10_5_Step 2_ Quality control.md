# Eğitilmiş Modelin Davranışı ve En İyi Uygulamalar

Eğitilmiş bir model, bir dil öğrenmiş bir kişi gibi davranacaktır. Giriş verilerinden neyi anlayabileceğini ve öğrenebileceğini bilecektir. Giriş verileri, Adım 1: Ön İşleme ile aynı işlemden geçmelidir ve eğitim veri kümesine yeni bilgiler eklemelidir. Eğitim veri kümesi, sırasıyla, bir kurumsal projenin bilgi tabanı haline gelebilir. Kullanıcılar, veri kümesi üzerinde Doğal Dil İşleme (NLP) görevlerini çalıştırabilecek ve sorulara güvenilir cevaplar, belirli belgelerin yararlı özetlerini ve daha fazlasını elde edebileceklerdir.

Gerçek zamanlı giriş verilerine, Adım 1: Ön İşleme'de açıklanan en iyi uygulamaları uygulamamız gerekir. Örneğin, bir transformer, bir kullanıcıdan veya bir NLP görevi gibi bir girdi üzerinde çalışabilir, örneğin bir belge listesini özetlemek gibi. Transformerlar şimdiye kadar geliştirilmiş en güçlü NLP modelleridir. Bu, etik sorumluluğumuzun da arttığı anlamına gelir.

# En İyi Uygulamalar

Bazı en iyi uygulamaları gözden geçirelim:

*   **Gerçek Zamanlı Giriş Metni Kontrolü**: Kötü bilgiyi kabul etmeyin. Bunun yerine, girişi gerçek zamanlı olarak ayrıştırın ve kabul edilemez verileri filtreleyin (Adım 1'e bakın).
*   **Gerçek Zamanlı Mesajlar**: Reddedilen verileri ve filtrelenme nedenini saklayın, böylece kullanıcılar günlük kayıtlarına danışabilir. Bir transformer, uygunsuz bir soru sorulduğunda gerçek zamanlı mesajlar gösterin.
*   **Dil Dönüşümleri**: Nadir kullanılan kelimeleri, mümkün olduğunda standart kelimelere dönüştürebilirsiniz. Bu bölümdeki Word2Vec tokenleştirme bölümünün 4. Durumuna bakın. Bu her zaman mümkün değildir. Mümkün olduğunda, ileriye doğru bir adım olabilir.
*   **Gizlilik Kontrolleri**: Bir transformer modeline veri akışı yaparken veya kullanıcı girdisini analiz ederken, özel veriler, kullanıcı veya transformer'ın çalıştığı ülke tarafından yetkili kılınmadıkça veri kümesinden ve görevlerden çıkarılmalıdır. Bu zor bir konudur. Gerekirse bir hukuk danışmanına danışın.

# İnsan Kalite Kontrolünün Gerekliliği

Sadece bazı en iyi uygulamaları gözden geçirdik. Şimdi neden insan kalite kontrolünün zorunlu olduğunu görelim.

Python kodları bulunmamaktadır, ancak NLP konseptleri ve transformer modelleri hakkında açıklamalar mevcuttur.

---

