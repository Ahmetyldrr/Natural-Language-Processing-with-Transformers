# Orijinal Transformer Modelinin Oluşturulması

2. Bölümde, Transformer Modelinin Mimarisine Giriş bölümünde açıklandığı gibi Orijinal Transformer modelini oluşturacağız. Trax fonksiyonumuz, birkaç satır kodla önceden eğitilmiş bir model konfigürasyonunu alacak:

```python
# gs://trax-ml/models/translation/ende_wmt32k.gin önceden eğitilmiş model konfigürasyonu
model = trax.models.Transformer(
    input_vocab_size=33300,
    d_model=512, d_ff=2048,
    n_heads=8, n_encoder_layers=6, n_decoder_layers=6,
    max_len=2048, mode='predict')
```

Model, bir kodlayıcı ve kod çözücü yığınına sahip Orijinal Transformer'dir. Her yığın 6 katman ve 8 kafadan oluşur. `d_model=512`, Orijinal Transformer mimarisinde olduğu gibi.

Modelin mimarisini aşağıdaki kodla inceleyebiliriz:
```python
from pprint import pprint
pprint(vars(model))
```

Çıktı, modelin mimarisinin ilginç bir görünümünü sağlar:
```
Serial_in2_out2[
    Embedding_33300_512
    Dropout
    PositionalEncoding
    Serial_in2_out2[
      Branch_in2_out3[
        None
        Serial_in2_out2[
          LayerNorm
          Serial_in2_out2[
            _in2_out2
            Serial_in2_out2[
              Select[0,0,0]_out3
              Serial_in4_out2[
                _in4_out4
                Serial_in4_out2[
                  Parallel_in3_out3[
                    Dense_512
                    Dense_512
                    Dense_512
   ...
```

Modeli incelemek için biraz zaman ayıralım. Birçok esnek mimariye açılan kritik bir kavramdan bahsedelim. **Combinator**, diğer katmanları içeren bir katman türüdür. Soyut bir sınıftır. Bu sınıfın alt sınıflarını kullanarak farklı işlevler için katmanları birleştiririz, örneğin `Serial`, `Parallel`, `Branch`, `Residual` ve `Select`. Bu alt sınıflar, sinir ağının yapı taşları olarak kullanılan kombinatorlardır:

*   `Serial`, katmanları sırayla birbiri ardına uygular.
*   `Parallel`, aynı girdiye birkaç katmanı paralel olarak uygular ve çıktılarının bir demetini oluşturur.
*   `Branch`, bir girdiye paralel olarak birkaç katmanı uygular, ardından çıktıları birleştirir.
*   `Residual`, katman dizilerinin (veya tek bir katmanın) çıktısını girdiye ekler.
*   `Select`, bir girdi demetinden öğeleri seçer.

`in2_out2` terimi, iki girdi olduğu ve iki çıktının üretildiği anlamına gelir. Daha fazla bilgi için lütfen Google Trax belgelerine bakın: https://trax-ml.readthedocs.io/en/latest/notebooks/layers_intro.html

Transformer'ın çalışması için önceden eğitilmiş ağırlıklara ihtiyacı vardır.

---

