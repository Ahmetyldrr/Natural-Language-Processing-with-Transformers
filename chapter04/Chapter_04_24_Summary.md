# Bölüm Özeti

Bu bölümde, transformerlarla çeviri yapmanın temel yönlerini inceledik. Makine çevirisini tanımlayarak başladık. İnsan çevirisi, makinelerin ulaşması gereken yüksek bir standart belirler. İngilizce-Fransızca ve İngilizce-Almanca çevirilerin birçok problemi beraberinde getirdiğini gördük. Orijinal Transformer, bu sorunları ele aldı ve geçilmesi gereken state-of-the-art BLEU kayıtları belirledi. Daha sonra, temizlemeyi gerektiren Avrupa Parlamentosu'ndan bir WMT Fransızca-İngilizce veri setini ön işleme tabi tuttular. Veri setlerini satırlara dönüştürmek ve verileri temizlemek zorunda kaldık. Bu işlem yapıldıktan sonra, veri setinin boyutunu, bir frekans eşiğinin altında kalan kelimeleri kaldırarak küçülttük. Makine çevirisi NLP modelleri, aynı değerlendirme yöntemlerini gerektirir. Örneğin, bir WMT veri seti üzerinde bir model eğitmek, BLEU değerlendirmelerini gerektirir. Geometrik değerlendirmelerin, çevirileri puanlamak için iyi bir temel oluşturduğunu gördük, ancak değiştirilmiş BLEU'nun bile sınırları vardır. Bu nedenle, BLEU'yu geliştirmek için bir düzeltme tekniği ekledik.

# Trax ile İngilizce-Almanca Çeviri Uygulaması

Google Brain'in uçtan uca derin öğrenme kütüphanesi olan Trax'i kullanarak bir İngilizce-Almanca çeviri transformer'ı uyguladık. Google Translate'in standart bir çeviri API'si, medya akışı API'si ve özel AutoML model eğitimi hizmetleri sunduğunu gördük. Google Translate API'lerini uygulamak, proje sorunsuz bir şekilde ilerlerse AI geliştirme gerektirmeyebilir. Aksi takdirde, googletrans kütüphanesini kullanarak Google Translate AJAX API wrapper'ı ile eski günlerde olduğu gibi ellerimizi kirletmek zorunda kalacağız!

# Gelecek Adımlar

Son olarak, Gemini'nin Generative AI arayüzü ile konuşarak, çevirilere uygulanan LLMs'in potansiyelini ve sınırlamalarını inceledik. Artık transformerları ve mimarilerini oluşturan ana yapı taşlarını ele aldık ve gerçekleştirebilecekleri bazı NLP görevlerini gördük. Bir sonraki adım, belirli bir NLP görevine odaklanmak istediğimizde bir modeli fine-tune etmektir. Bölüm 5'te, BERT aracılığıyla Fine-Tuning'e dalacağız ve bir Transformer modelini fine-tune edeceğiz.

Python kodları bulunmamaktadır, ancak bir sonraki bölümde fine-tuning işlemi için BERT modeli kullanılacaktır. Bu işlem için gerekli python kodları aşağıdaki gibi açıklanabilir:

```python
# Gerekli kütüphanelerin import edilmesi
import pandas as pd
import torch
from transformers import BertTokenizer, BertModel

# Veri setinin yüklenmesi
train_data = pd.read_csv("train.csv")

# BERT modelinin ve tokenizer'ın yüklenmesi
tokenizer = BertTokenizer.from_pretrained('bert-base-uncased')
model = BertModel.from_pretrained('bert-base-uncased')

# Veri setinin tokenize edilmesi
input_ids = []
attention_masks = []
for sentence in train_data['sentence']:
    inputs = tokenizer.encode_plus(
        sentence,
        add_special_tokens=True,
        max_length=512,
        return_attention_mask=True,
        return_tensors='pt'
    )
    input_ids.append(inputs['input_ids'])
    attention_masks.append(inputs['attention_mask'])

# Fine-tuning işlemi için modelin hazırlanması
device = torch.device('cuda' if torch.cuda.is_available() else 'cpu')
model.to(device)

# Fine-tuning işlemi
for epoch in range(5):
    model.train()
    total_loss = 0
    for batch in train_data:
        input_ids = batch['input_ids'].to(device)
        attention_masks = batch['attention_mask'].to(device)
        labels = batch['label'].to(device)

        optimizer = torch.optim.Adam(model.parameters(), lr=1e-5)

        optimizer.zero_grad()

        outputs = model(input_ids, attention_mask=attention_masks, labels=labels)
        loss = outputs.loss

        loss.backward()
        optimizer.step()

        total_loss += loss.item()
    print(f'Epoch {epoch+1}, Loss: {total_loss / len(train_data)}')
```

Bu kod, BERT modelini fine-tuning işlemine tabi tutmak için kullanılır. İlk olarak, gerekli kütüphaneler import edilir ve veri seti yüklenir. Daha sonra, BERT modeli ve tokenizer yüklenir. Veri seti tokenize edilir ve fine-tuning işlemi için model hazırlanır. Son olarak, fine-tuning işlemi gerçekleştirilir.

---

