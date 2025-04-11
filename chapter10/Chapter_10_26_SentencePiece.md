# A SentencePiece Tokenizer Eklenmesi
Bir SentencePiece tokenizer, Unigram dil modeli tokenizer'ına bir BPE yaklaşımı ekler. Ön tokenleştirici gerektirmez ve ham verileri işleyebilir. Aşağıdaki örnekte, ön tokenleştiricisi olmayan küçük bir örnek eğitiyoruz:

## Gerekli Modüllerin İçe Aktarılması
İlk olarak, gerekli modülleri içe aktarıyoruz:
```python
import sentencepiece as spm
import random
```
## Küçük Bir Örnek Korpus Oluşturma
Ardından, küçük bir örnek korpus oluşturuyoruz:
```python
# Temel bir korpus tanımlama
basic_corpus = [
    "Subword tokenizers break text sequences into subwords.",
    "This sentence is another part of the corpus.",
    "Tokenization is the process of breaking text down into smaller units.",
    "These smaller units can be words, subwords, or even individual characters.",
    "Transformer models often use subword tokenization."
]
```
## Veri Artırma
Rastgele bazı veri artırma işlemleri gerçekleştiriyoruz:
```python
# Temel korpusdan cümleleri tekrarlayarak daha büyük bir korpus oluşturma
corpus = [random.choice(basic_corpus) for _ in range(10000)]
```
## Korpusun Kaydedilmesi
Korpus'u kaydediyoruz:
```python
# Korpus'u bir metin dosyasına yazma
with open('large_corpus.txt', 'w') as f:
    for sentence in corpus:
        f.write(sentence + '\n')
```
## Tokenizer'ın Eğitilmesi
Tokenizer'ı eğitiyoruz:
```python
# SentencePiece modelini eğitme
spm.SentencePieceTrainer.train(input='large_corpus.txt', model_prefix='m', vocab_size=88)
```
## Eğitilen Modelin Yüklenmesi
Eğitilen modeli yüklüyoruz:
```python
# Eğitilen modeli yükleme
sp = spm.SentencePieceProcessor()
sp.load('m.model')
```
## Hedef Dizinin Tokenleştirilmesi
Hedef dizini tokenleştiriyoruz:
```python
# Orijinal cümleyi tokenleştirme
tokens = sp.encode_as_pieces("Subword tokenizers break text sequences into subwords.")
print(tokens)
```
Tekrar, cümle ve kelime tokenleştiricilerinin çıktısından farklı olan alt kelimeleri elde ediyoruz: `['_', 'S', 'ubword', '_tokeniz', 'ers', '_break', '_', 'te', 'x', 't', '_se', 'q', 'u', 'ence', 's', '_in', 'to', '_subwords', '.']`

## Sonuç
İki ana alt kelime tokenleştiricisini inceledik, ancak BPE veya WordPiece değil. Ancak, cümle ve kelime tokenleştiricilerinden farklı olarak, farklı yaklaşımlar aracılığıyla alt kelimeler elde ettiğimizi görebilirsiniz. Her biri kendi özel yaklaşımına sahip başka alt kelime tokenleştiricileri de vardır. Tokenleştirici seçimi her proje türü için bir karardır. 

## İlgili Bölüm
6. Bölümdeki "Step 3: Training a tokenizer" bölümünde, RoBERTa aracılığıyla sıfırdan bir Transformer ön eğitimi yaptık. Bu bölümde, WordPiece tokenleştirmesine odaklanacağız. WordPiece ile kodda alt kelime tokenleştirmesi oluşturmadan önce, BPE eğitiminin özetini yapalım.

---

