# Önceki Bölümde Anlatılanlar
Önceki bölümde, bir WordPiece tokenleştiricisinin sözlüğünün token-ID eşlemelerini inceledik. Bu bölümde ise tam tersini yapacağız: bir kelime alıp onu tokenleştirilmiş token-ID eşlemelerine ayıracağız. Kelimelerden tokenlere geçeceğiz.

# Transformer Modelinin Yüklenmesi
İlk olarak transformer modelini yüklüyoruz:
```python
# BERT tokenleştirici modelini yükle
model_name = 'bert-base-uncased'
tokenizer = BertTokenizer.from_pretrained(model_name)
```
Burada `BertTokenizer.from_pretrained` methodu kullanılarak önceden eğitilmiş BERT tokenleştirici modeli yükleniyor.

# Kelime Tokenleştirme Fonksiyonu
Kelime tokenleştirme ve çıktı gösterme fonksiyonunu tanımlıyoruz:
```python
# Kelime tokenleştirme ve bilgi sağlama fonksiyonu
def tokenize_word(word):
    # Kelimeyi tokenleştir
    tokens = tokenizer.tokenize(word)
    # Kelimenin doğrudan bulunduğunu veya alt kelime işleminin sonucu olduğunu kontrol et
    if len(tokens) == 1 and tokens[0] == word:
        process = "Doğrudan"
    else:
        process = "Alt Kelime"
    # Kelime ve işlem bilgilerini göster
    print("Kelime:", word)
    print("Tokenleştirilmiş Tokenler:", tokens)
    print("Tokenleştirme İşlemi:", process)
```
Bu fonksiyon, bir kelimeyi tokenleştirir ve tokenleştirme işleminin doğrudan mı yoksa alt kelime işlemi mi olduğunu belirler.

# Kelime Girişi için Widget Oluşturma
Kelime girişi için bir widget oluşturuyoruz:
```python
# Kelime girişi için widget oluştur
word_input = widgets.Text(description='Kelime Girin:')
display(word_input)
```
Bu, kullanıcıların bir kelime girmelerini sağlayan bir metin girişi alanı oluşturur.

# Olay İşleyici Oluşturma
Kelime tokenleştirme için bir olay işleyici oluşturuyoruz:
```python
# Widget için olay işleyici oluştur
def on_button_click(b):
    word = word_input.value
    tokenize_word(word)
```
Bu fonksiyon, butona tıklandığında kelimeyi tokenleştirir.

# Tokenleştirme Butonu Oluşturma
Tokenleştirme işlemini tetiklemek için bir buton oluşturuyoruz:
```python
# Tokenleştirme işlemini tetiklemek için buton widget'ı oluştur
button = widgets.Button(description="Tokenleştir")
button.on_click(on_button_click)
display(button)
```
Bu butona tıklandığında, `on_button_click` fonksiyonu çağrılır ve kelime tokenleştirilir.

# Örnekler
Eğer `dsdf` gibi rastgele bir dizi girersek, `ds` kelimesinin sözlükte bulunduğunu ve `##df`'nin bir kelimenin başlangıcı olmadığını görebiliriz. `dsdf` bir alt kelimedir:
```
Kelime: dsdf
Tokenleştirilmiş Tokenler: ['ds', '##df']
Tokenleştirme İşlemi: Alt Kelime
```
Eğer `word` girersek, kelimenin sözlükte bulunduğunu görebiliriz:
```
Kelime: word
Tokenleştirilmiş Tokenler: ['word']
Tokenleştirme İşlemi: Doğrudan
```
Şimdi, `amoeboid` gibi daha zor bir kelime girersek:
```
Kelime: amoeboid
Tokenleştirilmiş Tokenler: ['am', '##oe', '##bo', '##id']
Tokenleştirme İşlemi: Alt Kelime
```
`amoeboid` kelimesi, çoklu ön eklerle alt kelimelere ayrılır. `am` tokeni, `amoeboid` içinde çok anlamlılık (aynı dizi için birden fazla anlam) problemini düşük seviyede ortaya çıkarır. `am` bir ön ek, `I + am` gibi bir kelime veya `am + bush` gibi bir alt kelime olabilir. Dikkat katmanları, bir tokenin `am`'ini başka bir `am` ile ilişkilendirebilir, var olmayan ilişkiler yaratabilir. Karmaşık kelimelerdeki çok anlamlılık, zorlu bir problemdir.

# Sonuç
Alt kelime tokenleştiricilerinin bile nadir ve karmaşık kelimelerle ilgili problemler yaşayabileceğini görebiliriz. Bu kelimeler, eğitim veri kümelerinde sıkça karşılaşılmayabilir, bu nedenle küçümsenebilirler. Ancak, bu kelimeler tıbbi veya hukuki metinlerde kritik olabilir. Transformer modellerinin temel taşı olan tokenleştirme, onların doğruluğunu ve performansını derinden etkileyecektir.

---

