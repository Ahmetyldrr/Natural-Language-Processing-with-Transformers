# Tekrarlayan Katmanların Çalışması ve Zaman Karmaşıklığı

Tekrarlayan katmanlar bu şekilde çalışmaz. O(n) dir, n doğrusal zaman karmaşıklığının bir sırasıdır. Dizinin uzunluğu arttıkça, daha fazla bellek tüketirler. Neden? Boyutları ikili ilişkilerle öğrenmezler. Sırayla öğrenirler. Örneğin: 
Boyut a: Jay 
Boyut b: likes ve Jay 
Boyut d: oranges ve likes ve Jay 
Boyut e: in ve oranges ve likes ve Jay … 
Boyut z. 
Görülebileceği gibi, her kelime sadece başka bir kelimeye bakmaz, aynı anda birkaç kelimeye birden bakar! 
Bir kelimenin boyut sayısı d, önceki kelimenin boyutları ile çarpılır ve boyutları öğrenmek için d^2'ye yol açar. 
Bir tekrarlayan katmanın hesaplama zamanı karmaşıklığı böylece şu şekildedir: 
Şimdi sihri görelim.

Python kodu bulunmamaktadır, sadece ingilizce paragrafın türkçeye birebir çevirisi yapılmıştır. 

Eğer ingilizce paragraf içinde python kodları olsaydı, satır satır açıklamalar yapılırdı. 

Örneğin, eğer 
```python
# hesaplama zamanı karmaşıklığı örnegi
def time_complexity(n):
    return n**2
```
gibi bir python kodu olsaydı, 

- `def time_complexity(n):` satırı: `time_complexity` adında, `n` parametresini alan bir fonksiyon tanımlar.
- `return n**2` satırı: Fonksiyonun geri dönüş değerini `n` nin karesi olarak belirler. 

gibi açıklamalar yapılırdı.

---

