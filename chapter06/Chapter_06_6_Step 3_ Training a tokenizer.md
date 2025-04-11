# Bu Bölümde Yapılanlar
Bu bölümde, program önceden eğitilmiş bir tokenleştirici kullanmamaktadır. Örneğin, önceden eğitilmiş bir GPT-2 tokenleştiricisi kullanılabilir. Ancak, bu bölümdeki eğitim süreci, sıfırdan bir tokenleştirici eğitmeyi içerir. Hugging Face'in ByteLevelBPETokenizer'ı, kant.txt (veya başka bir metin) kullanılarak eğitildiğinde, Bayt Çift Kodlaması (BPE) tokenleştiricisini kullanır. Bir BPE tokenleştiricisi, dizeleri veya kelimeleri alt kelime birimlerine veya alt dizelere böler. Bu yaklaşımın birkaç avantajı vardır, bunlar şunları içerir: Tokenleştirici, kelimeleri minimal bileşenlere ayırabilir ve daha sonra bu bileşenleri istatistiksel olarak anlamlı olanlara birleştirebilir. Örneğin, "smaller" ve "smallest" gibi kelimeler "small," "er," ve "est" olarak temsil edilebilir. Ayrıca, tokenleştirici daha da ileri giderek "sm" ve "all" gibi alt kelime parçaları üretebilir. Esasen, kelimeler tek bir token gibi "small" yerine "sm" ve "all" gibi alt kelime tokenlarına ve daha küçük birimlere ayrılır. WordPiece düzeyinde kodlama kullanılarak "unk_token" olarak temsil edilen bilinmeyen olarak sınıflandırılan metin parçaları etkili bir şekilde minimize edilebilir veya ortadan kaldırılabilir. Bu modelde, tokenleştiriciyi aşağıdaki parametrelerle eğiteceğiz: files=paths veri kümesinin yoludur. vocab_size=52_000 tokenleştiricimizin model uzunluğudur. min_frequency=2 minimum frekans eşiğidir. special_tokens=[] özel tokenlerin listesidir. Bu durumda, özel tokenlerin listesi: <s> : başlangıç tokeni <pad> : doldurma tokeni </s> : bitiş tokeni <unk> : bilinmeyen token <mask> : dil modellemesi için maskeleme tokeni Tokenleştirici, birleştirilmiş alt dize tokenleri oluşturmak ve frekanslarını analiz etmek için eğitilecektir.

# Tokenleştirme İşlemi
İki kelimeyi bir cümlenin ortasında ele alalım: ...the tokenizer... İlk adım, dizeyi tokenleştirmektir: 'Ġthe' , 'Ġtoken' , 'izer' , Dize şimdi Ġ ile tokenlere ayrılmıştır, bu bir boşluğu (kelimeler arasındaki boşluk) temsil eder. Bir sonraki adım, bunları indekslerle değiştirmektir: ‘Ġthe’ ‘Ġtoken’ ‘izer’ 150 5430 4712 Tablo 6.1: Üç token için indeksler

# Python Kodları ve Açıklamaları
```python
# pathlib modülünü kullanarak Path sınıfını içe aktarıyoruz
from pathlib import Path

# tokenizers modülünden ByteLevelBPETokenizer sınıfını içe aktarıyoruz
from tokenizers import ByteLevelBPETokenizer

# paths değişkenine, mevcut dizinde ve alt dizinlerdeki tüm .txt dosyalarının yollarını atıyoruz
paths = [str(x) for x in Path(".").glob("**/*.txt")]

# Dosyalardan içerikleri okuyoruz, geçersiz karakterleri yok sayıyoruz veya değiştiriyoruz
file_contents = []
for path in paths:
    try:
        # Her bir dosyayı utf-8 kodlaması ile okuyoruz, hataları 'replace' ederek dosya içeriğini okuyoruz
        with open(path, 'r', encoding='utf-8', errors='replace') as file:
            file_contents.append(file.read())
    except Exception as e:
        # Dosya okunurken hata oluşursa, hata mesajını yazdırıyoruz
        print(f"Error reading {path}: {e}")

# Dosya içeriklerini tek bir stringde birleştiriyoruz
text = "\n".join(file_contents)

# Bir tokenleştirici nesnesi oluşturuyoruz
tokenizer = ByteLevelBPETokenizer()

# Tokenleştiriciyi eğitiyoruz
# vocab_size: tokenleştiricinin model uzunluğu
# min_frequency: minimum frekans eşiği
# special_tokens: özel tokenlerin listesi
tokenizer.train_from_iterator([text], vocab_size=52_000, min_frequency=2, special_tokens=["<s>", "<pad>", "</s>", "<unk>", "<mask>"])

# Tokenleştirici eğitildikten sonra, hatalı karakterleri atlayarak tokenleştiriciyi eğitir ve kullanıma hazır hale getirir.
```
Tokenleştirici, birleştirilmiş alt dize tokenleri oluşturmak ve frekanslarını analiz etmek için eğitilecektir.

---

