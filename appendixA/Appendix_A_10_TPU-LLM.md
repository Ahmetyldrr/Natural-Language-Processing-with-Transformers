# Dikkat Katmanı Simülasyonu

TPU için nispeten standart parametrelerle aynı simülasyonu çalıştıracağız. d=12288, bir LLM modelinin boyutluluğu olabilir. n=32728, bir LLM modelinin girdi limiti olabilir. Bu değerler, tekrarlayan katmanı TPU üzerinde çalıştırmayı göstermek için sadece bir örnektir. Değerler bir LLM'ninkilerdir:
```python
import tensorflow as tf
import numpy as np
import time

# dizinin uzunluğunu ve temsil boyutluluğunu tanımla
n = 32768
d = 12288

# girdileri tanımla
input_seq = tf.random.normal((n, d), dtype=tf.float32)
```
Aynı fonksiyonu daha önce olduğu gibi çalıştıracağız ve ne kadar zaman aldığını göstereceğiz:
```python
# self-attention katmanı simülasyonu O(n^2*d)
start_time = time.time()
_ = tf.matmul(input_seq, input_seq, transpose_b=True)
at = time.time() - start_time
print(f"Self-attention hesaplama zamanı: {at} saniye")
```
Zaman çok verimlidir:
```
Self-attention hesaplama zamanı: 23.117244005203247 saniye
```
TPU hakkında bazı bilgileri gösterebiliriz:
```python
import os
from tensorflow.python.profiler import profiler_client

tpu_profile_service_address = os.environ['COLAB_TPU_ADDR'].replace('8470', '8466')
print(profiler_client.monitor(tpu_profile_service_address, 100, 2))
```
TPU Matrix Units'ün neredeyse hiç kullanılmadığını görebiliriz:
```
Timestamp: 10:20:30
  TPU type: TPU v2
  Utilization of TPU Matrix Units (higher is better): 0.000%
```
Bu değerlendirmenin sonucu aşağıdaki noktalarda özetlenebilir:

* Dikkat katmanı hesaplama zamanı karmaşıklığı, tekrarlayan katmanı hesaplama zamanı karmaşıklığını aşar.
* Dikkat katmanının birebir kelime analizi, uzun vadeli bağımlılıkları tespit etmede daha iyidir.
* Dikkat katmanının mimarisi, modern GPU'ları ve TPU'ları tam olarak kullanan matris çarpımı sağlar.
* GPU'ların (ve TPU'ların) ve dikkatin gücünü serbest bırakarak, algoritmalar daha fazla veri işleyebilir ve daha fazla bilgi öğrenebilir.

Şimdi, token-to-token dikkat katmanının yapısının bir token devrimine nasıl dönüştüğünü göreceğiz.

---

