# Veri Hazırlama İşlemleri
Şimdi işlemimiz, önceki bölümde temizlenen veri kümelerini yükleyecek fonksiyonu tanımlamak ve ön işleme sonlandırıldığında bunları kaydetmektir:

```python
from pickle import load
from pickle import dump
from collections import Counter

# Temiz veri kümesini yükle
def load_clean_sentences(filename):
    return load(open(filename, 'rb'))

# Temiz cümle listesini dosyaya kaydet
def save_clean_sentences(sentences, filename):
    dump(sentences, open(filename, 'wb'))
    print('Saved: %s' % filename)
```

Şimdi bir kelime hazinesi sayaç oluşturacak fonksiyonu tanımlıyoruz. Ayrıştırmış olduğumuz dizilerde bir kelimenin kaç kez kullanıldığını bilmek önemlidir. Örneğin, iki milyon satır içeren bir veri kümesinde bir kelime sadece bir kez kullanılıyorsa, onu öğrenmek için değerli GPU kaynaklarını harcamak boşa olur!

```python
# Tüm kelimeler için frekans tablosu oluştur
def to_vocab(lines):
    vocab = Counter()
    for line in lines:
        tokens = line.split()
        vocab.update(tokens)
    return vocab
```

Kelime hazinesi sayaç, `min_occurrence` değerinin altında kalan kelimeleri tespit edecektir:

```python
# Frekansı belirli eşik değerin altında kalan kelimeleri kaldır
def trim_vocab(vocab, min_occurrence):
    tokens = [k for k, c in vocab.items() if c >= min_occurrence]
    return set(tokens)
```

Bu örnekte, `min_occurrence=5` olarak belirlenmiştir ve bu eşiğin altında veya eşit olan kelimeler, modelin analiz etmek için zaman harcamasını önlemek amacıyla kaldırılmıştır.

Şimdi, Out-Of-Vocabulary (OOV) kelimeleri ele almamız gerekiyor. OOV kelimeleri, yanlış yazılmış kelimeler, kısaltmalar veya standart kelime hazinesi temsillerine uymayan herhangi bir kelime olabilir. Otomatik yazım düzeltmesi kullanabilirdik, ancak bu tüm sorunları çözmezdi. Bu örnekte, OOV kelimelerini basitçe `unk` (bilinmeyen) etiketiyle değiştireceğiz:

```python
# Tüm OOV kelimelerini "unk" etiketiyle değiştir
def update_dataset(lines, vocab):
    new_lines = list()
    for line in lines:
        new_tokens = list()
        for token in line.split():
            if token in vocab:
                new_tokens.append(token)
            else:
                new_tokens.append('unk')
        new_line = ' '.join(new_tokens)
        new_lines.append(new_line)
    return new_lines
```

Şimdi, İngilizce veri kümesi için fonksiyonları çalıştıracağız, çıktıyı kaydedeceğiz ve 20 satırı görüntüleyeceğiz:

```python
# İngilizce veri kümesini yükle
filename = 'English.pkl'
lines = load_clean_sentences(filename)

# Kelime hazinesini hesapla
vocab = to_vocab(lines)
print('English Vocabulary: %d' % len(vocab))

# Kelime hazinesini küçült
vocab = trim_vocab(vocab, 5)
print('New English Vocabulary: %d' % len(vocab))

# OOV kelimelerini güncelle
lines = update_dataset(lines, vocab)

# Güncellenmiş veri kümesini kaydet
filename = 'english_vocab.pkl'
save_clean_sentences(lines, filename)

# Spot kontrol
for i in range(20):
    print("line", i, ":", lines[i])
```

Çıktı fonksiyonları önce elde edilen kelime hazinesi sıkıştırmasını gösterir:

```
English Vocabulary: 105357
New English Vocabulary: 41746
Saved: english_vocab.pkl
```

Ön işleme tabi tutulmuş veri kümesi kaydedilir. Çıktı fonksiyonu daha sonra aşağıdaki alıntılarda gösterildiği gibi 20 satırı görüntüler:

```
line 0 : resumption of the session
line 1 : i declare resumed the session of the european parliament adjourned on friday december and i would like once again to wish you a happy new year in the hope that you enjoyed a pleasant festive period
line 2 : although as you will have seen the dreaded millennium bug failed to materialise still the people in a number of countries suffered a series of natural disasters that truly were dreadful
line 3 : you have requested a debate on this subject in the course of the next few days during this partsession
```

Şimdi, Fransızca veri kümesi için fonksiyonları çalıştıracağız, çıktıyı kaydedeceğiz ve 20 satırı görüntüleyeceğiz:

```python
# Fransızca veri kümesini yükle
filename = 'French.pkl'
lines = load_clean_sentences(filename)

# Kelime hazinesini hesapla
vocab = to_vocab(lines)
print('French Vocabulary: %d' % len(vocab))

# Kelime hazinesini küçült
vocab = trim_vocab(vocab, 5)
print('New French Vocabulary: %d' % len(vocab))

# OOV kelimelerini güncelle
lines = update_dataset(lines, vocab)

# Güncellenmiş veri kümesini kaydet
filename = 'french_vocab.pkl'
save_clean_sentences(lines, filename)

# Spot kontrol
for i in range(20):
    print("line", i, ":", lines[i])
```

Çıktı fonksiyonları önce elde edilen kelime hazinesi sıkıştırmasını gösterir:

```
French Vocabulary: 141642
New French Vocabulary: 58800
Saved: french_vocab.pkl
```

Ön işleme tabi tutulmuş veri kümesi kaydedilir. Çıktı fonksiyonu daha sonra aşağıdaki alıntılarda gösterildiği gibi 20 satırı görüntüler:

```
line 0 : reprise de la session
line 1 : je declare reprise la session du parlement europeen qui avait ete interrompue le vendredi decembre dernier et je vous renouvelle tous mes vux en esperant que vous avez passe de bonnes vacances
line 2 : comme vous avez pu le constater le grand bogue de lan ne sest pas produit en revanche les citoyens dun certain nombre de nos pays ont ete victimes de catastrophes naturelles qui ont vraiment ete terribles
line 3 : vous avez souhaite un debat a ce sujet dans les prochains jours au cours de cette periode de session
```

# Sonuç
Bu bölüm, ham verilerin eğitilmeye hazır hale getirilmeden önce nasıl işlenmesi gerektiğini gösterdi. Veri kümeleri artık bir çeviri modeline eğitilmeye hazırdır. Fransızca veri kümesinin her satırı, çeviri yapılacak cümledir. İngilizce veri kümesinin her satırı, makine çeviri modelinin referans çevirisidir. Makine çeviri modeli, referans çeviriye uyumlu bir İngilizce çeviri adayı üretmelidir. BLEU, makine çeviri modelleri tarafından üretilen çeviri adaylarını değerlendirmek için bir yöntem sağlar.

---

