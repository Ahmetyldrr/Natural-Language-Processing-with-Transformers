# BPE (Byte Pair Encoding) Çevirisi

BPE, bireysel karakterlerden oluşan bir kelime haznesi ile başlar. Daha sonra ardışık karakterlerin en sık çiftini birleştirir. Bir hiperparametre, işlemin kaç kez tekrarlanacağını belirler. Sonuç, bireysel bir karakter, alt kelimeler veya kelimeler olabilen birleştirilmiş karakterler kümesidir. Sonuç, örneğin 6. Bölüm'de olduğu gibi merge.txt adlı bir birleştirme dosyasında saklanır. İkinci bir dosya, vocab.json (örneğin, 6. Bölüm'de olduğu gibi), benzersiz kimlikleri (bir tamsayı) olan alt kelimelerin sözlüğünü içerir. Dizi, tokenleştirme işlemi sırasında birleştirme sözlüğünde bulunan alt kelimelere ayrılır. İşlem yinelemelidir. Tokenleştirici, n kez daha büyük alt kelimeler bulmaya çalışacaktır. En iyi sonuç elde edildiğinde, yinelemeli olarak birleştirilen alt kelimeler ve tokenleştiriciler, vocab.json'da bulunan alt kelime kimlik bilgilerini kullanarak alt kelimeye bir kimlik atar. 6. Bölüm'ün kodunu tekrar gözden geçirmek isteyebilirsiniz. Seçtiğiniz bir korpusu seçebilir, tokenleştiriciyi eğitebilir, modeli eğitebilir ve tokenleştirme işleminin bir transformer modelinin çıktısı üzerindeki etkisini ölçebilirsiniz.

Python kodları bulunmamaktadır, ancak işlemin adımlarını açıklayan bir örnek kod aşağıdaki gibi olabilir:

### Örnek Kod

```python
# Gerekli kütüphaneleri içe aktarma
import json

# Birleştirme işlemini gerçekleştiren fonksiyon
def merge_characters(characters, num_merges):
    # İlk kelime haznesini oluştur
    vocab = set(characters)
    
    # Belirtilen sayıda birleştirme işlemini gerçekleştir
    for _ in range(num_merges):
        # Ardışık karakter çiftlerini say
        pair_counts = {}
        for i in range(len(characters) - 1):
            pair = (characters[i], characters[i + 1])
            if pair in pair_counts:
                pair_counts[pair] += 1
            else:
                pair_counts[pair] = 1
        
        # En sık çiftleri birleştir
        max_pair = max(pair_counts, key=pair_counts.get)
        vocab.add(max_pair[0] + max_pair[1])
        characters = characters.replace(max_pair[0] + max_pair[1], '')
        characters = characters.replace(max_pair[0], max_pair[0] + max_pair[1])
        characters = characters.replace(max_pair[1], '')
    
    return vocab

# Kelime haznesini json dosyasına yazma
def save_vocab(vocab, filename):
    vocab_dict = {word: i for i, word in enumerate(vocab)}
    with open(filename, 'w') as f:
        json.dump(vocab_dict, f)

# Örnek kullanım
characters = 'örnek karakter dizisi'
num_merges = 10
vocab = merge_characters(characters, num_merges)
save_vocab(vocab, 'vocab.json')
```

### Kod Açıklaması

1. `merge_characters` fonksiyonu, belirtilen sayıda birleştirme işlemini gerçekleştirerek kelime haznesini oluşturur.
   - İlk olarak, bireysel karakterlerden oluşan kelime haznesini oluşturur.
   - Daha sonra, ardışık karakter çiftlerini sayar ve en sık çiftleri birleştirir.
   - Bu işlem, belirtilen sayıda tekrarlanır.

2. `save_vocab` fonksiyonu, oluşturulan kelime haznesini json dosyasına yazar.
   - Kelime haznesini, her kelimeye benzersiz bir kimlik atayarak bir sözlüğe dönüştürür.
   - Bu sözlüğü json formatında belirtilen dosyaya yazar.

3. Örnek kullanımda, `merge_characters` fonksiyonu ile kelime haznesi oluşturulur ve `save_vocab` fonksiyonu ile 'vocab.json' dosyasına yazılır.

---

