# CoLA Veri Kümesinin Tanımı ve Kullanımı

CoLA, bir GLUE görevi (https://gluebenchmark.com/tasks), binlerce İngilizce cümle örneği içerir ve bu cümleler gramatik kabul edilebilirlik açısından etiketlenmiştir. Alex Warstadt ve ekibinin (2019) amacı, bir NLP modelinin bir cümlenin dilbilimsel kabul edilebilirliğini değerlendirme konusundaki dilbilimsel yeterliliğini test etmekti. NLP modelinin cümleleri buna göre sınıflandırması beklenmektedir. Cümleler gramatik veya gramatik olmayan olarak etiketlenir. Cümle gramatik olarak kabul edilemezse 0, gramatik olarak kabul edilebilirse 1 olarak etiketlenir. Örneğin: Sınıflandırma = 1 için "we yelled ourselves hoarse." Sınıflandırma = 0 için "we yelled ourselves.". BERT modelini CoLA veri kümelerinde ince-tune ettiğimiz 5. Bölüm, BERT ile İnce-Ayar'a Dalış'taki BERT_Fine_Tuning_Sentence_Classification_GPU.ipynb dosyasını inceleyebilirsiniz.

# Veri Kümesinin Yüklenmesi

CoLA verilerini kullandık. Öncelikle veri kümesini yükleyeceğiz:

```python
# Veri kümesinin kaynağı: https://nyu-mll.github.io/CoLA/
df = pd.read_csv("in_domain_train.tsv", delimiter='\t', header=None, names=['sentence_source', 'label', 'label_notes', 'sentence'])
df.shape
```

- `pd.read_csv`: Pandas kütüphanesinin CSV dosyalarını okumak için kullanılan fonksiyonudur.
- `"in_domain_train.tsv"`: Okunacak dosyanın adı. Bu dosya, CoLA veri kümesinin bir parçasıdır ve sekme ile ayrılmış değerler içerir.
- `delimiter='\t'`: Dosyadaki değerlerin sekmelerle ayrıldığını belirtir.
- `header=None`: Dosyanın ilk satırının başlık satırı olmadığını belirtir.
- `names=['sentence_source', 'label', 'label_notes', 'sentence']`: Dosyadaki sütunların isimlerini tanımlar.

# Önceden Eğitilmiş BERT Modelinin Yüklenmesi

Ayrıca, önceden eğitilmiş bir Hugging Face BERT modelini yükleyeceğiz:

```python
model = BertForSequenceClassification.from_pretrained("bert-base-uncased", num_labels=2)
```

- `BertForSequenceClassification`: Hugging Face Transformers kütüphanesinde bulunan, dizilim sınıflandırma görevleri için kullanılan bir BERT model sınıfıdır.
- `from_pretrained`: Önceden eğitilmiş bir modeli yüklemek için kullanılan yöntemdir.
- `"bert-base-uncased"`: Yüklenecek önceden eğitilmiş modelin adı. Bu, küçük harflere dönüştürülmüş metinlerde eğitilmiş temel BERT modelidir.
- `num_labels=2`: Sınıflandırma görevinde kullanılacak etiket sayısını belirtir. Bu örnekte, iki sınıf vardır: gramatik ve gramatik olmayan.

# Değerlendirme Metodu

Son olarak, kullandığımız ölçüm yöntemi veya metriği MCC'dir (Matthew's Correlation Coefficient), bu bölümün MCC bölümünde anlatılmıştır. MCC'nin matematiksel tanımı için o bölüme başvurabilirsiniz ve gerekirse kaynak kodunu yeniden çalıştırarak zamanı değerlendirebilirsiniz.

Bir cümle gramatik olarak kabul edilemez olabilir ancak yine de bir duygu ifade edebilir. Duygu analizi, bir makineye bir tür empati ekleyebilir.

---

