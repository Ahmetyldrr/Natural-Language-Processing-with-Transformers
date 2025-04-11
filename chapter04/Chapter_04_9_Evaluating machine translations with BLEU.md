# Papineni ve Takımı Tarafından Geliştirilen Değerlendirme Yöntemi

Papineni ve takımı (2002) bir insan çevirisini değerlendirmek için verimli bir yol geliştirdiler. İnsan taban çizgisi tanımlamak zordu. Ancak, insan çevirisini makine çevirisiyle kelime kelime karşılaştırırsak verimli sonuçlar elde edebileceğimizi fark ettiler. Papineni ve takımı (2002) yöntemlerini Çift Dilli Değerlendirme Çalışması (BLEU) puanı olarak adlandırdılar.

# BLEU Skorunun Uygulanması

Bu bölümde, BLEU skorunu uygulamak için Doğal Dil Araç Seti'ni (NLTK) kullanacağız: http://www.nltk.org/api/nltk.translate.html#nltk.translate.bleu_score.sentence_bleu 
Geometrik değerlendirmelerle başlayacağız.

Python kodu bulunmamaktadır, sadece bir ingilizce paragrafın türkçeye birebir çevirisi yapılmıştır.

Eğer NLTK kütüphanesini kullanarak BLEU skorunu hesaplamak için bir python kodu örneği verseniz, kodu satır satır açıklayabilirim.

Örnek python kodu:
```python
from nltk.translate.bleu_score import sentence_bleu
from nltk.tokenize import word_tokenize

# Referans çeviri
reference = "Bu bir örnek cümledir."
# Makine çevirisi
hypothesis = "Bu bir örnek cümle."

# Kelimelere ayırma
reference_tokens = word_tokenize(reference)
hypothesis_tokens = word_tokenize(hypothesis)

# BLEU skorunu hesaplama
bleu_score = sentence_bleu([reference_tokens], hypothesis_tokens)

print("BLEU Skoru:", bleu_score)
```
Satır satır açıklaması:

1. `from nltk.translate.bleu_score import sentence_bleu`: NLTK kütüphanesinden `sentence_bleu` fonksiyonunu içe aktarır. Bu fonksiyon, bir cümlenin BLEU skorunu hesaplamak için kullanılır.
2. `from nltk.tokenize import word_tokenize`: NLTK kütüphanesinden `word_tokenize` fonksiyonunu içe aktarır. Bu fonksiyon, bir metni kelimelere ayırmak için kullanılır.
3. `reference = "Bu bir örnek cümledir."`: Referans çeviriyi tanımlar.
4. `hypothesis = "Bu bir örnek cümle."`: Makine çevirisini tanımlar.
5. `reference_tokens = word_tokenize(reference)`: Referans çeviriyi kelimelere ayırır.
6. `hypothesis_tokens = word_tokenize(hypothesis)`: Makine çevirisini kelimelere ayırır.
7. `bleu_score = sentence_bleu([reference_tokens], hypothesis_tokens)`: BLEU skorunu hesaplar. `sentence_bleu` fonksiyonu, bir liste içinde referans çevirilerin kelimelerine ayrılmış hallerini ve makine çevirisinin kelimelerine ayrılmış halini alır.
8. `print("BLEU Skoru:", bleu_score)`: Hesaplanan BLEU skorunu yazdırır.

---

