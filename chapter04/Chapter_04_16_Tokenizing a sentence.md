# Makine Çevirmeni Hazır
Makine çevirmenimiz bir cümleyi tokenize etmeye hazır. Bu not defteri, Trax tarafından önceden işlenmiş olan kelime hazinesini kullanıyor. Ön işleme yöntemi, bu bölümün "WMT Veri Kümesini Ön İşleme" bölümünde açıklanan yönteme benzer. Cümle şimdi tokenize edilecek:

# Cümleyi Tokenize Etme
```python
sentence = 'I am only a machine but I have machine intelligence.'
tokenized = list(trax.data.tokenize(iter([sentence]),  # Akış üzerinde işlem yapar.
                                   vocab_dir='gs://trax-ml/vocabs/', 
                                   vocab_file='ende_32k.subword'))[0]
```
Şimdi cümleyi çözmeye ve bir çeviri üretmeye hazırız.

# Kod Açıklaması

1. `sentence = 'I am only a machine but I have machine intelligence.'` 
   - Bu satır, çevrilecek cümleyi tanımlıyor.

2. `tokenized = list(trax.data.tokenize(iter([sentence]), ...))`
   - `trax.data.tokenize` fonksiyonu, cümleyi tokenize etmek için kullanılıyor.
   - `iter([sentence])`: Cümleyi bir iterable yapısına dönüştürür. `trax.data.tokenize` fonksiyonu akış üzerinde çalıştığı için bu gereklidir.

3. `vocab_dir='gs://trax-ml/vocabs/'`
   - `vocab_dir` parametresi, kelime hazinesinin bulunduğu dizini belirtir.

4. `vocab_file='ende_32k.subword'`
   - `vocab_file` parametresi, kelime hazinesi dosyasının adını belirtir.

5. `list(...)[0]`
   - `trax.data.tokenize` fonksiyonu bir iterable döndürür. `list` fonksiyonu bu iterable'ı bir liste yapısına dönüştürür ve `[0]` indeksi ilk (ve bu durumda tek) elemanı alır.

Bu kod, belirtilen cümleyi `ende_32k.subword` kelime hazinesini kullanarak tokenize eder ve sonucu `tokenized` değişkenine atar.

---

