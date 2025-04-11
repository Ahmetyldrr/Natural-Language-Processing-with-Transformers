# Gömmeleri TensorFlow Embedding Projector ile Görselleştirme
Gömmeleri TensorFlow Embedding Projector ile görselleştirebiliriz: https://projector.tensorflow.org/ Gömmeleri görselleştirmek için iki dosya oluşturmamız gerekir: Gömmeleri içeren bir vektör dosyası. Genellikle TSV ( Sekmeyle Ayrılmış Değerler ) formatında vecs.tsv adlı bir dosyadır. Etiketleri, bu durumda kelimeleri içeren bir meta veri dosyası. Genellikle TSV formatında meta.tsv adlı bir dosyadır. Her iki dosya da vektörleri ve etiketleri aynı sırayla içermelidir. İki dosyayı oluşturmak ve kaydetmek için bir fonksiyon yazalım:

```python
import csv
import os
import numpy as np

# Dosyaları kaydetmek istediğiniz dizin
LOG_DIR = '/content'
os.makedirs(LOG_DIR, exist_ok=True)

# Kelimeleri ve vektörleri al
words = list(model.wv.key_to_index.keys())
vectors = [model.wv[word] for word in words]

# Vektörleri .tsv dosyasına yaz
with open(os.path.join(LOG_DIR, "vecs.tsv"), 'w', newline='') as f:
    writer = csv.writer(f, delimiter='\t')
    writer.writerows(vectors)

# Etiketleri (kelimeleri) ayrı bir .tsv dosyasına yaz
with open(os.path.join(LOG_DIR, "meta.tsv"), 'w', newline='', encoding='utf-8') as f:
    writer = csv.writer(f, delimiter='\t')
    writer.writerows([[word] for word in words])
```

## Kod Açıklaması

1. `import csv`: csv modülünü içe aktarır, bu modül CSV dosyalarını okumak ve yazmak için kullanılır.
2. `import os`: os modülünü içe aktarır, bu modül işletim sistemi ile etkileşim için kullanılır.
3. `import numpy as np`: numpy kütüphanesini np takma adı ile içe aktarır, bu kütüphane sayısal işlemler için kullanılır.
4. `LOG_DIR = '/content'`: dosyaları kaydetmek istediğimiz dizini belirler.
5. `os.makedirs(LOG_DIR, exist_ok=True)`: belirtilen dizini oluşturur, eğer dizin zaten varsa hata vermez.
6. `words = list(model.wv.key_to_index.keys())`: modeldeki kelimeleri bir liste olarak alır.
7. `vectors = [model.wv[word] for word in words]`: kelimelere karşılık gelen vektörleri bir liste olarak alır.
8. `with open(os.path.join(LOG_DIR, "vecs.tsv"), 'w', newline='') as f:`: vecs.tsv dosyasını yazma modunda açar.
9. `writer = csv.writer(f, delimiter='\t')`: csv yazıcısını sekme karakteri ile ayarlama yapar.
10. `writer.writerows(vectors)`: vektörleri dosyaya yazar.
11. `with open(os.path.join(LOG_DIR, "meta.tsv"), 'w', newline='', encoding='utf-8') as f:`: meta.tsv dosyasını yazma modunda açar.
12. `writer.writerows([[word] for word in words])`: kelimeleri dosyaya yazar.

## TensorFlow Projector'a Dosyaları Yükleme

Çıktı olarak TensorFlow Projector'a yüklemek için gerekli iki dosya: vecs.tsv ve meta.tsv. Bu dosyaları yerel olarak kaydedebilir ve ardından TensorFlow Projector'a yükleyebilirsiniz.

Dosyaların boyutlarını kontrol edebilirsiniz:
```bash
!echo "Vectors file (vecs.tsv) size:"
!wc -l /content/vecs.tsv
!echo "Metadata file (meta.tsv) size:"
!wc -l /content/meta.tsv
```

Bu durumda çıktı, dosyaların aynı boyutta olduğunu doğrular:
```
Vectors file (vecs.tsv) size:
3843 /content/vecs.tsv
Metadata file (meta.tsv) size:
3843 /content/meta.tsv
```

## TensorFlow Projector'da Görselleştirme

Dosyaları yerel olarak kaydettikten sonra, TensorFlow Projector sitesine gidin: https://projector.tensorflow.org/. Yükleme düğmesine tıklayın ve dosyaları yükleyin.

Dosyalar yüklendikten sonra, kelime gömmelerinin veri noktalarını göreceksiniz. Her nokta bir kelimeyi temsil eder. Kelimenin vektörü noktanın konumunu belirler.

Bir kelime seçebilir (örneğin "think") ve benzer kelimeleri görselleştirebilirsiniz.

Bu örnekteki küresel görselleştirme, veri kümesine Uygulanan Ana Bileşen Analizi (PCA) ile oluşturuldu. PCA, karmaşık verileri basitleştirmek için kullanılan bir istatistiksel tekniktir.

## Ana Bileşen Analizi (PCA)

PCA, değişkenler arasındaki korelasyonu algılar ve ardından değişkenleri "ana bileşenler" kümesine birleştirerek sayısını azaltır. Bu bileşenler, orijinal değişkenlerdeki varyasyonun çoğunu koruyacak şekilde sıralanır.

Artık gömme tabanlı arama tekniklerinin muazzam potansiyelini tam olarak anlamak için temel bilgileri ele aldık. Şimdi, gömme tabanlı tekniklerle soru-cevap sistemlerini uygulayacağız.

---

