# Trafo Modellerinde Tokenizerlerin Rolü

Trafo modellerini incelerken, genellikle mimarilerine ve eğitilmeleri için sağlanan veri kümelerine odaklanırız. Bu kitap, Orijinal Trafo, BERT, RoBERTa, ChatGPT, GPT4, PaLM, LaMBDA, DALL-E ve daha fazlasını kapsar. Ayrıca, kitap birkaç kıyaslama görevi ve veri kümesini gözden geçirir. BERT benzeri bir modeli fine-tune ettik ve tokenizers kullanarak veri kodlamak suretiyle bir RoBERTa tokenizer eğittik. Önceki Bölüm 9, Yorumlanabilir Araçlarla Siyah Kutuyu Kırma'da, bir trafo modelinin iç işleyişini analiz ederek siyah kutuyu açtık. Ancak, tokenizerlerin oynadığı kritik rolü keşfetmedik ve oluşturduğumuz modelleri nasıl şekillendirdiklerini değerlendirmedik. Yapay zeka veri-güdümlüdür. Raffel ve diğerleri (2019), bu kitapta atıfta bulunulan tüm yazarlar gibi, trafo modelleri için veri kümeleri hazırlamak için zaman harcadılar. Bu bölümde, trafo modellerinin performansını engelleyen veya artıran tokenizerlerin bazı sorunlarını inceleyeceğiz. Tokenizerleri yüzeyselleştirmeyin. Kullanmış olduğunuz belirli bir kelime sözlüğünüz olabilir (örneğin, gelişmiş tıbbi dil) ve genel bir tokenizer tarafından zayıf bir şekilde işlenen kelimeler içerebilir. Bir tokenizerin kalitesini ölçmek için bazı tokenizer-agnostik en iyi uygulamaları tanıtarak başlayacağız. Veri kümeleri ve tokenizerler için temel yönergeleri bir tokenization perspektifinden açıklayacağız. Ardından, herhangi bir tokenleştirme yöntemiyle karşılaştığımız sorunları açıklamak için bir Word2Vec tokenizer kullanarak tokenizerlerin bazı olası sınırlarını göreceğiz. Sınırlar bir Python programı ile gösterilecektir.

## Tokenizerlerin İncelenmesi

İncelememize cümle ve kelime tokenizerleri ile başlayacağız. Bu tokenizerler değerli doğal dil işleme araçları sağlar. Ancak, trafo modeli eğitimi için daha verimli alt kelime tokenizerleri ile eşleşmezler. Bu nedenle, trafo modelleri için daha verimli alt kelime tokenizerleri ile devam edeceğiz. Alt kelime tokenizerleri, bir tokenizerin bir trafo modelinin eğitimi ve performansını nasıl şekillendirebileceğini gösterir. Bir sözlük oluşturmak için hangi alt kelime tokenizerin uygulandığını tespit etmeyi göreceğiz. Son olarak, token-ID eşlemelerini görüntülemek ve kontrol etmek için bir fonksiyon oluşturacağız.

### Bu Bölümün Kapsadığı Konular

* Tokenizerlerin çıktısını kontrol etmek için temel yönergeler
* Ham veri stratejileri ve ön işleme veri stratejileri
* Word2Vec tokenization sorunları ve sınırları
* Word2Vec tokenizerleri değerlendirmek için bir Python programı oluşturma
* Cümle ve kelime tokenizerleri
* Alt kelime tokenizerleri
* Tokenizer tespiti
* Token-ID eşlemelerini görüntüleme ve kontrol etme

Bu alandaki tüm yeniliklere ve kütüphane güncellemelerine rağmen, paketler ve modeller düzenli olarak değişmektedir. Lütfen en son kurulum ve kod örnekleri için GitHub deposuna gidin: https://github.com/Denis2054/Transformers-for-NLP-and-Computer-Vision-3rd-Edition/tree/main/Chapter10 . Bu veya herhangi bir bölümdeki kodu çalıştırırken sorun yaşarsanız, Discord topluluğumuzda bir mesaj gönderin ( https://discord.com/invite/Fp4XXhECdh ). İlk adımımız, Raffel ve diğerleri (2019) tarafından tanımlanan metin-metin metodolojisini keşfetmek olacaktır.

Python kodları bulunmamaktadır, ancak ileriki kısımlarda örnek kodlar verilecektir. Örnek bir Python kodu aşağıdaki gibi açıklanabilir:

```python
# Örnek bir Python kodu
def token_id_goster(tokenizer, input_text):
    # Tokenizer kullanarak girdi metnini tokenleştir
    inputs = tokenizer(input_text, return_tensors="pt")
    
    # Token-ID eşlemelerini görüntüle
    print(inputs["input_ids"])

# Tokenizer nesnesini oluştur
tokenizer = AutoTokenizer.from_pretrained("bert-base-uncased")

# Girdi metnini belirle
input_text = "Bu bir örnek cümledir."

# Token-ID eşlemelerini görüntülemek için fonksiyonu çağır
token_id_goster(tokenizer, input_text)
```

Bu kod, bir tokenizer nesnesi oluşturur, girdi metnini tokenleştirir ve token-ID eşlemelerini görüntüler.

1. `tokenizer = AutoTokenizer.from_pretrained("bert-base-uncased")`: Bu satır, önceden eğitilmiş bir BERT tokenizer nesnesi oluşturur.
2. `inputs = tokenizer(input_text, return_tensors="pt")`: Bu satır, girdi metnini tokenleştirir ve PyTorch tensörleri olarak döndürür.
3. `print(inputs["input_ids"])`: Bu satır, token-ID eşlemelerini görüntüler.

Bu kod, bir tokenizerin nasıl kullanılacağını ve token-ID eşlemelerinin nasıl görüntüleneceğini gösterir.

---

