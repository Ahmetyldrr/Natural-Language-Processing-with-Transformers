# KantaiBERT'i Sıfırdan Oluşturma

    KantaiBERT'i sıfırdan 15 adımda oluşturacağız ve bir MLM örneğinde çalıştıracağız. Google Colaboratory'i açın (Gmail hesabınızın olması gerekir). Ardından, bu bölümün GitHub dizininde bulunan KantaiBERT.ipynb dosyasını yükleyin. Bu bölümün 15 adımının başlıkları, not defteri hücrelerinin başlıklarına benzer, bu da onları takip etmeyi kolaylaştırır. Veri setini yükleyerek başlayalım.

Python kodu bulunmamaktadır, bu nedenle açıklama yapmaya gerek yoktur. Çeviri birebir yapılmıştır. 

Eğer bir python kodu olsaydı, örneğin:
```python
# Veri setini yükleme
import pandas as pd

# Veri setini oku
data = pd.read_csv('data.csv')

# İlk 5 satırı göster
print(data.head())
```
Yukarıdaki kod için satır satır açıklama aşağıdaki gibi olurdu:
1. `import pandas as pd`: pandas kütüphanesini `pd` takma adıyla içe aktarır.
2. `data = pd.read_csv('data.csv')`: `data.csv` dosyasını okuyarak `data` değişkenine atar.
3. `print(data.head())`: `data` değişkenindeki veri setinin ilk 5 satırını yazdırır.

---

