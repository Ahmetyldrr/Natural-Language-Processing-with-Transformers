# Programın Çıktısı: Cümlelerin Hazırlanması

Program şimdi bu bölümün "Pretraining Giriş Ortamını Hazırlama" kısmında açıklandığı gibi cümleleri oluşturacaktır:
```python
sentences = df.sentence.values 
```
# Cümlelere CLS ve SEP Tokenlarının Eklenmesi

BERT için her cümlenin başına ve sonuna CLS ve SEP tokenları eklenir:
```python
sentences = [ "[CLS] " + sentence + " [SEP]" for sentence in sentences]
```
Bu işlem aşağıdaki python koduyla gerçekleştirilir:
- `sentences` değişkenine `df.sentence.values` atanır. Bu, `df` adlı veri çerçevesindeki `sentence` sütunundaki tüm değerleri alır.
- Liste kavrama (list comprehension) kullanılarak her `sentence` (cümle) için:
  - Başına "[CLS] " (CLS tokenı, cümlenin başlangıcını temsil eder) eklenir.
  - Sonuna " [SEP]" (SEP tokenı, cümlenin sonunu temsil eder) eklenir.

# Etiketlerin Hazırlanması

Etiketler (`labels`) `df.label.values` ile alınır:
```python
labels = df.label.values
```
Bu, `df` adlı veri çerçevesindeki `label` sütunundaki tüm değerleri `labels` değişkenine atar.

# CLS ve SEP Tokenlarının Amacı

[CLS] ve [SEP] şimdi BERT modeli için bir cümlenin başlangıcını ve sonunu bulmak üzere eklenmiştir. 
- [CLS] tokenı, tüm giriş cümlelerinin başına eklenir ve sınıflandırma görevlerinde kullanılır.
- [SEP] tokenı, cümlenin sonunu belirtir ve özellikle birden fazla cümle işlendiğinde cümleleri ayırmak için kullanılır.

# Tokenizer'ın Aktif Hale Getirilmesi

Program şimdi tokenizer'ı aktif hale getirir. Tokenizer, metni BERT modelinin işleyebileceği bir forma dönüştürmek için kullanılır.

---

