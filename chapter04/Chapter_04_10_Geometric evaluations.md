# BLEU Yöntemi
BLEU yöntemi, bir aday cümleyi bir referans cümle veya birkaç referans cümle ile karşılaştırır. Python'da metin işleme kütüphaneleri ile nltk kütüphanesini kullanacağız. Program nltk kütüphanesini içe aktarır: 
```python
from nltk.translate.bleu_score import sentence_bleu
from nltk.translate.bleu_score import SmoothingFunction
```
# NLTK Kütüphanesinin Kullanımı
Daha sonra, makine çeviri modelinin ürettiği aday çeviriyi ve veri kümesindeki gerçek çeviri referanslarını karşılaştırır. Bir cümlenin birkaç kez tekrarlanmış olabileceğini ve farklı çevirmenler tarafından farklı şekillerde çevrilmiş olabileceğini unutmayın, bu da etkili değerlendirme stratejileri bulmayı zorlaştırır. Program bir veya daha fazla referansı değerlendirebilir:

## Örnek 1
```python
reference = [['the', 'cat', 'likes', 'milk'], ['cat', 'likes', 'milk']]
candidate = ['the', 'cat', 'likes', 'milk']
score = sentence_bleu(reference, candidate)
print('Example 1', score)
```
## Örnek 2
```python
reference = [['the', 'cat', 'likes', 'milk']]
candidate = ['the', 'cat', 'likes', 'milk']
score = sentence_bleu(reference, candidate)
print('Example 2', score)
```
Her iki örneğin puanı 1'dir:
```
Example 1 1.0
Example 2 1.0
```
# Değerlendirme
Aday C'nin, referans R'nin ve C'de bulunan doğru token sayısının (N) basit bir değerlendirmesi P, geometrik bir fonksiyon olarak temsil edilebilir: Bu geometrik yaklaşım, örneğin 3-gram örtüşme arıyorsanız katıdır:

## Örnek 3
```python
reference = [['the', 'cat', 'likes', 'milk']]
candidate = ['the', 'cat', 'enjoys', 'milk']
score = sentence_bleu(reference, candidate)
print('Example 3', score)
```
Çıktı, 3-gram örtüşme arıyorsanız şiddetlidir:
```
Warning (from warnings module):
  File
Example 3 1.0547686614863434e-154
/usr/local/lib/python3.10/dist-packages/nltk/translate/bleu_score.py:552: UserWarning: 
The hypothesis contains 0 counts of 3-gram overlaps.
Therefore the BLEU score evaluates to 0, independently of
how many N-gram overlaps of lower order it contains.
Consider using lower n-gram order or use SmoothingFunction()
```
# BLEU Skorunun Sınırlamaları
Hiperparametreler değiştirilebilir, ancak yaklaşım bazen kabul edilebilir değerlendirmeler elde ettiğimizde bile katıdır. Önceki koddaki uyarı, bir sonraki bölümde tartışacağımız şeyleri öngören iyi bir uyarıdır. Mesajlar, programın her sürümü ve her çalıştırılması ile değişebilir, çünkü bu bir stokastik süreçtir.

# Değiştirilmiş Unigram Yaklaşımı
Papineni ve diğerleri (2002), değiştirilmiş bir unigram yaklaşımı geliştirdiler. Fikir, referans cümlesindeki kelime oluşumlarını saymak ve kelimenin aday cümlede aşırı değerlendirilmemesini sağlamaktı. Papineni ve diğerleri (2002) tarafından açıklanan şu örneği düşünün:
Referans 1: The cat is on the mat.
Referans 2: There is a cat on the mat.
Şimdi, aşağıdaki aday sırasını düşünün:
Aday: the the the the the the the
Şimdi, aday cümlesindeki (aynı kelimenin 7 oluşumu "the") Referans 1 cümlesinde bulunan kelime sayısına bakıyoruz (kelimenin 2 oluşumu "the"). Standart unigram hassasiyeti 7/7 olacaktır. Değiştirilmiş unigram hassasiyeti 2/7'dir. BLEU fonksiyon çıktısının uyarı ile aynı fikirde olduğunu ve düzeltme kullanmayı önerdiğini unutmayın.

# Düzeltme Teknikleri
Düzeltme tekniklerini BLEU araç setine ekleyelim.

---

