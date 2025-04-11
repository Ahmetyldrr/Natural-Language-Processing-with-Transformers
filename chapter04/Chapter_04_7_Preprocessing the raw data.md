# Veri Ön İşleme

Bu bölümde, europarl-v7.fr-en.en ve europarl-v7.fr-en.fr dosyalarını ön işleyeceğiz. Program, standart Python fonksiyonları ve pickle kullanarak serileştirilmiş çıktı dosyalarını döker:

```python
import pickle
from pickle import dump
```

## Dosyayı Belleğe Yükleme

Dosyayı belleğe yüklemek için fonksiyon tanımlarız:
```python
# load doc into memory
def load_doc(filename):
    # dosyayı sadece okunabilir olarak aç
    file = open(filename, mode='rt', encoding='utf-8')
    # tüm metni oku
    text = file.read()
    # dosyayı kapat
    file.close()
    return text
```

## Dokümanı Cümlelere Ayırma

Yüklenen dokümanı cümlelere ayırır:
```python
# split a loaded document into sentences
def to_sentences(doc):
    return doc.strip().split('\n')
```

## Cümle Uzunluklarını Bulma

En kısa ve en uzun cümle uzunluklarını alır:
```python
# shortest and longest sentence lengths
def sentence_lengths(sentences):
    lengths = [len(s.split()) for s in sentences]
    return min(lengths), max(lengths)
```

## Cümleleri Temizleme

İçeri aktarılan cümle satırları, işe yaramaz ve gürültülü tokenleri önlemek için temizlenmelidir. Satırlar normalize edilir, beyaz boşluklarda tokenleştirilir ve küçük harfe dönüştürülür. Her token'den noktalama işaretleri kaldırılır, yazdırılamayan karakterler kaldırılır ve sayı içeren tokenler hariç tutulur. Temizlenen satır bir dize olarak saklanır.

```python
# clean lines
import re
import string
import unicodedata

def clean_lines(lines):
    cleaned = list()
    # karakter filtreleme için regex hazırla
    re_print = re.compile('[^%s]' % re.escape(string.printable))
    # noktalama işaretlerini kaldırmak için çeviri tablosu hazırla
    table = str.maketrans('', '', string.punctuation)
    for line in lines:
        # unicode karakterleri normalize et
        line = unicodedata.normalize('NFD', line).encode('ascii', 'ignore')
        line = line.decode('UTF-8')
        # beyaz boşluklarda tokenleştir
        line = line.split()
        # küçük harfe dönüştür
        line = [word.lower() for word in line]
        # her token'den noktalama işaretlerini kaldır
        line = [word.translate(table) for word in line]
        # her token'den yazdırılamayan karakterleri kaldır
        line = [re_print.sub('', w) for w in line]
        # sayı içeren tokenleri kaldır
        line = [word for word in line if word.isalpha()]
        # dize olarak sakla
        cleaned.append(' '.join(line))
    return cleaned
```

## Veri Kümesini Hazırlama

İngilizce verileri yükler ve temizler:
```python
# load English data
filename = 'europarl-v7.fr-en.en'
doc = load_doc(filename)
sentences = to_sentences(doc)
minlen, maxlen = sentence_lengths(sentences)
print('English data: sentences=%d, min=%d, max=%d' % (len(sentences), minlen, maxlen))
cleanf = clean_lines(sentences)
```

Veri kümesi şimdi temiz ve `English.pkl` adlı serileştirilmiş bir dosyaya pickle ile dökülür:
```python
filename = 'English.pkl'
outfile = open(filename, 'wb')
pickle.dump(cleanf, outfile)
outfile.close()
print(filename, "saved")
```

Çıktı, anahtar istatistikleri gösterir ve `English.pkl` dosyasının kaydedildiğini doğrular:
```
English data: sentences=2007723, min=0, max=668
English.pkl saved
```

## Fransızca Veri Kümesini Hazırlama

Aynı işlemi Fransızca verileri için tekrar eder ve `French.pkl` adlı serileştirilmiş bir dosyaya dökülür:
```python
# load French data
filename = 'europarl-v7.fr-en.fr'
doc = load_doc(filename)
sentences = to_sentences(doc)
minlen, maxlen = sentence_lengths(sentences)
print('French data: sentences=%d, min=%d, max=%d' % (len(sentences), minlen, maxlen))
cleanf = clean_lines(sentences)
filename = 'French.pkl'
outfile = open(filename, 'wb')
pickle.dump(cleanf, outfile)
outfile.close()
print(filename, "saved")
```

Çıktı, Fransızca veri kümesi için anahtar istatistikleri gösterir ve `French.pkl` dosyasının kaydedildiğini doğrular:
```
French data: sentences=2007723, min=0, max=693
French.pkl saved
```

## Sonuç

Ana ön işleme işlemi tamamlandı. Ancak, veri kümelerinin gürültülü ve karışık tokenler içermediğinden emin olmak için hala bazı kontroller yapmamız gerekiyor.

---

