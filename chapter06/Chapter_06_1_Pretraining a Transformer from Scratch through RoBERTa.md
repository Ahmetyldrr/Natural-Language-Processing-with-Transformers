# Birebir Türkçe Çeviri

Bazen, önceden eğitilmiş bir model beklenen sonuçları vermez. Önceden eğitilmiş model, ince ayar yoluyla ek eğitime tabi tutulsa bile, yine de planlandığı gibi çalışmaz. O noktada, bir yaklaşım, GPT ve BERT gibi mimarileri kullanmak için Hugging Face gibi platformlar aracılığıyla sıfırdan ön eğitim başlatmaktır. Sıfırdan bir model ön eğitimi yaptığınızda, bir proje için ihtiyaç duyabileceğiniz diğer modelleri nasıl eğiteceğinizi bileceksiniz. Bu bölümde, BERT'in gelişmiş bir varyantı olan RoBERTa modelini sıfırdan oluşturacağız. Model, BERT modelleri için ihtiyacımız olan transformer yapım kitinin yapı taşlarını kullanacaktır. Ayrıca, önceden eğitilmiş tokenleştiriciler veya modeller kullanılmayacaktır. RoBERTa modeli, bu bölümde açıklanan 15 adımlı süreç izlenerek oluşturulacaktır. Maskelenmiş tokenler üzerinde dil modellemesi yapabilen bir model oluşturmak için önceki bölümlerde kazanılan transformer bilgisini adım adım kullanacağız.

# Bölüm 2'de, Transformer Modelinin Mimarisine Giriş bölümünde, Orijinal Transformer'ın yapı taşlarını inceledik. 
# Bölüm 5'te, BERT Aracılığıyla İnce Ayar'a Dalış bölümünde, BERT modelinin bir varyasyonu aracılığıyla önceden eğitilmiş bir modelin nasıl ince ayar yapılacağını araştırdık. 
Bu bölüm, Hugging Face'in sorunsuz modüllerine dayanan bir Jupyter not defteri kullanarak sıfırdan bir önceden eğitilmiş transformer modeli oluşturmaya odaklanacaktır. Modelin adı KantaiBERT'tir. Felsefeci Immanuel Kant'ın adını taşıyan benim projemdir. Bir modeli kendi ortamınızda eğittiğinizde ve dağıttığınızda, ürününüzü benzersiz kılmak için ona bir "marka" verebilirsiniz. KantaiBERT ilk olarak bu bölüm için oluşturulan Immanuel Kant'ın kitaplarının bir derlemesini yükler. Verilerin nasıl elde edildiğini göreceksiniz. Ayrıca, bu not defteri için kendi veri kümelerinizi nasıl oluşturacağınızı da göreceksiniz.

KantaiBERT, kendi tokenleştiricisini sıfırdan eğitir. İlk olarak, ön eğitim süreci sırasında kullanılacak olan birleştirme ve kelime bilgisi dosyalarını oluşturacaktır. KantaiBERT daha sonra veri kümesini işler, bir eğitmen başlatır ve modeli eğitir. Daha sonra, eğitilmiş model KantaiBERT'i deneysel bir aşağı akış dil modelleme görevi gerçekleştirmek ve Immanuel Kant'ın mantığını kullanarak bir maskeyi doldurmak için çalıştıracağız. Son olarak, bu bölümde edindiğiniz bilgiyi çalışmaya ve X (eski adıyla Twitter) verileri üzerinde bir Generative AI müşteri destek modeli ön eğitimi yapmaya koyacağız. 20 büyük markanın destek tweetlerinden oluşan bir Kaggle veri kümesini kullanacağız. RoBERTa modeli ile açık kaynaklı bir Generative AI sohbet ajanı prototipi nasıl oluşturulacağını keşfedeceksiniz. Bu, gerektiğinde bağımsız sohbet ajanlarının kapısını açar. Bölümün sonunda, sıfırdan bir transformer modeli nasıl oluşturulacağını bileceksiniz. Ayrıca, belirli bir ihtiyacı karşılamak için bir modeli eğitmek zorunda kaldığınız bir durumla yüzleşmek için yeterli transformer bilgisine sahip olacaksınız.

Bu bölüm aşağıdaki konuları kapsar:
- RoBERTa ve DistilBERT benzeri modeller
- Bayt düzeyinde bayt çifti kodlama
- Bir tokenleştirici eğitmek
- Modelin yapılandırmasını tanımlama
- Sıfırdan bir model başlatma
- Bir modelin parametrelerini keşfetme
- Bir veri kümesi oluşturma
- Bir veri toplayıcı tanımlama
- Bir eğitmen başlatma
- Modeli ön eğitimi
- FillMaskPipeline ile dil modelleme
- Modeli Maskelenmiş Dil Modelleme (MLM) aşağı akış görevlerine uygulama
- X (eski adıyla Twitter) veri kümesine dayalı bir Generative AI sohbet ajanı ön eğitimi

Bu son teknoloji alanındaki tüm yenilikler ve kütüphane güncellemeleri ile paketler ve modeller düzenli olarak değişmektedir. Lütfen en son kurulum ve kod örnekleri için GitHub deposuna gidin: https://github.com/Denis2054/Transformers-for-NLP-and-Computer-Vision-3rd-Edition/tree/main/Chapter06 . Ayrıca, bu veya herhangi bir bölümdeki kodu çalıştırırken herhangi bir sorun yaşarsanız Discord topluluğumuza bir mesaj gönderin ( https://www.packt.link/Transformers ). İlk adımımız, oluşturmayı planladığımız transformer mimarisinin yapısını ve başarmayı amaçladığımız görevleri ana hatlarıyla belirlemek içerir.

Python kodları bulunmamaktadır, ancak ilgili başlıklar altında kodlarla ilgili açıklamalar yapılacaktır.

# İlgili Python Kodları ve Açıklamaları

İlgili python kodları mevcut değildir, ancak transformer modelinin nasıl oluşturulacağı ve eğitileceği hakkındaki adımlar yukarıdaki metinde açıklanmıştır. 

Örneğin, bir tokenleştiricinin eğitilmesi aşağıdaki gibi bir kod ile gerçekleştirilebilir:
```python
from tokenizers import ByteLevelBPETokenizer

# Tokenleştiriciyi oluşturma
tokenizer = ByteLevelBPETokenizer()

# Tokenleştiriciyi eğitme
tokenizer.train(
    files=["path/to/your/dataset.txt"],
    vocab_size=52000,
    min_frequency=2,
    special_tokens=["<s>", "<pad>", "</s>", "<unk>", "<mask>"],
)
```
Yukarıdaki kod, `ByteLevelBPETokenizer` kullanarak bir tokenleştirici oluşturur ve belirtilen veri kümesi üzerinde eğitir.

Modelin yapılandırmasını tanımlama ve sıfırdan bir model başlatma aşağıdaki gibi yapılabilir:
```python
from transformers import RobertaConfig, RobertaForMaskedLM

# Model yapılandırmasını tanımlama
config = RobertaConfig(
    vocab_size=52000,
    max_position_embeddings=514,
    num_attention_heads=12,
    num_hidden_layers=6,
    type_vocab_size=1,
)

# Sıfırdan bir model başlatma
model = RobertaForMaskedLM(config=config)
```
Yukarıdaki kod, `RobertaConfig` kullanarak model yapılandırmasını tanımlar ve `RobertaForMaskedLM` kullanarak sıfırdan bir model başlatır.

Bu şekilde, transformer modeli oluşturma ve eğitme adımları python kodları ile gerçekleştirilebilir.

---

