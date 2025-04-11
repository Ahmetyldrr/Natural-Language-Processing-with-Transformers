# Nadir Kelimelerin Dönüştürücüler Üzerindeki Etkisi

Nadir kelimeler, basit uygulamaların ötesine geçen belirli görevler için dönüştürücülerin çıktısı üzerinde yıkıcı etkiler yaratır. Nadir kelimeleri yönetmek, doğal dilin birçok alanına uzanır. Örneğin: Nadir kelimeler veri kümelerinde ortaya çıkabilir ancak fark edilmez veya modeller onlarla başa çıkmak için yeterince eğitilmemiştir. Nadir kelimeler tıbbi, hukuki, mühendislik terimleri veya diğer herhangi bir profesyonel jargon olabilir. Nadir kelimeler argo olabilir. İngilizce dilinin yüzlerce varyasyonu vardır. Örneğin, Amerika Birleşik Devletleri, Birleşik Krallık, Singapur, Hindistan, Avustralya ve diğer birçok ülkede farklı İngilizce kelimeler kullanılır. Nadir kelimeler yüzyıllar önce yazılmış ve unutulmuş veya yalnızca uzmanlar tarafından kullanılan metinlerden gelebilir. Örneğin, bu durumda, eleutheromania (yoğun özgürlük özlemi) kelimesini kullanıyoruz: 
```python
word1 = "eleutheromania"
word2 = "liberty"
print("Similarity", similarity(word1, word2), word1, word2)
```
Sistem eleutheromania'yı tanımıyor: 
```
# Çıktı:
The word eleutheromania does not exist in the dictionary
Similarity 0 eleutheromania liberty
```
Ne yazık ki, eğer nadir bir kelime kullanılırsa, program karıştırılacak ve her çalıştırma sonrasında beklenmedik sonuçlar elde edeceğiz. Eğer bu bir proje sırasında gerçekleşirse, tanınmayan nadir kelimeler içeren ek metinlerin tokenizer eğitim sürecine dahil edilmesi gerekecektir. Örneğin, bir avukatlık firmasında belgeleri özetlemek veya diğer görevleri gerçekleştirmek için bir dönüştürücü model uyguladığımızda dikkatli olmalıyız! Şimdi, nadir kelime problemini çözmek için kullanabileceğimiz bazı yöntemlere bakalım.

## Kod Açıklaması

1. `word1 = "eleutheromania"`: `word1` değişkenine `"eleutheromania"` string değeri atanır.
2. `word2 = "liberty"`: `word2` değişkenine `"liberty"` string değeri atanır.
3. `print("Similarity", similarity(word1, word2), word1, word2)`: 
   - `similarity(word1, word2)`: `word1` ve `word2` arasındaki benzerliği hesaplar. 
   - `print()`: Hesaplanan benzerlik değerini, `"Similarity"` stringi ile birlikte ve `word1` ve `word2` değerlerini yazdırır.

Bu kod, iki kelime arasındaki benzerliği hesaplamak için `similarity()` fonksiyonunu kullanmaktadır. Ancak, `similarity()` fonksiyonunun tanımı verilmediği için, bu fonksiyonun nasıl çalıştığı bilinmemektedir. 
`eleutheromania` kelimesi sözlükte bulunmadığı için, sistem tarafından tanınmamaktadır ve benzerlik değeri `0` olarak hesaplanır.

---

