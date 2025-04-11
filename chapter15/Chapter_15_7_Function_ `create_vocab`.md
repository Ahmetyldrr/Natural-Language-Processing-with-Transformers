# Giriş: Metin ve kelime haznesi boyutu
# Çıkış: Metindeki en sık kullanılan 'vocab_size' kadar kelimeyi benzersiz tam sayılara eşleyen bir kelime haznesi

İngilizce paragrafın birebir Türkçe çevirisi aşağıdaki gibidir:

Giriş: Metin ve bir kelime haznesi boyutu 
Çıkış: Metindeki en yaygın 'vocab_size' kadar kelimeyi benzersiz tam sayılara eşleyen bir kelime haznesi

Python kodları bulunmadığından ötürü herhangi bir kod açıklaması yapılmamıştır. Eğer bir python kodu verilseydi, kodu satır satır açıklayacaktım.

Örneğin eğer aşağıdaki gibi bir python kodu verilseydi:

```python
def create_vocabulary(text, vocab_size):
    # kelimeleri say
    word_counts = {}
    for word in text.split():
        if word not in word_counts:
            word_counts[word] = 0
        word_counts[word] += 1
    
    # en sık kullanılan kelimeleri bul
    sorted_word_counts = sorted(word_counts.items(), key=lambda x: x[1], reverse=True)
    vocab = {}
    for i, (word, count) in enumerate(sorted_word_counts[:vocab_size]):
        vocab[word] = i
    
    return vocab
```

# Kod Açıklaması

## Fonksiyon Tanımlama
```python
def create_vocabulary(text, vocab_size):
```
Bu satır `create_vocabulary` adında bir fonksiyon tanımlar. Bu fonksiyon iki parametre alır: `text` ve `vocab_size`.

## Kelimeleri Sayma
```python
word_counts = {}
for word in text.split():
    if word not in word_counts:
        word_counts[word] = 0
    word_counts[word] += 1
```
Bu bölüm, verilen `text` içindeki her kelimenin kaç kez geçtiğini sayar. 
- `text.split()`: Metni boşluklardan ayırarak kelimelere böler.
- `word_counts` sözlüğü her kelimenin sayısını tutar.

## En Sık Kullanılan Kelimeleri Bulma
```python
sorted_word_counts = sorted(word_counts.items(), key=lambda x: x[1], reverse=True)
```
Bu satır, `word_counts` sözlüğündeki kelimeleri sayılarına göre büyükten küçüğe sıralar.

## Kelime Haznesi Oluşturma
```python
vocab = {}
for i, (word, count) in enumerate(sorted_word_counts[:vocab_size]):
    vocab[word] = i
```
Bu bölüm, sıralanmış kelimelerin ilk `vocab_size` tanesini alır ve her birine benzersiz bir tam sayı (`i`) atar.

## Kelime Haznesini Dönme
```python
return vocab
```
Oluşturulan `vocab` sözlüğünü döndürür. Bu sözlük, metindeki en sık kullanılan `vocab_size` kadar kelimeyi benzersiz tam sayılara eşler.

---

