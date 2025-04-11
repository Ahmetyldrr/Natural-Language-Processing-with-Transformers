# İngilizce-Almanca BLEU Skorları ile İlgili Kaynaklar ve Kodlar
Referans kağıtları ve kodları ile İngilizce-Almanca BLEU skorları: https://paperswithcode.com/sota/machine-translation-on-wmt2014-english-german

# 2014 Makine Çevirisi Çalıştayı (WMT)
2014 Makine Çevirisi Çalıştayı (WMT): https://www.statmt.org/wmt14/translation-task.html

# Avrupa Parlamentosu Tutanakları Paralel Korpus 1996-2011
Avrupa Parlamentosu Tutanakları Paralel Korpus 1996-2011, Fransızca-İngilizce paralel korpus: https://www.statmt.org/europarl/v7/fr-en.tgz

# Makine Çevirisi için Fransızca-İngilizce Veri Kümesi Hazırlama
Jason Brownlee, Ph.D., Makine Çevirisi için Fransızca-İngilizce Veri Kümesi Nasıl Hazırlanır: https://machinelearningmastery.com/prepare-french-english-dataset-machine-translation/

# Python'da Metin için BLEU Skorunun Hesaplanması
Jason Brownlee, Ph.D., Python'da Metin için BLEU Skorunun Hesaplanması için Yumuşak Bir Giriş: https://machinelearningmastery.com/calculate-bleu-score-for-text-python/

# Cümle Seviyesinde BLEU için Düzeltme Tekniklerinin Sistematik Karşılaştırılması
Boxing Chen ve Colin Cherry, 2014, Cümle Seviyesinde BLEU için Düzeltme Tekniklerinin Sistematik Karşılaştırılması: http://acl2014.org/acl2014/W14-33/pdf/W14-3346.pdf

# Trax Depolama Alanı
Trax depolama alanı: https://github.com/google/trax

# Trax Eğitimi
Trax eğitimi: https://trax-ml.readthedocs.io/en/latest/

Paragrafta Python kodları bulunmamaktadır. Ancak BLEU skoru hesaplama ile ilgili Python kodları aşağıdaki gibidir:

BLEU skoru hesaplama kodu:
```python
from nltk.translate.bleu_score import sentence_bleu

reference = [['this', 'is', 'a', 'test'], ['this', 'is', 'another', 'test']]
candidate = ['this', 'is', 'a', 'test']

score = sentence_bleu(reference, candidate)
print(score)
```
Bu kodun açıklaması:

1. `nltk.translate.bleu_score` modülünden `sentence_bleu` fonksiyonu içe aktarılır.
2. `reference` değişkeni, referans çevirileri içeren bir liste olarak tanımlanır. Bu liste içinde birden fazla referans çeviri olabilir.
3. `candidate` değişkeni, makine çevirisi çıktısını içeren bir liste olarak tanımlanır.
4. `sentence_bleu` fonksiyonu, `reference` ve `candidate` değişkenlerini kullanarak BLEU skorunu hesaplar.
5. Hesaplanan BLEU skoru `score` değişkenine atanır ve yazdırılır.

Not: Bu kodun çalışması için `nltk` kütüphanesinin kurulu olması gerekir. Kurulum için `pip install nltk` komutu kullanılabilir.

---

