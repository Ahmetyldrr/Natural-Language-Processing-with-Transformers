# Cümle Tokenizasyonu
Cümle tokenizasyonu, bir metni ayrı cümlelere böler. Bir paragrafı veya belgeyi cümle birimlerine ayırır:

```python
# Cümle Tokenizasyonu örneği
text = "This is a sentence. This is another one."
sentences = sent_tokenize(text)
print("Cümle Tokenizasyonu:")
print(sentences)
print()
```

`sent_tokenize(text)` ifadesi, metni ayırıcılarla cümlelere böler:

# Cümle Tokenizasyonu:
`sent_tokenize(text)` fonksiyonu, verilen metni cümlelere ayırır ve bir liste olarak döndürür.

Çıktısı:
['This is a sentence.', 'This is another one.']

Türkçe Çevirisi:
['Bu bir cümledir.', 'Bu başka bir tanesidir.']

Kodun tamamının açıklaması:
1. `text = "This is a sentence. This is another one."` : Bu satır, üzerinde işlem yapılacak metni tanımlamaktadır. 
2. `sentences = sent_tokenize(text)`: Bu satır, tanımlanan `text` değişkenindeki metni `sent_tokenize()` fonksiyonu ile cümlelere ayırır ve `sentences` değişkenine atar.
3. `print("Cümle Tokenizasyonu:")`: Bu satır, ekrana "Cümle Tokenizasyonu:" yazdırır.
4. `print(sentences)`: Bu satır, `sentences` değişkeninin içeriğini, yani cümlelere ayrılmış metni ekrana yazdırır.
5. `print()`: Bu satır, boş bir satır yazdırarak çıktıları daha okunabilir hale getirir.

`sent_tokenize()` fonksiyonu, NLTK (Natural Language Toolkit) kütüphanesinin bir parçasıdır ve metni cümlelere ayırmak için kullanılır. Bu fonksiyonun çalışması için NLTK kütüphanesinin ilgili modeli indirmeniz gerekebilir.

---

