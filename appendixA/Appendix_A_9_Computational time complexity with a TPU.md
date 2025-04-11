# Google Cloud TPU ile Matris Hesaplamaları ve Sinir Ağları
Google, Cloud TPU'ları özellikle matris hesaplamaları ve sinir ağları için tasarladı. Bir TPU'nun birincil görevi matris çarpımı olduğundan, sıralı işlemleri çalıştırmak pek anlamlı değildir. Tekrarlayan katmanı, dikkat katmanının çalışma süresinin on katıyla sınırlayacağız.

# TPU Kullanımını Doğrulama
İlk hücreyi çalıştırmadan önce, Çalışma Zamanı menüsüne giderek, Çalışma Zamanı türünü değiştir'i seçerek ve Donanım hızlandırıcısının TPU olarak ayarlandığından ve Çalışma Zamanı şeklinin (RAM) Yüksek-RAM olarak ayarlandığından emin olarak bir TPU kullandığımızı doğrulamalıyız: 
Şekil A.6: TPU kullanmak için not defteri ayarlarını değiştirme

# TPU ile TensorFlow Kullanımı
Bu simülasyon için, TPU'nun tam avantajını kullanmak üzere TensorFlow'u kullanacağız:
```python
import tensorflow as tf
import numpy as np
import time
```
Program, CPU ve GPU değerlendirmeleri için kullanılan programla aynıdır, ancak bu sefer TPU üzerinde TensorFlow ile çalışmaktadır:
```python
# dizinin uzunluğunu ve temsil boyutunu tanımla
n = 512
d = 512

# girdileri tanımla
input_seq = tf.random.normal((n, d), dtype=tf.float32)
```
Matris çarpımını çalıştırıyoruz ve ne kadar zaman aldığını ölçüyoruz:
```python
# self-attention katman simülasyonu O(n^2*d)
start_time = time.time()
_ = tf.matmul(input_seq, input_seq, transpose_b=True)
at = time.time() - start_time
print(f"Self-attention hesaplama zamanı: {at} saniye")
```
Çıktı verimliliği:
```
Self-attention hesaplama zamanı: 0.10626077651977539 saniye
```
Şimdi tekrarlayan katmanı çalıştıracağız:
```python
# tekrarlayan katman simülasyonu O(n*d^2)
start_time = time.time()
hidden_state = np.zeros((n, d), dtype=np.float32)
for i in range(n):
    for j in range(d):
        for k in range(d):
            hidden_state[i, j] += input_seq[i, j].numpy() * hidden_state[min(i, k), j]
            ct = time.time() - start_time
            if ct > at * 10:
                break
```
Çıktı verimsizliği, ki bu normaldir:
```python
rt = time.time() - start_time
print(f"Tekrarlayan katman hesaplama zamanı: {rt} saniye")
```
Çıktı:
```
Tekrarlayan katman hesaplama zamanı: 66.53181290626526 saniye
```
Şimdi toplam zamanın yüzdesini hesaplayacağız:
```python
# Toplamı hesapla
total = at + rt

# at'nin yüzdesini hesapla
percentage_at = round((at / total) * 100, 2)

# Sonucu yazdır
print(f"Self-attention ve tekrarlayan hesaplama toplamında self-attention hesaplamasının yüzdesi {percentage_at}%")
```
Çıktı, dikkat katmanlarının daha verimli olduğunu doğrular:
```
Self-attention ve tekrarlayan hesaplama toplamında self-attention hesaplamasının yüzdesi 0.16%
```
Şimdi TPU simülasyonunu LLM'ler dünyasına taşıyacağız.

Kod açıklamaları:

1. `import tensorflow as tf`: TensorFlow kütüphanesini içe aktarır.
2. `import numpy as np`: NumPy kütüphanesini içe aktarır.
3. `import time`: Zaman kütüphanesini içe aktarır.
4. `n = 512` ve `d = 512`: Dizinin uzunluğunu ve temsil boyutunu tanımlar.
5. `input_seq = tf.random.normal((n, d), dtype=tf.float32)`: Girdileri tanımlar.
6. `tf.matmul(input_seq, input_seq, transpose_b=True)`: Matris çarpımını gerçekleştirir.
7. `time.time() - start_time`: İşlemin ne kadar zaman aldığını ölçer.
8. `hidden_state = np.zeros((n, d), dtype=np.float32)`: Tekrarlayan katman için gizli durum değişkenini tanımlar.
9. İç içe geçmiş döngüler: Tekrarlayan katman simülasyonunu gerçekleştirir.
10. `ct > at * 10`: Tekrarlayan katman simülasyonunu, dikkat katmanının çalışma süresinin on katıyla sınırlar.
11. `total = at + rt`: Toplam zamanı hesaplar.
12. `percentage_at = round((at / total) * 100, 2)`: Self-attention hesaplamasının yüzdesini hesaplar.

---

