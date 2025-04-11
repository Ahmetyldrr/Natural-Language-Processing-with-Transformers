# Bölüm 7: ChatGPT ile Üretken Yapay Zeka Devrimi
Bu bölüm, genel olarak derin öğrenme modellerinin ve özellikle ChatGPT gibi büyük dil modellerinin (LLM) genişleyen taksonomisine uyum sağlamanın karmaşıklığını tanıttı. 

# Anlamsal Rol Etiketlemesi (SRL) ve Doğal Dil İşleme (NLP) Görevleri
SRL, bir cümlede her kelimenin rolünü daha iyi anlamak için geliştirilmiş bilgi çıkarımı sağlar. Çıkarılan bilgi, çeviri, özetleme ve diğer NLP görevlerini geliştirebilir. Kelimelerin anlamsal rolünü anlayan bir model, daha iyi kalitede NLP çıktıları sağlayacaktır. Ancak, bir NLP görevini uygulamak için bir yol seçmek zorlaşmıştır. SRL de bu durumdan etkilenmiştir. 

## Kaynak Kullanımını Tanımlayan Dört Parametre
Bu bölümde kullanılan kaynakları tanımlayan dört parametre ile sorunları özetleyebiliriz: göreve özgü, genel amaçlı, geliştirme ve self-servis.

### Şekil 12.1: LLM Yönetiminin Karmaşıklığı
Şekil 12.1, LLM proje yönetiminin karmaşıklığını göstermektedir. Parametreler, bir proje için çeşitli olası şekillerde etkileşime girer. Her parametrenin riski dikkatlice tartılmalıdır, örneğin:

*   **Göreve Özgü**: Bir göreve özgü model (BERT tabanlı bir model gibi) SRL gerçekleştirmek için eğitilmelidir. Bu, makine kaynakları, veri yönetimi, model optimizasyonu (hiperparametreler) ve insan uzman düzeyinde kaynaklar anlamına gelir.
*   **Genel Amaçlı**: ChatGPT, göreve özgü bir model olmamasına rağmen belirli görevleri de gerçekleştirebilir. Bu bölümdeki ChatGPT modeli SRL için eğitilmemiştir. Göreve özgü model kadar kesin olmayabilir, ancak çoğu SRL görevi için maliyet etkin ve nispeten verimlidir.
*   **Geliştirme**: Örneğin bir API ile geliştirme söz konusu olduğunda bir maliyet vardır. Geliştirme, özel bir çözüm veya self-servis oluşturmak için gerekebilir.
*   **Self-Servis**: Self-servis veya özel bir çözüm kullanarak elde edilen gelir, maliyeti haklı kılabilir. Ancak, özelleştirilmiş bir çözümün etkinliğini ölçmek için bir risk yönetimi çalışması yapılmalıdır. ChatGPT Plus gibi bir çevrimiçi hizmet, zayıf bir internet bağlantısı varsa yetersiz olabilir veya bazı projeler için yeterli olabilir.

### Ek Parametreler ve Proje Yönetimi
Dikkate alınması gereken birkaç ek parametre vardır, örneğin: ekiplerin eğitilmesi, self-servis konfigürasyonunda son kullanıcı faaliyetlerinin izlenmesi, çıktıların diğer sistemlere manuel veya otomatik olarak bağlanması ve rekabet eden transformer modelleri. Birçok olası senaryodan bazılarını inceledik. Gerçek hayattaki proje yönetimi daha fazla parametre gerektirir. Örneğin, bir BERT veya GPT modeli yerel bir makinede veya uzak bir sunucuda çalıştırılabilir. Sonuç olarak, parametrelerin değerlendirilmesi ve doğru seçim proje bağlı olacaktır. Bunu akılda tutarak, Shi ve Lin (2019) tarafından tanımlanan sözdizimden bağımsız SRL yaklaşımını keşfetmeye hazırız. 

Bu çeviride Python kodları bulunmamaktadır.

---

