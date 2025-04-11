# Özetleme Fonksiyonu Oluşturma

İlk olarak, `summarize` adında bir özetleme fonksiyonu oluşturalım. Bu şekilde, özetlemek istediğimiz metinleri fonksiyonumuza göndereceğiz. Fonksiyon iki parametre alır. İlk parametre `preprocess_text`, özetlenecek metindir. İkinci parametre `ml`, özetlenen metnin maksimum uzunluğudur. Her iki parametre de fonksiyonu her çağırdığınızda gönderdiğiniz değişkenlerdir: 
```python
def summarize(text, ml):
```
`text.strip` fonksiyonu, metni gereksiz karakterlerden arındırır, örneğin:
- Boşluk ( )
- Sekme ( \t )
- Yeni satır ( \n )
- Satır başı ( \r )

Bu durumda, içerik metni yeni satır karakterinden arındırılır:
```python
preprocess_text = text.strip().replace("\n", "")
```
Daha sonra, giriş metnine inovatif T5 görev ön eki "summarize" uygularız:
```python
t5_prepared_Text = "summarize: " + preprocess_text
```
T5 modeli, görev ne olursa olsun, ön ek + giriş dizisi yaklaşımı yoluyla birleşik bir yapıya sahiptir. Basit görünebilir, ancak NLP transformer modellerini evrensel eğitim ve sıfır-shot downstream görevlerine yaklaştırır.

İşlenmiş (arındırılmış) ve hazırlanmış metni (görev ön eki) wrapper ile görüntüleyebiliriz:
```python
wrapped_t5_prepared_Text = textwrap.fill(t5_prepared_Text, width=70)
print(wrapped_t5_prepared_Text)
```
Basit, değil mi? RNN'lerden ve CNN'lerden transformerlara geçmek 35 yıldan fazla sürdü. Daha sonra, spesifik görevler için tasarlanmış transformerlardan, ince ayar gerektirmeyen çoklu görev modellerine geçmek, dünyanın en parlak araştırma takımlarından bazılarını gerektirdi. Son olarak, Google araştırma takımı, çözülecek NLP problemini belirten bir ön ek içeren bir transformer giriş metni için standart bir format oluşturdu. Bu oldukça büyük bir başarı!

Görüntülenen çıktı, önceden işlenmiş ve hazırlanmış metni içerir:
```
Özetlenecek metin: We hold these truths to be self-evident, that all
men are created equal,that they are endowed by their Creator with
certain unalienable Rights,that among these are Life, Liberty, and the
pursuit of Happiness.That to secure these rights, Governments are…
```
"summarize" ön eki, çözülecek görevi belirtir. Metin şimdi token ID'lerine kodlanır ve bunları torch tensorları olarak döndürür:
```python
tokenized_text = tokenizer.encode(t5_prepared_Text, return_tensors="pt").to(device)
```
Kodlanmış metin, Getting started with T5 bölümünde açıkladığımız parametrelerle bir özet oluşturmak üzere modele gönderilmeye hazırdır:
```python
# Özetle
summary_ids = model.generate(tokenized_text,
                                      num_beams=4,
                                      no_repeat_ngram_size=2,
                                      min_length=30,
                                      max_length=ml,
                                      early_stopping=True)
```
Işın sayısı, içe aktardığımız modeldekiyle aynı kalır. Ancak, `no_repeat_ngram_size` 3 yerine 2'ye düşürülmüştür. Oluşturulan çıktı şimdi tokenizer ile çözülür:
```python
output = tokenizer.decode(summary_ids[0], skip_special_tokens=True)
return output
```
Özetleme fonksiyonunu içe aktardık, başlattık ve tanımladık. Şimdi T5 modelini genel bir konu ile deneyelim.

---

