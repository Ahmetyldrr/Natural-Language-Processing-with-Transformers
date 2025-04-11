# WordPiece Sözlüğünün Token-ID Eşlemeleri

Bu bölüm, WordPiece sözlüğünün token-ID eşlemelerini incelemektedir. Etkileşimli bir arayüz oluşturmak, modülleri görüntülemek ve az önce tespit ettiğimiz tokenizer'ı içe aktarmak için tabulate modüllerini ve widget'ları içe aktarıyoruz: 
```python
from tabulate import tabulate 
import ipywidgets as widgets 
from IPython.display import display 
from transformers import BertTokenizer
```

## Model ve Tokenizer'ı Yükleme

Modeli ve tokenizer'ı yüklüyoruz: 
```python
# BERT tokenizer modelini yükle
model_name = 'bert-base-uncased' 
tokenizer = BertTokenizer.from_pretrained(model_name)
```

## Sözlüğü Alma

Sözlüğü alıyoruz: 
```python
# Sözlüğü al
vocab = tokenizer.get_vocab()
```

## Sözlüğü Liste Dönüştürme

Sözlüğü bir liste haline getiriyoruz: 
```python
# Sözlüğü tuple listesine dönüştür
vocab_list = list(vocab.items())
```

## Sözlüğü Sıralama ve Filtreleme

Sözlüğü sıralıyoruz ve etkileşimli arayüzümüz için bir widget ile filtre oluşturuyoruz: 
```python
# Token'a göre sözlüğü sırala
sorted_vocab = sorted(vocab_list, key=lambda x: x[0]) 
# Filtreleme için metin girişi widget'ı oluştur
filter_widget = widgets.Text(placeholder='Filter vocabulary')
```

## Sözlüğü Filtreleme ve Görüntüleme Fonksiyonu

Sözlüğü filtrelemek ve görüntülemek için bir fonksiyon oluşturuyoruz: 
```python
# Sözlüğü filtreleme ve görüntüleme fonksiyonu
def filter_vocabulary(filter_text):
    filtered_vocab = [word for word in sorted_vocab if word[0].startswith(filter_text)]
    table = tabulate(filtered_vocab, headers=['Token', 'ID'])
    display(widgets.HTML(table))
```

## Filtreyi Çağırma ve Görüntüleme

Son olarak, filtreyi çağırıyoruz ve görüntülüyoruz: 
```python
# Widget değeri değiştiğinde filtre fonksiyonunu çağır
filter_widget.observe(lambda event: filter_vocabulary(event.new), names='value') 
# Filtre widget'ını görüntüle
display(filter_widget)
```

Güzel bir filtre arayüzü görüntülenir: 
### Şekil 10.3: Arayüzümüzün filtresi

Bir karakter yazın, o karakterle başlayan kelimeler görünecektir. Örneğin, `t` yazınca, o harfle başlayan tüm token ID'leri aşağıdaki alıntıda gösterildiği gibi üretilecektir: 
...tomorrow 4826 ton 10228 tone 430… 

Başka bir filtre çalıştırmak için hücreyi yeniden çalıştırın. Token ID'lerini gözlemlemek için zaman ayırın ve sözlükte bulunan karakterleri, önekleri (##), kısmi kelimeleri ve kelimeleri görün. Bu, tokenleştiricilerin tokenleştirme sürecini nasıl kurduklarına dair iyi bir zihinsel temsil verecektir.

---

