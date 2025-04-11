# Google Brain'in Trax ile Uygulaması

Google Brain, Trax ile Transformer'ın ana akım, yıkıcı ve sezgisel bir uygulamasını üretti. Program şimdi birkaç satırda çeviriyi de-tokenize ediyor ve gösteriyor:

```python
tokenized_translation = tokenized_translation[0][:-1]  # Batch ve EOS'u kaldır.
translation = trax.data.detokenize(tokenized_translation,
                                   vocab_dir='gs://trax-ml/vocabs/',
                                   vocab_file='ende_32k.subword')
print("The sentence:", sentence)
print("The translation:", translation)
```

* `tokenized_translation = tokenized_translation[0][:-1]`: Bu satır, `tokenized_translation` değişkeninin ilk elemanını alır ve son elemanını (`EOS` tokeni) kaldırır.
* `trax.data.detokenize()`: Bu fonksiyon, tokenize edilmiş çeviriyi geri alır ve orijinal metni oluşturur.
	+ `vocab_dir` parametresi, kelime haznesinin bulunduğu dizini belirtir.
	+ `vocab_file` parametresi, kelime haznesi dosyasının adını belirtir.
* `print()` fonksiyonları, orijinal cümleyi ve çeviriyi yazdırır.

Çıktı oldukça etkileyici:

The sentence: I am only a machine but I have machine intelligence.
The translation: Ich bin nur eine Maschine, aber ich habe Maschinenübersicht.

Transformer, "machine intelligence" ifadesini "Maschinenübersicht" olarak çevirdi. "Maschinenübersicht" ifadesini "Maschin" (makine) + "übersicht" (görüş veya bakış) olarak ayırırsak, şunu görebiliriz:
* "über" kelimesi tam olarak "üst" veya "öte" anlamına gelir.
* "sicht" kelimesi "görüş" veya "bakış" anlamına gelir.

Transformer, bir makine olmasına rağmen vizyonu olduğunu söylüyor. Makine zekası transformerlar aracılığıyla büyüyor, ancak bu insan zekası değil. Makineler, kendi zekalarına sahip olarak dil öğreniyorlar.

Google Trax, modelleri oluşturmak ve çalıştırmak için bir araç seti sağlar. Şimdi, Google Translate'i keşfedelim.

---

