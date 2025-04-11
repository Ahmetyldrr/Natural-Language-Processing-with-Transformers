# CoLA Veri Kümesinin Yüklenmesi

Warstadt ve diğerlerinin (2018) makalesine dayanarak CoLA'yı yükleyeceğiz. Doğal Dil İşleme (NLP) alanında dilbilimsel kabul edilebilirliği değerlendirmek kritik öneme sahiptir. Gerekirse, 3. Bölüm'ün CoLA bölümünü, "Emergent vs Downstream Tasks: The Unseen Depths of Transformers" başlıklı kısmı gözden geçirmek için bir an durun. Bu bölümde uygulanan veri kümesi CoLA ana sayfasından elde edilmiştir: https://nyu-mll.github.io/CoLA/ ve bu bölümün GitHub dizinine yüklenmiştir. Notebook'taki aşağıdaki hücreler, ince ayar için gerekli dosyaları (`in_domain_train.tsv`) ve ince ayarlı modelin tahminlerini değerlendirmek için (`out_of_domain_dev.tsv`) otomatik olarak indirir:

```python
import os
!curl -L https://raw.githubusercontent.com/Denis2054/Transformers-for-NLP-and-Computer-Vision-3rd-Edition/master/Chapter05/in_domain_train.tsv --output "in_domain_train.tsv"
!curl -L https://raw.githubusercontent.com/Denis2054/Transformers-for-NLP-and-Computer-Vision-3rd-Edition/master/Chapter05/out_of_domain_dev.tsv --output "out_of_domain_dev.tsv"
```

Bu kodlar:
- `import os`: OS modülünü içe aktarır, işletim sistemiyle etkileşim için kullanılır.
- `!curl -L <url> --output "<dosya_adı>"`: Curl komutunu kullanarak belirtilen URL'deki dosyayı indirir ve belirtilen dosya adı ile kaydeder. `!` işareti, Jupyter Notebook'ta komut satırı komutlarını çalıştırmak için kullanılır.

Bu dosyaları dosya yöneticisinde görünür olmaları gerekir: 
# Şekil 5.6: Veri Kümelerinin Yüklenmesi

Şimdi, program veri kümelerini yükleyecek:

```python
# Veri kümesinin kaynağı: https://nyu-mll.github.io/CoLA/
df = pd.read_csv("in_domain_train.tsv", delimiter='\t', header=None, names=['sentence_source', 'label', 'label_notes', 'sentence'])
df.shape
```

Bu kod:
- `df = pd.read_csv(...)`: `in_domain_train.tsv` dosyasını pandas kütüphanesini kullanarak okur. 
  - `delimiter='\t'`: Dosyanın sekme (`\t`) ile ayrıldığını belirtir.
  - `header=None`: Dosyanın ilk satırının başlık olmadığını belirtir.
  - `names=['sentence_source', 'label', 'label_notes', 'sentence']`: Sütunlara isim verir.

Çıktı, içe aktardığımız veri kümesinin şeklini gösterir: (8551, 4)

Kabul edilebilirlik yargı görevini görselleştirmek için 10 satırlık bir örnek görüntülenir:

```python
df.sample(10)
```

Bu kod:
- `df.sample(10)`: Veri kümesinden rastgele 10 satır seçer.

Çıktı, her çalıştırma sonrasında değişebilen etiketli veri kümesinin 10 satırını gösterir:
# Şekil 5.7: Etiketli Veri Kümesinin 10 Satırı

`.tsv` dosyalarındaki her bir örnek, dört sekme ile ayrılmış sütun içerir (sütun 0 bir dizinidir):
- Sütun 1: Cümlenin kaynağı (kod).
- Sütun 2: Etiket (0 = kabul edilemez, 1 = kabul edilebilir).
- Sütun 3: Yazar tarafından ek açıklamalı etiket.
- Sütun 4: Sınıflandırılacak cümle.

`.tsv` dosyalarını yerel olarak açarak veri kümesinin birkaç örneğini okuyabilirsiniz.

Program şimdi BERT modeli için verileri işleyecek.

---

