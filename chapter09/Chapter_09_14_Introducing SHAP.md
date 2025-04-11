# Oyun Teorisi ve Shapley Değeri
Oyun teorisinde, bir Shapley değeri, toplam değerlerin "oyuncu"lar arasında marjinal katkı yoluyla dağıtımını ifade eder. Bir cümlede, kelimeler "oyuncu"lardır. Her kelimenin bir puanı olacaktır. Toplam puan, oyunun değeridir. Her kelimenin değeri, cümlenin tüm permütasyonları üzerinden hesaplanır. Amaç, her kelimenin cümlenin anlamını nasıl değiştirdiğini görmektir.

# Shapley Değerinin Hesaplanması
Örneğin, aşağıdaki cümlede yedi kelime vardır: "I love playing chess with my friends" Toplam permütasyon sayısı = 7! = 7x6x5x4x3x2x1 = 5040. Hemen anlaşılacağı üzere, SHAP uzun bir metin için zorlayıcı olacaktır. Ancak, nispeten kısa metinler için verimlidir. Bir oyunda (cümlenin) bir oyuncu (kelime) i için Shapley değerini hesaplamak için formül aşağıdaki gibidir:

Burada: φ (i'nin Shapley değeri) i'nin N koalisyonundaki değerinin v "eşit" olduğunu gösterir. Bu noktada, i'nin N koalisyonundaki marjinal katkısını φ bulacağımızı biliyoruz.

# Python Kodları ile SHAP Uygulaması
Python itertools kütüphanesini kullanarak döngüleri ve permütasyonları çalıştırmak için bir program yazacağız.

### Adım 1: Kelime Değerlerini ve Koalisyonları Tanımlama
```python
# SHAP with an Iterator
import itertools

# Kelimelerin temel puanlarını tanımla
words = {'I': 0.2, 'love': 0.6, 'playing': 0.5, 'chess': 0.4, 'with': 0.1, 'my': 0.3, 'friends': 0.4}

# Belirli kelime kombinasyonları için bonus puanları tanımla
bonus = {('I', 'love'): 0.3, ('love', 'playing'): 0.25, ('playing', 'chess'): 0.45, ('with', 'my', 'friends'): 0.35}
```

### Adım 2: Koalisyonun Toplam Değerini Hesaplayan Fonksiyonu Tanımlama
```python
# Koalisyonun toplam puanını hesaplayan fonksiyon
def total_score(coalition):
    score = sum(words[word] for word in coalition)
    for b in bonus.keys():
        if all(word in coalition for word in b):
            score += bonus[b]
    return score
```

### Adım 3: Bir Kelimenin Shapley Değerini Hesaplayan Fonksiyonu Tanımlama
```python
# Bir kelimenin Shapley değerini hesaplayan fonksiyon
def shapley_value(word):
    N = len(words)
    permutations = list(itertools.permutations(words))
    marginal_contributions = []
    counter = 0  # Sayaç başlatma
    for permutation in permutations:
        index = permutation.index(word)
        coalition_without_word = permutation[:index]
        coalition_with_word = permutation[:index + 1]
        marginal_contribution = total_score(coalition_with_word) - total_score(coalition_without_word)
        marginal_contributions.append(marginal_contribution)
        counter += 1  # Sayaç artırma
    print(f"Processed {counter} permutations")  # Sayaç yazdırma
    return sum(marginal_contributions)
```

### Adım 4: Her Kelimenin Shapley Değerini Hesaplamak
```python
# Her kelimenin Shapley değerini hesapla
for word in words:
    print(f"The Shapley value of '{word}' is {shapley_value(word)}")
```

### Çıktı
```
Processed 5040 permutations
The Shapley value of 'I' is 1764.0000000000798
Processed 5040 permutations
The Shapley value of 'love' is 4409.99999999998
Processed 5040 permutations
The Shapley value of 'playing' is 4283.999999999768
Processed 5040 permutations
The Shapley value of 'chess' is 3150.000000000016
Processed 5040 permutations
The Shapley value of 'with' is 1092.000000000074
Processed 5040 permutations
The Shapley value of 'my' is 2099.999999999982
Processed 5040 permutations
The Shapley value of 'friends' is 2604.0000000001683
```

Bu kodlar, her kelimenin cümleye olan marjinal katkısını hesaplamak için Shapley değerini kullanır.

---

