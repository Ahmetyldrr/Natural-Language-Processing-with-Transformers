# 5. Bölüm: Transformer Modelini İnce Ayarlama

Bu bölümde, bir transformer modelini ince ayarlamanın sürecini keşfettik. Bunu, önceden eğitilmiş bir Hugging Face BERT modelinin ince ayar sürecini uygulayarak başardık. BERT'in mimarisini analiz ederek başladık, bu model sadece transformer'ların kodlayıcı yığını kullanır ve çift yönlü dikkat kullanır. BERT, iki adımlı bir çerçeve olarak tasarlandı. Çerçevenin ilk adımı bir modeli önceden eğitmek. İkinci adım ise modeli ince ayarlamaktır. Daha sonra, bir kabul edilebilirlik yargısı aşağı akış görevi için bir ince ayar BERT modeli yapılandırdık. İnce ayar süreci, sürecin tüm aşamalarından geçti. Hugging Face transformer'ları kurduk ve torch için cihaz olarak CUDA'yı seçmek de dahil olmak üzere donanım kısıtlamalarını dikkate aldık. CoLA veri setini GitHub'dan aldık. Alan içi (eğitim verileri) cümleleri, etiket listeleri ve BERT token'ları yükledik ve oluşturduk. Eğitim verileri, BERT tokenleştiricisi ve dikkat maskeleri dahil olmak üzere diğer veri hazırlama işlevleri ile işlendi. Daha sonra veriler eğitim ve doğrulama kümelerine ayrıldı. İşlemi optimize etmek için bir parti boyutu seçtik ve bir yineleyici oluşturduk. Daha sonra bir Hugging Face BERT uncased base modeli yükledik. İşlem, başka bir tokenleştirici ve GPT-2, T5, RoBERTa veya diğerleri gibi başka bir Hugging Face önceden eğitilmiş model ile uygulanabilirdi.

## Parametrelerin Gruplanması ve Hiperparametrelerin Tanımlanması

Parametreleri grupladık, hiperparametreleri tanımladık ve işlem sırasında değerlendirmeler de dahil olmak üzere eğitim döngüsünü çalıştırdık. Eğitim tamamlandıktan sonra, ince ayarlı modelin çıktısını değerlendirmek için alan dışı tutulan veri setini kullandık. Tahmin sürecini keşfettik ve sonuçları değerlendirmek için Matthews korelasyon katsayısını uyguladık. Son olarak, eğitilmiş modelimizle etkileşimde bulunmak için ipywidgets ile bir arayüz oluşturduk.

# İnce Ayar ve Önceden Eğitim

Önceden eğitilmiş bir modeli ince ayarlamak, sıfırdan bir model eğitmekten daha az makine kaynağı gerektirir. İnce ayarlı modeller çeşitli görevleri yerine getirebilir. Ancak bazı durumlarda, bir modeli ince ayarlamak hedefimize ulaşmak için yeterli değildir. Örneğin, bir transformer modelini pratik olarak sıfırdan önceden eğitmemiz gerekebilir. Bir sonraki bölüm olan # 6. Bölüm: RoBERTa ile Sıfırdan Bir Transformer'ı Önceden Eğitme bölümünde, sıfırdan bir transformer modeli oluşturacağız ve önceden eğiteceğiz.

Python kodları bulunmamaktadır, ancak yukarıdaki metinde bahsedilen bazı işlemler python kodları ile gerçekleştirilebilir. İşte bazı örnekler:

### Hugging Face Transformer'ları Kurma

```python
pip install transformers
```

### CoLA Veri Setini Alma

```python
import pandas as pd

# CoLA veri setini GitHub'dan indirin
# Veri setini yüklemek için pandas kütüphanesini kullanın
train_df = pd.read_csv("https://raw.githubusercontent.com/nyu-mll/GLUE-baselines/master/data/CoLA/train.tsv", sep='\t')
```

### BERT Tokenleştiricisi ile Veri Hazırlama

```python
from transformers import BertTokenizer

# BERT tokenleştiricisini yükleyin
tokenizer = BertTokenizer.from_pretrained('bert-base-uncased')

# Veri hazırlama işlevi
def prepare_data(sentences, labels):
    inputs = tokenizer(sentences, return_tensors='pt', padding=True, truncation=True)
    labels = torch.tensor(labels)
    return inputs, labels

# Eğitim verilerini hazırlayın
train_inputs, train_labels = prepare_data(train_df['sentence'], train_df['label'])
```

### Eğitim ve Doğrulama Kümelerine Ayırma

```python
from sklearn.model_selection import train_test_split

# Verileri eğitim ve doğrulama kümelerine ayırın
train_inputs, val_inputs, train_labels, val_labels = train_test_split(train_inputs, train_labels, test_size=0.2, random_state=42)
```

### Modeli Yükleme ve Eğitme

```python
from transformers import BertForSequenceClassification

# BERT modelini yükleyin
model = BertForSequenceClassification.from_pretrained('bert-base-uncased', num_labels=2)

# Modeli eğitme
device = torch.device('cuda' if torch.cuda.is_available() else 'cpu')
model.to(device)
train_inputs = train_inputs.to(device)
train_labels = train_labels.to(device)

# Eğitim döngüsü
for epoch in range(5):
    model.train()
    optimizer = torch.optim.Adam(model.parameters(), lr=1e-5)
    loss = model(train_inputs['input_ids'], attention_mask=train_inputs['attention_mask'], labels=train_labels)
    loss.backward()
    optimizer.step()
    model.eval()
    # Değerlendirme
    with torch.no_grad():
        outputs = model(val_inputs['input_ids'], attention_mask=val_inputs['attention_mask'])
        logits = outputs.logits
        # Matthews korelasyon katsayısını hesaplayın
        matthews_corrcoef = matthews_corrcoef(val_labels, torch.argmax(logits, dim=1))
        print(f'Epoch {epoch+1}, Matthews Corrcoef: {matthews_corrcoef}')
```

---

