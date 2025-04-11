# T5 Modelinin Mimarisini ve Yapılandırmasını İnceleme

Bu bölümde, T5-large modelinin mimarisini ve yapılandırmasını inceleyeceğiz. `display_architecture==True` ise, modelin yapılandırmasını görebiliriz:

```python
if display_architecture == True:
    print(model.config)
```

Örneğin, modelin temel parametrelerini görebiliriz:
```
"num_heads": 16,
"num_layers": 24,
...
```
Model, 16 başlıklı ve 24 katmanlı bir T5 transformer'dır. T5'in metinden-metinye uygulamasını da görebiliriz, bu da bir girdi cümlesine görevi gerçekleştirmek için bir önek ekler. Önek, modelin parametrelerini değiştirmeden geniş bir görev yelpazesini metinden-metinye formatında temsil etmeyi mümkün kılar. Bizim durumumuzda, önek "summarization"dır:

```
"task_specific_params": {
    "summarization": {
      "early_stopping": true,
      "length_penalty": 2.0,
      "max_length": 200,
      "min_length": 30,
      "no_repeat_ngram_size": 3,
      "num_beams": 4,
      "prefix": "summarize: "
    },
```

T5'in karakteristik bir özelliği olan "task_specific_params"i görebiliriz:
- `"early_stopping": true`: Model, son-cümle tokenini öngördüğünde metin üretimi duracaktır, bu da makine kullanımını optimize edebilir.
- `"length_penalty": 2.0`: Bu parametre, ışın aramasının skorunu etkiler. Değer 1'i aşarsa, model daha uzun diziler üretmeye teşvik edilir. Aksi takdirde, model daha kısa diziler üretecektir.
- `"max_length": 200` ve `"min_length": 30`: Üretilen token sayısını kontrol eder. Model en az `min_length` kadar token üretecek ve `max_length`e ulaştığında duracaktır.
- `"no_repeat_ngram_size": 3`: Tokenların n-gramlarının tekrarını kontrol eder. Parametre 3'e ayarlanmıştır, 3-gramların tekrarını sınırlar.
- `"num_beams": 4`: Işın arama algoritmasını uygular, bu da en önemli dört metin tamamlama öngörüsünü genişletecektir. Değer 1'e ayarlanırsa, algoritma açgözlü olur, yani sadece bir öngörü arayacaktır. Değer birden fazla olursa, ışının genişliği genişleyecek ve model daha fazla olasılık arayacaktır.
- `"prefix": "summarize:"`: Görevi tanımlar; bu durumda, özetleme.

Diğer ilginç bir parametre de kelime hazinesi boyutudur:
```
"vocab_size": 32128
```
Kelime hazinesi boyutu kendi başına bir konudur. Çok fazla kelime hazinesi seyrek temsillere yol açacaktır. Öte yandan, çok az kelime hazinesi NLP görevlerini bozacaktır. Kelime hazinesi boyutunun seçimi, bir modelin eğitimi ve uygulanması üzerinde kritik bir etkiye sahip olacaktır. Gerekirse, Bölüm 10'a geri dönmek için zaman ayırın, Transformer Modellerinin Şekillenmesinde Tokenizerların Rolünü Araştırma.

Modelin detaylarını basitçe model yazdırarak da görebiliriz:
```python
if display_architecture == True:
    print(model)
```

Örneğin, kodlayıcı yığınının (0'dan 23'e numaralandırılmış) bir bloğunun (katmanının) içine bakabiliriz:
```
(12): T5Block(
    (layer): ModuleList(
      (0): T5LayerSelfAttention(
        (SelfAttention): T5Attention(
          (q): Linear(in_features=1024, out_features=1024, bias=False)
          (k): Linear(in_features=1024, out_features=1024, bias=False)
          (v): Linear(in_features=1024, out_features=1024, bias=False)
          (o): Linear(in_features=1024, out_features=1024, bias=False)
        )
        (layer_norm): T5LayerNorm()
        (dropout): Dropout(p=0.1, inplace=False)
      )
      (1): T5LayerFF(
        (DenseReluDense): T5DenseReluDense(
          (wi): Linear(in_features=1024, out_features=4096, bias=False)
          (wo): Linear(in_features=4096, out_features=1024, bias=False)
          (dropout): Dropout(p=0.1, inplace=False)
        )
        (layer_norm): T5LayerNorm()
        (dropout): Dropout(p=0.1, inplace=False)
      )
    )
)
```
Modelin, dikkat alt katmanları için 1024 özellik üzerinde işlem yaptığını ve çıktı olarak 1024 özellik üreten beslemeli ağ alt katmanının iç hesaplamaları için 4096 özellik üzerinde işlem yaptığını görebiliriz. Transformerların simetrik yapısı tüm katmanlarda korunur.

Kodlayıcı yığınlarını, çözücü yığınlarını, dikkat alt katmanlarını ve beslemeli alt katmanlarını incelemek için birkaç dakika ayırabilirsiniz. Ayrıca, sadece çalıştırmak istediğiniz hücreleri seçerek modelin belirli bir yönünü seçebilirsiniz:
```python
if display_architecture == True:
    print(model.encoder)
```
Çıktı, kodlayıcının yapısını gösterecektir:
```
T5Stack(
  (embed_tokens): Embedding(32128, 1024)
  (block): ModuleList(
    (0): T5Block(
      (layer): ModuleList(
        (0): T5LayerSelfAttention(
          (SelfAttention): T5Attention(
            (q): Linear(in_features=1024, out_features=1024, bias=False)
            (k): Linear(in_features=1024, out_features=1024, bias=False)
            (v): Linear(in_features=1024, out_features=1024, bias=False)
            (o): Linear(in_features=1024, out_features=1024, bias=False)
            (relative_attention_bias): Embedding(32, 16)
          )
          (layer_norm): T5LayerNorm()
          (dropout): Dropout(p=0.1, inplace=False)
        )
```
Çözücünün mimarisine bakalım:
```python
if display_architecture == True:
    print(model.decoder)
```
Çıktı, çözücünün yapısını gösterecektir:
```
T5Stack(
  (embed_tokens): Embedding(32128, 1024)
  (block): ModuleList(
    (0): T5Block(
      (layer): ModuleList(
        (0): T5LayerSelfAttention(
          (SelfAttention): T5Attention(
            (q): Linear(in_features=1024, out_features=1024, bias=False)
            (k): Linear(in_features=1024, out_features=1024, bias=False)
            (v): Linear(in_features=1024, out_features=1024, bias=False)
            (o): Linear(in_features=1024, out_features=1024, bias=False)
            (relative_attention_bias): Embedding(32, 16)
          )
          (layer_norm): T5LayerNorm()
          (dropout): Dropout(p=0.1, inplace=False)
        )
```
Beslemeli ağın mimarisine bakalım:
```python
if display_architecture == True:
    print(model.forward)
```
Çıktı, beslemeli ağı gösterecektir:
```
(1): T5LayerFF(
        (DenseReluDense): T5DenseActDense(
          (wi): Linear(in_features=1024, out_features=4096, bias=False)
          (wo): Linear(in_features=4096, out_features=1024, bias=False)
          (dropout): Dropout(p=0.1, inplace=False)
          (act): ReLU()
        )
```
Beslemeli ağın boyutlarının, temsillerin karmaşıklığını artırmak için 1024'ten 4096'ya çıkarıldığını ve ardından wo'nun çıktısı için 1024'e düşürüldüğünü unutmayın.

T5 transformer'ı başlattık. Şimdi bazı belgeleri özetleyelim.

---

