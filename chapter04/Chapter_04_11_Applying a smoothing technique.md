# Chen ve Cherry (2014) tarafından tanıtılan bir yumuşatma tekniği
Chen ve Cherry (2014) tarafından tanıtılan bir yumuşatma tekniği, standart BLEU tekniklerinin geometrik değerlendirme yaklaşımını geliştirir. 

## Etiket Yumuşatma (Label Smoothing)
Etiket yumuşatma, eğitim aşamasında bir Transformer modelinin performansını artıran çok etkili bir yöntemdir. 
Perplexity üzerinde olumsuz bir etkisi vardır. Ancak, modeli daha belirsiz olmaya zorlar. 
Buna karşılık, doğruluk üzerinde olumlu bir etkisi vardır.

### Örnek
Örneğin, aşağıdaki dizide maskelenmiş kelimenin ne olduğunu tahmin etmemiz gerektiğini varsayalım: 
The cat [mask] milk.

Çıktının bir softmax vektörü olarak çıktığını hayal edin:
```python
candidate_words = ['drinks', 'likes', 'enjoys', 'appreciates']
candidate_softmax = [0.7, 0.1, 0.1, 0.1]
candidate_one_hot = [1, 0, 0, 0]
```
Bu, kaba bir yaklaşım olacaktır. 
Etiket yumuşatma, epsilon = ε değerini tanıtarak sistemi daha açık fikirli hale getirebilir. 
`candidate_softmax`'ın eleman sayısı k=4'tür. 
Etiket yumuşatma için, örneğin 0.25'e ayarlayabiliriz.

Etiket yumuşatmanın birkaç yaklaşımından biri basit bir fonksiyon olabilir. 
İlk olarak, `candidate_one_hot` değerini ε kadar azaltın. 
0 değerlerini ε kadar artırın. 
Bu yaklaşımı uygularsak aşağıdaki sonucu elde ederiz:
```python
candidate_smoothed = [0.75, 0.083, 0.083, 0.083]
```
Bu, çıktıyı gelecekteki dönüşümlere ve değişikliklere açık hale getirir.

## Transformers ve Chencherry Yumuşatma
Transformers, etiket yumuşatmanın varyantlarını kullanır. 
BLEU'nun bir varyantı chencherry yumuşatmadır.

### Chencherry Yumuşatma
Chen ve Cherry (2014), aksi halde 0 olan değerlere ekleyerek aday değerlendirmelerini yumuşatmanın ilginç bir yolunu tanıttı. 
Bu bölümde, önce yumuşatma olmadan değerlendireceğiz, sonra bir chencherry (Boxing Chen + Colin Cherry) yumuşatma fonksiyonu uygulayacağız.

#### Örnek 4
```python
reference = [['je', 'vous', 'invite', 'a', 'vous', 'lever', 'pour', 'cette', 'minute', 'de', 'silence']]
candidate = ['levez', 'vous', 'svp', 'pour', 'cette', 'minute', 'de', 'silence']
score = sentence_bleu(reference, candidate)
print("without smoothing score", score)
```
İnsan kabul etse de, çıktı skoru zayıf:
without smoothing score 0.37188004246466494

Şimdi, değerlendirmeye biraz açık fikirli yumuşatma ekleyelim:
```python
chencherry = SmoothingFunction()
r1 = list('je vous invite a vous lever pour cette minute de silence')
candidate = list('levez vous svp pour cette minute de silence')
print("with smoothing score", sentence_bleu([r1], candidate, smoothing_function=chencherry.method1))
```
Skor, sadece yumuşatmanın nasıl kullanılacağına dair bir örnektir ve fonksiyonlar geliştikçe sürekli olarak gelişecektir:
with smoothing score 0.6194291765462159

Artık bir veri kümesinin nasıl ön işleme tabi tutulduğunu ve BLEU'nun makine çevirilerini nasıl değerlendirdiğini gördük.

---

