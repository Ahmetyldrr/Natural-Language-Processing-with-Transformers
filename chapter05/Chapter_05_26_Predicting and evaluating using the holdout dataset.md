# BERT Downstream Modelinin Değerlendirilmesi

BERT downstream modeli, in_domain_train.tsv veri seti ile eğitilmiştir. Program şimdi out_of_domain_dev.tsv dosyasında bulunan holdout (test ve değerlendirme) veri setini kullanarak tahminler yapacaktır. Amaç, cümlenin gramatik olarak doğru olup olmadığını tahmin etmektir. Kodun aşağıdaki alıntıları, değerlendirme sürecinin ana adımlarını göstermektedir.

## Veri Hazırlama

İlk olarak, eğitim verilerine uygulanan veri hazırlama süreci, holdout veri seti için kodun bir kısmında tekrarlanır:
```python
df = pd.read_csv("out_of_domain_dev.tsv", delimiter='\t', header=None, names=['sentence_source', 'label', 'label_notes', 'sentence'])
df.shape
```
`df.shape` çıktısı, değerlendirme yapılacak satır sayısını ve veri setinin şeklini gösterir: (516, 4)

## Değerlendirme Süreci

Ardından, değerlendirme süreci, değerlendirme yapılacak cümleleri ve etiketlerini oluşturarak başlar:
```python
# Cümle ve etiket listeleri oluştur
sentences = df.sentence.values
# BERT'in düzgün çalışması için her cümlenin başına ve sonuna özel tokenler eklememiz gerekir
sentences = ["[CLS] " + sentence + " [SEP]" for sentence in sentences]
labels = df.label.values
tokenized_texts = [tokenizer.tokenize(sent) for sent in sentences]
```
...

## Toplu Tahminler

Program daha sonra dataloader kullanarak toplu tahminler yapar:
```python
# Tahmin için
for batch in prediction_dataloader:
    # Batch'i GPU'ya ekle
    batch = tuple(t.to(device) for t in batch)
    # Dataloader'dan girdileri ayır
    b_input_ids, b_input_mask, b_labels = batch
    # Modelin gradyan hesaplamamasını ve saklamamasını söyle, hafızadan tasarruf et ve tahminleri hızlandır
    with torch.no_grad():
        # İleri besleme, logit tahminleri hesapla
        logits = model(b_input_ids, token_type_ids=None, attention_mask=b_input_mask)
```
Tahminlerin logitleri ve etiketleri CPU'ya taşınır:
```python
# Logitleri ve etiketleri CPU'ya taşı
logits = logits['logits'].detach().cpu().numpy()
label_ids = b_labels.to('cpu').numpy()
```
Ardından, değerlendirme, en yüksek olasılığa sahip sınıfı seçerek yapılır:
```python
# Tahmin edilen sınıf, en yüksek olasılığa sahip olanıdır
batch_predictions = np.argmax(probabilities, axis=1)
```
Bu sürece daha detaylı bir şekilde aşağıdaki alt bölümde bakalım.

---

