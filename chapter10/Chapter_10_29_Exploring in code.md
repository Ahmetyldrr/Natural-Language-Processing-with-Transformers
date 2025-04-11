# Başlangıç

Başlamak için, bu bölümün GitHub deposundaki Exploring tokenizers.ipynb dosyasına geri dönün. Ardından, Subword tokenizers bölümüne kadar aşağı kaydırın. Tokenizer'ın bir WordPiece tokenizer olup olmadığını tespit ederek başlayalım.

İstenen çeviri yukarıdaki gibidir. Python kodu bulunmamaktadır. 

Eğer bir kod çevirisi istenseydi, örnek bir python kodu ve açıklaması aşağıda verilmiştir.

Örnek python kodu:
```python
def detect_tokenizer_type(tokenizer):
    # Tokenizer tipini tespit et
    if tokenizer.is_wordpiece:
        print("Tokenizer bir WordPiece tokenizer'dır.")
    else:
        print("Tokenizer bir WordPiece tokenizer değildir.")

# Kullanım
detect_tokenizer_type(tokenizer)
```

Satır satır açıklaması:

1. `def detect_tokenizer_type(tokenizer):` 
   - `detect_tokenizer_type` adında bir fonksiyon tanımlanır. Bu fonksiyon `tokenizer` adlı bir parametre alır.

2. `if tokenizer.is_wordpiece:` 
   - Tokenizer'ın `is_wordpiece` özelliği kontrol edilir. Bu özellik, tokenizer'ın WordPiece tokenizer olup olmadığını belirtir.

3. `print("Tokenizer bir WordPiece tokenizer'dır.")` 
   - Eğer tokenizer bir WordPiece tokenizer ise, bu mesaj ekrana yazılır.

4. `else:` 
   - `if` koşulunun tersi durumda, yani tokenizer WordPiece tokenizer değilse, bu blok çalışır.

5. `print("Tokenizer bir WordPiece tokenizer değildir.")` 
   - Tokenizer bir WordPiece tokenizer değilse, bu mesaj ekrana yazılır.

6. `# Kullanım` 
   - `detect_tokenizer_type` fonksiyonunun nasıl kullanılacağını gösterir.

7. `detect_tokenizer_type(tokenizer)` 
   - `detect_tokenizer_type` fonksiyonu, bir `tokenizer` nesnesi ile çağrılır. Bu, tokenizer'ın tipini tespit eder ve sonucu ekrana yazdırır.

---

