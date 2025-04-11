# Kelime Tokenizasyonu

Kelime tokenizasyonu, bir diziyi (örneğin, cümle ve metni) bireysel kelimelere ayırır. Tırnak işaretleri, sekmeler ve yeni satırlar gibi noktalama işaretlerini ve boşluk karakterlerini algılar:

```python
# Kelime Tokenizasyonu örneği
sentence = "This sentence contains several words."
words = word_tokenize(sentence)
print("Word Tokenization:")
print(words)
print()
```

`word_tokenize(Sentence)` komutu, ayırıcılarla birlikte kelimeleri üretir:

# Çıktı
Word Tokenization:
['This', 'sentence', 'contains', 'several', 'words', '.']

## Kod Açıklaması

1. `sentence = "This sentence contains several words."` : Bu satır, bir cümleyi string olarak tanımlar.
2. `words = word_tokenize(sentence)` : Bu satır, `word_tokenize` fonksiyonunu kullanarak cümleyi kelimelere ayırır. `word_tokenize` fonksiyonu, NLTK (Natural Language Toolkit) kütüphanesinin bir parçasıdır ve bir cümleyi kelimelere ayırma işlemini gerçekleştirir.
3. `print("Word Tokenization:")` : Bu satır, "Word Tokenization:" başlığını ekrana yazdırır.
4. `print(words)` : Bu satır, kelimelere ayrılmış cümleyi ekrana yazdırır.
5. `print()` : Bu satır, boş bir satır yazdırarak çıktının daha okunabilir olmasını sağlar.

### NLTK ve `word_tokenize` Fonksiyonu

`word_tokenize` fonksiyonu, NLTK kütüphanesinin bir parçasıdır. NLTK, doğal dil işleme görevleri için kullanılan popüler bir Python kütüphanesidir. `word_tokenize` fonksiyonu, bir cümleyi kelimelere ayırma işlemini gerçekleştirir ve bu kelimeleri bir liste olarak döndürür. 

Örneğin, "This sentence contains several words." cümlesini `['This', 'sentence', 'contains', 'several', 'words', '.']` listesine çevirir. Noktalama işaretleri de bu listedeki elemanlardan biridir.

---

