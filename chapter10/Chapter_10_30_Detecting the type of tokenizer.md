# Bu Örnekte İlk Adım: Tokenizer Türünü Belirleme

Bu örnekte, ilk adımımız tokenizer'ın bir WordPiece tokenizer olup olmadığını tespit etmek olacaktır. Bunu başarmak için, 6. Bölümde oluşturulan `merge.txt` ve `vocab.json` dosyalarını yükleyeceğiz:

## 1. Adım: merges.txt Dosyasını Yükleme
#1. Colab dosya yöneticisini kullanarak merges.txt dosyasını yükleyin
#2. GitHub'dan dosyasını indirin 
```python
!curl -L https://raw.githubusercontent.com/Denis2054/Transformers-for-NLP-and-Computer-Vision-3rd-Edition/main/Chapter10/merges.txt --output "merges.txt"
```

## 2. Adım: vocab.json Dosyasını Yükleme
#1. Colab dosya yöneticisini kullanarak vocab.json dosyasını yükleyin
#2. GitHub'dan dosyasını indirin 
```python
!curl -L https://raw.githubusercontent.com/Denis2054/Transformers-for-NLP-and-Computer-Vision-3rd-Edition/main/Chapter10/vocab.txt --output "vocab.json"
```

Şimdi, bir Hugging Face `RobertaTokenizer` import edelim:
```python
from transformers import RobertaTokenizer
tokenizer = RobertaTokenizer.from_pretrained("/content", max_length=512)
```
Bu kod, `/content` dizininden önceden eğitilmiş bir `RobertaTokenizer` modelini yükler ve maksimum girdi uzunluğunu 512 olarak ayarlar.

## Tokenizer Türünü Belirleme
```python
# Kelime hazinesini al
vocab = tokenizer.get_vocab()

# WordPiece veya BPE olup olmadığını kontrol et
is_wordpiece = any(token.startswith('##') for token in vocab)

# Tokenizer türünü yazdır
if is_wordpiece:
    print("Tokenizer type: WordPiece")
else:
    print("Tokenizer type: BPE")
```
Bu kod, tokenizer'ın kelime hazinesini alır ve içinde `##` önekiyle başlayan token olup olmadığını kontrol eder. Eğer böyle bir token varsa, tokenizer'ın WordPiece olduğu anlaşılır; yoksa BPE'dir.

Çıktı, bunun bir BPE tokenizer olduğunu gösterir. Bu örnek basitleştirilmiştir ve tokenizer'ın yalnızca BPE veya WordPiece olabileceği varsayılmıştır. Ayrıca, 6. Bölümde eğitildiği için bunun bir BPE olduğu kesindir.

## Hugging Face Platformunda Eğitilmiş Bir Tokenizer Yükleme
```python
from transformers import BertTokenizer

# BERT tokenizer modelini yükle
model_name = 'bert-base-uncased'
tokenizer = BertTokenizer.from_pretrained(model_name)

# Kelime hazinesini al
vocab = tokenizer.get_vocab()
```
Bu kod, Hugging Face platformunda önceden eğitilmiş bir `BertTokenizer` modelini yükler.

## Tokenizer Türünü Tekrar Belirleme
```python
# WordPiece veya başka bir tokenleştirme türü kullanılıp kullanılmadığını kontrol et
is_wordpiece = any(token.startswith('##') for token in vocab)

# Tokenizer türünü yazdır
if is_wordpiece:
    print("Tokenizer type: WordPiece")
else:
    print("Tokenizer type: BPE")
```
Bu kod, daha önce olduğu gibi tokenizer'ın WordPiece olup olmadığını kontrol eder.

Bu sefer, `##` öneki tespit edildiği için bunun bir WordPiece tokenizer olduğu anlaşılır.

## Kelime Hazinesini Yazdırma
```python
# Kelime hazinesini yazdır
for token, id in vocab.items():
    print(f'{token}: {id}')
```
Bu kod, kelime hazinesindeki her token'ı ve onun kimliğini yazdırır.

Çıktı, `##` önekinin varlığını gösterir, bu da alt kelimenin bir kelimenin başlangıcı olmadığını belirtir.

## Verileri Tabulate Kütüphanesini Kullanarak Görüntüleme
Son olarak, verileri `tabulate` kütüphanesini kullanarak görüntüleyebiliriz.

---

