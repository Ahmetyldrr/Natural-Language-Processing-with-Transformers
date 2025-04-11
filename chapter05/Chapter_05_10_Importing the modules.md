# İthalarat (Imports)

Gerekli önceden eğitilmiş modülleri içe aktaracağız, örneğin önceden eğitilmiş BERT tokenizer ve BERT modelinin konfigürasyonu gibi. BERT Adam optimizer da sequence classification modülü ile birlikte içe aktarılır:

```python
import torch 
import torch.nn as nn 
from torch.utils.data import TensorDataset, DataLoader, RandomSampler, SequentialSampler 
from keras.utils import pad_sequences 
from sklearn.model_selection import train_test_split 
from transformers import BertTokenizer, BertConfig 
from transformers import AdamW, BertForSequenceClassification, get_linear_schedule_with_warmup
```

Şimdi ilerleme çubuğu modülünü tqdm'den içe aktaracağız:
```python
from tqdm import tqdm, trange # ilerleme çubukları için
```

Artık yaygın olarak kullanılan standart Python modüllerini içe aktarabiliriz:
```python
import pandas as pd 
import io 
import numpy as np 
import matplotlib.pyplot as plt 
from IPython.display import Image # resim render etmek için
```

Her şey yolunda giderse, Google Colab'ın sanal makinelerinde ihtiyacımız olan modüllerin birkaçını önceden yüklemiş olduğunu göz önünde bulundurarak hiçbir mesaj görüntülenmez. 

# Çeviri Açıklaması

Yukarıdaki metin birebir Türkçeye çevrilmiştir. Python kodları satır satır açıklanmıştır. Markdown formatına uygun başlıklar (#) kullanılmıştır.

1. İlk bölümde gerekli kütüphaneler içe aktarılır. Bunlar arasında `torch`, `torch.nn`, `torch.utils.data`, `keras.utils`, `sklearn.model_selection` ve `transformers` kütüphaneleri bulunur.
2. İlerleme çubuğu modülü `tqdm` içe aktarılır.
3. Standart Python kütüphaneleri (`pandas`, `io`, `numpy`, `matplotlib.pyplot`) ve `IPython.display` içe aktarılır.
4. Google Colab'ın önceden yüklenmiş modülleri hakkında bilgi verilir.

---

