# Çok Kelimeli Tokenization

Çok kelimeli tokenization, dizileri kelimelere ayırır, ancak "cannot" gibi çok kelimeli ifadeleri korur:

```python
# Çok Kelimeli İfade Tokenization 
tokenizer = MWETokenizer()
tokenizer.add_mwe(("can", "not"))
text = "I cannot go to the movies today"
tokens = tokenizer.tokenize(text.split())
print("Çok Kelimeli İfade Tokenization:")
print(tokens)
print()
```

Bu kodun açıklaması:

1. `tokenizer = MWETokenizer()`: `MWETokenizer` sınıfından bir nesne oluşturur. Bu nesne, çok kelimeli ifadeleri tanımak için kullanılır.
2. `tokenizer.add_mwe(("can", "not"))`: `add_mwe` methodunu kullanarak, "can" ve "not" kelimelerini bir arada tanıyarak "cannot" ifadesini oluşturmasını sağlar.
3. `text = "I cannot go to the movies today"`: İşlenecek metni tanımlar.
4. `tokens = tokenizer.tokenize(text.split())`: Metni kelimelere ayırır ve `tokenize` methodunu kullanarak çok kelimeli ifadeleri tanır.
   - `text.split()`: Metni boşluk karakterlerinden ayırarak bir kelime listesi oluşturur.
   - `tokenizer.tokenize(...)`: Bu kelime listesini işleyerek çok kelimeli ifadeleri birleştirir.
5. `print("Çok Kelimeli İfade Tokenization:")`: Başlık yazdırır.
6. `print(tokens)`: Tokenize edilmiş kelime listesini yazdırır.
7. `print()`: Boş bir satır yazdırarak çıktıyı biçimlendirir.

Çıktısı:
```
Çok Kelimeli İfade Tokenization:
['I', 'cannot', 'go', 'to', 'the', 'movies', 'today']
```

# Cümle ve Kelime Tokenizer'ları

Cümle ve kelime tokenizer'ları hafife alınmamalıdır, çünkü son zamanlardaki büyük ölçekli dil modelleri alt kelime tokenizer'larını tercih etmektedir. Örneğin, bazı durumlarda, cümle ve kelime tokenizer'ları, transformer modeli eğitimi için etiketli veri kümeleri oluşturmak amacıyla bir ön işleme hattının parçası olabilir. Ancak, bazı durumlarda, alt kelime tokenizer'ları ham verileri işlemek için yeterli olabilir. Şimdi alt kelime tokenizer'larını inceleyeceğiz.

---

