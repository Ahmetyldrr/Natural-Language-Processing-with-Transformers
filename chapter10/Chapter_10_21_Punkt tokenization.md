# Punkt Cümle Tokenizationu

Aşağıda verilen kod, önceden denetimsiz ön eğitimden geçen bir Punkt tokenizer'ın nasıl cümlelere ayırdığını göstermektedir. Etiketlere ihtiyacı yoktur:

```python
# Punkt Cümle Tokenizer'ı oluşturma
tokenizer = PunktSentenceTokenizer()

# Tokenize edilecek metin
text = "A tokenizer can be trained. Many tokenizers aren't trained."

# Metni cümlelere ayırma
sentences = tokenizer.tokenize(text)

# Sonuçları yazdırma
print("Punkt Cümle Tokenization:")
print(sentences)
print()
```

PunktSentenceTokenizer() bireysel cümleler üretir:

Punkt Cümle Tokenization:
`['A tokenizer can be trained.', "Many tokenizers aren't trained."]`

# Kodun Açıklaması

1. `tokenizer = PunktSentenceTokenizer()`: Bu satır, `PunktSentenceTokenizer` sınıfından bir nesne oluşturur. Bu nesne, metni cümlelere ayırmak için kullanılır.

2. `text = "A tokenizer can be trained. Many tokenizers aren't trained."`: Bu satır, tokenize edilecek metni tanımlar.

3. `sentences = tokenizer.tokenize(text)`: Bu satır, tanımlanan metni `tokenizer` nesnesini kullanarak cümlelere ayırır.

4. `print("Punkt Cümle Tokenization:")`: Bu satır, sonuç başlığını yazdırır.

5. `print(sentences)`: Bu satır, cümlelere ayrılmış metni yazdırır.

6. `print()`: Bu satır, boş bir satır yazdırarak çıktıları daha okunabilir hale getirir.

# Çıktı

Punkt Cümle Tokenization:
`['A tokenizer can be trained.', "Many tokenizers aren't trained."]`

Bu çıktı, orijinal metnin iki cümleye ayrıldığını gösterir: "A tokenizer can be trained." ve "Many tokenizers aren't trained.".

---

