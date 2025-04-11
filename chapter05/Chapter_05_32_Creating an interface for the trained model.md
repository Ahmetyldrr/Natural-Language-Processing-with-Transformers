# Modeli Değerlendirme Moduna Alma ve Tahmin Fonksiyonu Oluşturma

İlk olarak, modelin değerlendirme modunda olduğundan emin olun: 
```python
from transformers import BertTokenizer, BertForSequenceClassification 
import torch
model.eval()  # modeli değerlendirme moduna ayarla
```
Şimdi, aşağıdaki kod parçasında gösterildiği gibi modelle etkileşimde bulunmak için bir fonksiyon oluşturuyoruz:
```python
def predict(sentence, model, tokenizer):
    # [CLS] ve [SEP] tokenlerini ekleyin
    sentence = "[CLS] " + sentence + " [SEP]"
    # Cümleyi tokenleştirin
    tokenized_text = tokenizer.tokenize(sentence)
```
Fonksiyonu şu şekilde özetleyebiliriz: 
Fonksiyon üç parametre alır: bir cümle, bir model ve bir tokenizer.
- Cümle, BERT benzeri modellerde kullanılan özel tokenler olan [CLS] ve [SEP] tokenleri eklenerek ön işleme tabi tutulur.
- Cümle, sağlanan tokenizer kullanılarak alt kelimelere tokenleştirilir.

### Tokenleştirme ve Tensör Dönüşümü

- Tokenler, modelin sözlüğünden karşılık gelen ID'lere dönüştürülür.
- Her token için, tek bir dizi olduğu için 0'a ayarlanmış bir segment ID tanımlanır.
- Token ID'leri ve segment ID'leri listeleri PyTorch tensörlerine dönüştürülür.

### Tahmin Yapma

- Model kullanılarak gradyanları güncellenmeden bir tahmin yapılır.
- Model, ham tahmin değerlerini temsil eden logits çıktıları verir.
- En yüksek logit değerine sahip etiket, tahmin edilen etiket olarak seçilir.
- Tahmin edilen etiket döndürülür.

Artık modelle etkileşimde bulunabiliriz.

---

