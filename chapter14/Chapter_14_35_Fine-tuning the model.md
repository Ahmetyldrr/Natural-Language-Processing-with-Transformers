# İncelenen Durum: Metin Sınıflandırma Görevi için PaLM 2 Modelini İnce Ayara Alma

Bu durumda, veri seti, bir metnin hokey veya beyzbol ile ilgili olup olmadığını belirlemek için bir sınıflandırma görevi için oluşturulmuştur: 
Şekil 14.15: Hiperparametrelerin Seçilmesi 
Kullanılan model PaLM 2, text-bison@001'dir. Projenize ve bölgedeki modellerin mevcudiyetine bağlı olarak diğerlerini seçebilirsiniz. İnce ayar, belirli Google Vertex AI kütüphanelerinin etkinleştirilmesini gerektirir: https://cloud.google.com/model-garden. Bir proje oluşturmanız ve bir faturalandırma hesabını etkinleştirmeniz gerekecektir. Bazı durumlarda, Google başlamak için ücretsiz krediler sağlayabilir. Başlamadan önce bütçeleri, maliyetleri ve faturalandırmayla ilgili her şeyi doğruladığınızdan emin olun. Ayrıca, bazı bölgeler ve hizmetler için istek sayısı sınırlıdır. Gerekli kotalara erişiminiz olduğundan emin olun. Son olarak, arayüz, Google'ın yeni işlevler oluşturmaya devam etmesi nedeniyle gelişecektir. Ancak temel kavramlar aynı kalır: bir veri seti hazırlama, bir modeli ince ayar yapma ve modeli test etme. Bu süreç, bazı açık kaynak platformlarına göre daha az sezgisel ve hızlı olabilir. Ancak, Google Cloud, AWS, Microsoft Azure, IBM Cloud ve Hugging Face'i büyük platformlardan biri veya diğer profesyonel bulut platformlarıyla birlikte yönetebilmek, becerileri geliştirmek için dikkate değer bir varlıktır. Yapay zeka destekli asistanlar birçok yapay zeka ve veri bilimi görevini üstlendikçe, yapay zeka projeleri için bir bulut platformu yönetmek mükemmel bir beceridir. Şimdi, ince ayar sürecini oluşturabilir ve çalıştırabiliriz: 
Şekil 14.16: Spor verileriyle modeli ince ayar yapma 
Model ince ayarlandıktan sonra, her projeye verilen izinlere bağlı olarak Google Vertex AI test sürecini izleyerek çalıştırabiliriz. PaLM 2'nin yetenekleri GPT-4 ile karşılaştırılabilir. Mutlak "en iyi çözüm" yoktur. Her projenin farklı hedefleri ve özellikleri vardır. Proje yönetimi ekibinin hangi platformun bir proje için en iyi olduğuna karar vermesi, maliyet, performans, güvenlik, gizlilik ve diğer proje kısıtlamalarını dikkate alması gerekecektir. Bir yapay zeka uzmanının rolü, karar vericileri etkilemek değil, her platformun artılarını ve eksilerini objektif ve etik bir şekilde göstermektir. Sonunda, Google Cloud veya başka bir platformla çalışmak bir proje düzeyinde ve yönetim kararına bağlı olacaktır. Google AI asistanlarını ve API'larını inceledik. Yolculuğumuzu özetleyelim.

Python kodu bulunmamaktadır. 

Eğer bir kod snippet içerseydi, satır satır açıklamalar şu şekilde yapılırdı:
```python
# kod satırı
print("örnek kod")  # bu satır ekrana "örnek kod" yazdırır
```
Örneğin, eğer bir python kodu aşağıdaki gibi olsaydı:
```python
def topla(a, b):
    return a + b

sonuc = topla(3, 5)
print(sonuc)
```
Açıklaması şu şekilde olurdu:
1. `def topla(a, b):` : `topla` adında, iki parametre (`a` ve `b`) alan bir fonksiyon tanımlanır.
2. `return a + b` : Fonksiyon, `a` ve `b` değerlerini toplar ve sonucu döndürür.
3. `sonuc = topla(3, 5)` : `topla` fonksiyonu `3` ve `5` değerleri ile çağrılır ve sonuç `sonuc` değişkenine atanır.
4. `print(sonuc)` : `sonuc` değişkeninin değeri ekrana yazdırılır.

---

