# Çeviri
Bazen, bir kelime bir metinde olabilir, ancak sözlükte olmayabilir. Bu, sonuçları çarpıtacaktır. Hadi pie ve logic kelimelerini ele alalım: 
```python
word1 = "pie"
word2 = "logic"
print("Similarity", similarity(word1, word2), word1, word2)
```
"pie" kelimesi sözlükte değil: "pie" kelimesi sözlükte mevcut değil
Similarity 0 pie logic 
"pie" kelimesinin tokenize edilmiş bir sözlükte olacağını varsayabiliriz. Peki ya değilse veya başka bir kelime değilse? 
"pie" kelimesi metin dosyasında değil. Bu nedenle, ardışık düzenimizde sözlükte olmayan kelimeleri tespit eden ve düzeltmeler veya alternatifler uygulayan fonksiyonlar bulunmalıdır. 
Ayrıca, veri kümelerinde önemli olabilecek kelimeleri tespit eden fonksiyonlara da sahip olmalıyız. 
Örneğin, bir proje yöneticisi, bilinmeyen kelimeleri tespit etmek için yüzlerce belgeyi tokenizer üzerinden çalıştırabilir ve bu kelimeleri analiz etmek için bir dosyada saklayabilir. 
Bu sadece bir örnek; her proje spesifik kalite kontrol eylemleri gerektirir. Şimdi nadir kelimelerle karşılaştığımız problemi görelim.

# Python Kodlarının Açıklaması

1. `word1 = "pie"` : "word1" değişkenine "pie" değerini atar.
2. `word2 = "logic"` : "word2" değişkenine "logic" değerini atar.
3. `print("Similarity", similarity(word1, word2), word1, word2)` : 
   - `similarity(word1, word2)` : "word1" ve "word2" arasındaki benzerliği hesaplar. 
   - `print()` : Hesaplanan benzerlik değerini, "word1" ve "word2" yi ekrana yazdırır.

Not: `similarity()` fonksiyonunun tanımı verilmediği için, bu fonksiyonun ne yaptığını tam olarak bilemiyoruz. Ancak, iki kelime arasındaki benzerliği hesapladığını varsayıyoruz.

---

