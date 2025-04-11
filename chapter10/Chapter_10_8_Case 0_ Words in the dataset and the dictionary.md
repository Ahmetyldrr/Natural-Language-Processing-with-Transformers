# Veri Kümesinde Kelime Benzerliği Hesapları

Veri kümesinde "freedom" ve "liberty" kelimeleri bulunmaktadır ve bunların kosinüs benzerliği hesaplanabilir: 
```python
word1 = "freedom"
word2 = "liberty"
print("Similarity", similarity(word1, word2), word1, word2)
```
İçerik yoğun olmasına rağmen benzerlik 0.99 ile sınırlıdır: "freedom" ve "liberty" arasındaki benzerlik [[0.99947506]]'dir.

# Benzerlik Algoritmasının Doğası

Benzerlik algoritması yinelemeli deterministik bir hesaplama değildir. Bu bir stokastik algoritmadır. Bu bölümün sonuçları, veri kümesinin içeriğine, veri kümesinin boyutuna ve modülün sürümlerine bağlı olarak değişebilir. Örneğin, hücreyi 10 kez çalıştırdığınızda, aşağıdaki 10 çalıştırma örneğinde olduğu gibi farklı değerler elde edebilirsiniz veya etmeyebilirsiniz.

## Farklı Çalıştırmalarda Sonuçlar

Aşağıdaki durumda, Google Colab VM ve CPU ile 10 kez aynı sonucu elde ettim:
- Çalıştırma 1: Benzerlik [[0.62018466]] "freedom" "liberty"
- Çalıştırma 2: Benzerlik [[0.62018466]] "freedom" "liberty"
- ...
- Çalıştırma 10: Benzerlik [[0.62018466]] "freedom" "liberty"

Ancak, Google Colab'da çalışma zamanını "fabrika ayarlarına sıfırlama" yaptım. Yeni bir VM ve CPU ile aşağıdaki sonuçları elde ettim:
- Çalıştırma 1: Benzerlik [[0.51549244]] "freedom" "liberty"
- Çalıştırma 2: Benzerlik [[0.51549244]] "freedom" "liberty"
- ...
- Çalıştırma 10: Benzerlik [[0.51549244]] "freedom" "liberty"

Daha sonra, Google Colab'da çalışma zamanını tekrar "fabrika ayarlarına sıfırlama" yaptım ve GPU'yu etkinleştirdim. Yeni bir VM ve GPU ile aşağıdaki sonuçları elde ettim:
- Çalıştırma 1: Benzerlik [[0.58365834]] "freedom" "liberty"
- Çalıştırma 2: Benzerlik [[0.58365834]] "freedom" "liberty"
- ...
- Çalıştırma 10: Benzerlik [[0.58365834]] "freedom" "liberty"

# Stokastik Algoritmaların Doğası

Buradaki sonuç, stokastik algoritmaların olasılıklara dayandığıdır. Bu nedenle, bir tahmini gerektiği kadar n kez çalıştırmak iyi bir uygulamadır. Şimdi, bir kelimenin eksik olduğu durumları inceleyelim.

---

