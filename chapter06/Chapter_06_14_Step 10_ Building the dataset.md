# Programın Veri Setini Yüklemesi ve Örnek Oluşturması

Program şimdi, toplu eğitim için örnekler oluşturmak üzere veri setini satır satır yükleyecek; `block_size=128` bir örneğin uzunluğunu sınırlıyor:

```python
%%time 
from transformers import LineByLineTextDataset
dataset = LineByLineTextDataset(
    tokenizer=tokenizer,
    file_path="./kant.txt",
    block_size=128,
)
```

- `%%time`: Bu, Jupyter Notebook'larda kullanılan bir komuttur ve bir hücrenin çalıştırılmasının ne kadar sürdüğünü ölçer.
- `from transformers import LineByLineTextDataset`: Bu satır, `transformers` kütüphanesinden `LineByLineTextDataset` sınıfını içe aktarır. Bu sınıf, metin dosyalarını satır satır okuyarak bir veri seti oluşturmak için kullanılır.
- `dataset = LineByLineTextDataset(...)`: Bu satır, `LineByLineTextDataset` sınıfının bir örneğini oluşturur ve `dataset` değişkenine atar.
  - `tokenizer=tokenizer`: Oluşturulan veri setindeki metinleri tokenlara ayırmak için kullanılan tokenizer nesnesini belirtir.
  - `file_path="./kant.txt"`: Okunacak metin dosyasının yolunu belirtir.
  - `block_size=128`: Her bir örneğin maksimum uzunluğunu belirler. Bu, modelin girdi olarak kabul ettiği maksimum token sayısına karşılık gelir.

Çıktı, Hugging Face'in veri işleme süresini optimize etmek için önemli miktarda kaynak harcadığını gösteriyor:

- `CPU times: user 25.9 s, sys: 375 ms, total: 26.3 s`: Bu, işlemci tarafından harcanan toplam zamanı gösterir. 
  - `user 25.9 s`: Kullanıcı modunda harcanan zaman.
  - `sys: 375 ms`: Sistem çağrıları için harcanan zaman.
  - `total: 26.3 s`: Toplam geçen zaman.
- `Wall time: 26.9 s`: Bu, işlemin başlangıcından sonuna kadar geçen gerçek zamanı gösterir. Bu, işlemcilerin aktif olarak çalıştığı gerçek süreyi temsil eder ve optimize edilmiştir.

# Veri Collator Tanımlama

Program şimdi, geri yayılım (backpropagation) için bir nesne oluşturmak üzere bir veri collator tanımlayacak.

---

