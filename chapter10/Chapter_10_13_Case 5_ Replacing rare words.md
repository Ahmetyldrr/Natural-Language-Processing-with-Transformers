# Nadir Kelimelerin Yerine Koyma

Nadir kelimelerin yerine koyma başlı başına bir projedir. Bu çalışma belirli görevler ve projeler için ayrılmıştır. Örneğin, bir şirketin bütçesi havacılık alanında bir bilgi tabanına sahip olma maliyetini karşılayabilir. Bu durumda, tokenize edilmiş dizini sorgulayarak kaçırdığı kelimeleri bulmak için zaman harcamaya değer. Sorunlar çözülen konuya göre gruplandırılabilir ve bilgi tabanı düzenli olarak güncellenecektir.

## Örnek: Eleutheromania Kelimesi

Case 4'te eleutheromania kelimesine rastladık. 
```python
word1 = "freedom"
word2 = "liberty"
print("Similarity", similarity(word1, word2), word1, word2)
```
Yukarıdaki python kodu `word1` ve `word2` değişkenlerine sırasıyla "freedom" ve "liberty" değerlerini atar ve daha sonra bu iki kelimenin benzerliğini hesaplayarak sonucu ekrana yazdırır.

Bu kodun çıktısı ilginç bir sonuç üretir:
```
Similarity [[0.99956566]] freedom liberty
```
Eleutheromania kelimesini aynı meta-konsepti aktaran "freedom" ile değiştirebilirdik. Her durumda, bazı nadir kelimelerin daha yaygın kelimelerle değiştirilmesi gerekir. Örneğin, 0.9'un üzerinde korelasyonlar bulana kadar çalıştırdığımız değiştirme kelimeleriyle sorgular oluşturabiliriz. Ayrıca, kritik bir hukuk projesi yönetiyorsak, nadir kelimeler içeren temel belgelerin standart İngilizceye çevrilmesini sağlayabiliriz. Böylece, NLP görevlerinde dönüştürücünün performansı artacak ve şirketin bilgi tabanı giderek artacaktır.

## Tokenizerların NLP Görevleriyle Eşleşmesi

Şimdi, önceden eğitilmiş tokenizörlerin NLP görevleriyle ne kadar iyi eşleştiğini görelim.

---

