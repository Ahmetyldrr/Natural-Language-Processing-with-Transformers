# Doğal Dil İşleme (NLP) Projelerinde Tokenizer Seçimi

Bir tokenizer seçimi, NLP projesinin hedeflerine bağlıdır. Alt kelime tokenizer'ları transformer modelleri için daha verimli olsa da, kelime ve cümle tokenizer'ları yararlı işlevsellik sağlar. Cümle ve kelime tokenizer'ları, aşağıdakiler de dahil olmak üzere birçok görev için yararlıdır:

Metin işleme, cümle veya kelime düzeyinde NLP görevleri için yeterli olabilir, örneğin metin sınıflandırma. Ayrıca, metinleri cümlelere ve kelimelere ayırmak, transformer modelleri için denetimli bir eğitim veri kümesi oluşturmak için bir işlem hattının bir parçası olabilir. Elde edilen cümleler, örneğin, normalize edilebilir ve ardından çıktıya bir etiketleme işlevi eklenebilir. Buradan, bir alt kelime tokenizer'ı, bir transformer'ın ön eğitim sürecini başlatmak için devreye girebilir. Cümle veya kelime düzeyinde tokenleştirme, örneğin spam tespiti için sınıflandırıcılar gibi daha basit makine öğrenimi görevleri için yeterli olabilir. Parça-of-Speech (POS) etiketleme ve Named Entity Recognition (NER), kelime düzeyinde yapıldığında kelime veya cümle tokenleştirmeden yararlanabilir. Bir tokenizer seçimi, uygulanacak NLP işlevleri, makine öğrenimi veya transformer modeli üzerinde kalıcı bir etkiye sahip olacak kritik bir karardır.

# Tokenizer'ları Keşfetme

Bu bölümdeki GitHub deposunda bulunan `Exploring tokenizers.ipynb` dosyasını açın. İlk hücreler, bu not defterini çalıştırmak için gerekli kütüphaneleri yükler:

```python
# Hugging Face Transformers
!pip install transformers

# Python'da tablo verilerini yazdırma
!pip install tabulate

# Doğal Dil Araç Seti
!pip install nltk
```

Hugging Face transformer'larını alt kelime tokenizer'ları için, tabulate kütüphanesini tablo verilerini yazdırmak için ve Doğal Dil Araç Seti'ni (nltk) kelime ve cümle tokenizer'ları için yükledik. Bu bölümdeki alt bölüm başlıkları, not defterindekiyle aynıdır.

 Doğal Dil Araç Seti'ni kullanarak bazı ana kelime ve cümle tokenizer'larını inceleyelim:

```python
import nltk
nltk.download('punkt')  # 'punkt' paketini indir

# nltk.tokenize modülünden çeşitli tokenizer'ları içe aktar
from nltk.tokenize import sent_tokenize, word_tokenize, RegexpTokenizer, \
    TreebankWordTokenizer, WhitespaceTokenizer, PunktSentenceTokenizer, \
    WordPunctTokenizer, MWETokenizer
```

Satır satır açıklama:

1. `import nltk`: Doğal Dil Araç Seti (nltk) kütüphanesini içe aktarır.
2. `nltk.download('punkt')`: 'punkt' paketini indirir. Bu paket, cümle ve kelime tokenleştirme için gerekli olan önceden eğitilmiş modelleri içerir.
3. `from nltk.tokenize import ...`: nltk.tokenize modülünden çeşitli tokenizer'ları içe aktarır. Bu tokenizer'lar:
   - `sent_tokenize`: Cümle tokenleştirme için kullanılır.
   - `word_tokenize`: Kelime tokenleştirme için kullanılır.
   - `RegexpTokenizer`: Düzenli ifadeler kullanarak tokenleştirme için kullanılır.
   - `TreebankWordTokenizer`: Treebank kelime tokenleştirme için kullanılır.
   - `WhitespaceTokenizer`: Boşluk karakterlerine göre tokenleştirme için kullanılır.
   - `PunktSentenceTokenizer`: Cümle tokenleştirme için kullanılır.
   - `WordPunctTokenizer`: Kelime ve noktalama tokenleştirme için kullanılır.
   - `MWETokenizer`: Çoklu kelime öbeklerini tokenleştirme için kullanılır.

---

