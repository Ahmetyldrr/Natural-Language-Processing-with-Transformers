# Ek: Transformerların Optimize Edilmiş Zaman Karmaşıklığının Detaylı Açıklaması

Bu ek, 1. Bölüm olan "Transformerlar Nedir?" bölümündeki "Transformerların nasıl doğduğu" kısmında tanıtılan transformerların optimize edilmiş zaman karmaşıklığının detaylı bir açıklamasını içerir. Bu ekte, her şeyi değiştiren transformer modellerindeki tek bir işlemin aldatıcı bir şekilde basit olan O(1) zaman karmaşıklığının inanılmaz gücünü ortaya koyacağız. Bunu yapmak için, 1. Bölüm'de tanıtılan `O-1_and_Accelerators.ipynb` dosyasını, transformerların donanım hızlandırıcılarını nasıl ele geçirdiğini görmek için detaylı olarak inceleyeceğiz. Daha sonra, transformerların kullandığı token-token yaklaşımının, metni her bir token'ı bir önceki token'ların oluşturduğu ilişki ve bağlamdan etkilenerek tek bir token halinde oluşturmalarını nasıl sağladığını göreceğiz.

Not: Tokenlar kelimelerin parçalarıdır, ancak basitlik açısından, bu bölümde doğal dil işleme anlatılırken "kelime" ve "token" terimleri birbirinin yerine kullanılacaktır.

Python kodları bulunmamaktadır, bu nedenle satır satır açıklama yapılmamıştır. Eğer ingilizce paragraf içerisinde kod var ise belirtiniz.

---

