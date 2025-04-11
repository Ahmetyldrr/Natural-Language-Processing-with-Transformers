# İşlenmiş Tokenlerin İncelenmesi
Bu bölümde, bu bölümün 2. kısmında işlenmiş tokenleri inceleyebiliriz. Seçtiğimiz bir kelimenin kelime haznesinde olup olmadığını görebiliriz. Örneğin, "consciousness" kelimesi kelime haznesinde değil: 
```python
try:
    vector = model.wv['consciousness']
    print('Vector for "consciousness":', vector)
except KeyError:
    print('"consciousness" is not in the dictionary')
```
Çıktı, kelimenin sözlükte olmadığını doğrular: "consciousness" is not in the dictionary

"Consciousness" kelimesi, lemmatization'dan sonra sözlükte olmamalıdır. Ancak, "consciousness" kelimesinin lemma (temel kelime) hali olan "conscious" bu metinde bulunmalıdır, çünkü felsefi ve bilimsel düşünceler içermektedir. Hadi bakalım:
```python
try:
    vector = model.wv['conscious']
    print('Vector for "conscious":', vector)
except KeyError:
    print('"conscious" is not in the dictionary')
```
Kelime vektörünün çıktısının bir kısmı, "conscious" kelimesinin kelime haznesinde olduğunu gösterir: 
Vector for "conscious": [-2.2882714e-03 -2.9769554e-03 -2.3382956e-03  3.2302644e-03
  4.9209874e-04 -7.2649046e-04  8.2537113e-04 -3.6820408e-04
 -1.1185763e-03 -1.8049215e-03  2.1578181e-03 -1.0867673e-03
  7.9940347e-04  2.3183119e-03 -1.7192229e-04  2.8174506e-03
 -1.5929197e-03  3.3099041e-03 -1.9293354e-03 -3.0342239e-04
  1.4344892e-04  3.6501623e-04  1.3159955e-03  2.5331231e-03
 -9.0605288e-04  1.5739332e-03 -1.6196299e-03  9.4100273e-05
 -7.1035558e-04 -9.2428079e-04 -6.3189666e-04  3.4200953e-04…

# "Conscious" Kelimesine Benzer Kelimelerin Bulunması
Şimdi programa "conscious" kelimesine en benzer kelimeleri bulmasını soracağız:
```python
try:
    similar_words = model.wv.most_similar('conscious')
    print('Most similar words to "conscious":', similar_words)
except KeyError:
    print('"conscious" is not in the dictionary')
```
Çıktı, işlediğimiz metne göre kelime haznesindeki benzer kelimeleri gösterir: 
Most similar words to "conscious": 
[('wouldconduce', 0.21150538325309753), 
('itscounterweights', 0.19385728240013123), 
('versed', 0.185345858335495), 
('comprehend', 0.1835186779499054), 
('requisite', 0.17346185445785522), 
('convertsthe', 0.1722400188446045), 
('ibelieved', 0.1657719910144806), 
('transmit', 0.16429133713245392), 
('speakingmyself', 0.16091690957546234), 
('warmth', 0.15618115663528442)]

Çıktı, "conscious" kelimesine benzer kelimeleri ve 0 ile 1 arasında benzerlik puanlarını içerir. Daha yüksek puan, daha yüksek benzerlik anlamına gelir. Çıktılar, NLP algoritmalarının rastgele doğası nedeniyle bir çalışmadan diğerine değişebilir. Tokenization işlevi için daha fazla belge eklemek, embedding sürecini optimize edebilir. Ancak, bu bölümdeki örnek için yeterli bilgiye sahibiz. Şimdi Gensim'in vektör uzayını inceleyelim.

**Python Kodlarının Açıklaması**

1. `try-except` blokları: Bu bloklar, kodun hata vermesini önlemek için kullanılır. `try` bloğu içindeki kod çalıştırılır ve eğer bir hata oluşursa, `except` bloğu içindeki kod çalıştırılır.

2. `model.wv['consciousness']`: Bu satır, `model` nesnesinin `wv` özelliğini kullanarak "consciousness" kelimesinin vektör temsilini alır.

3. `model.wv.most_similar('conscious')`: Bu satır, `model` nesnesinin `wv` özelliğini kullanarak "conscious" kelimesine en benzer kelimeleri bulur.

4. `print` fonksiyonu: Bu fonksiyon, çıktıları yazdırmak için kullanılır.

5. `similar_words = model.wv.most_similar('conscious')`: Bu satır, "conscious" kelimesine en benzer kelimeleri `similar_words` değişkenine atar.

---

