# Hugging Face Transformer Uygulaması

Hugging Face, transformerları daha üst düzeyde uygulamak için bir çerçeve tasarladı. Örneğin, zaten 5. Bölüm'de, BERT aracılığıyla İnce Ayarlamaya Dalışta bir BERT modelini ince ayarlamak ve 6. Bölüm'de, RoBERTa aracılığıyla Sıfırdan Bir Transformer Eğitiminde bir RoBERTa modelini eğitmek için Hugging Face'i kullandık. Bu bölümde, yine Hugging Face'in çerçevesini kullanarak bir T5-large modelini uygulayacağız.

Python kodu bulunmamaktadır, sadece bir ingilizce paragrafın türkçeye çevrilmesi istenmiştir. 

Eğer python kodları olsaydı, satır satır açıklama aşağıdaki gibi yapılırdı:

Örnek python kodu:
```python
# import necessary libraries
import pandas as pd

# load data
data = pd.read_csv("data.csv")

# print data
print(data.head())
```
Açıklama:
1. `# import necessary libraries` : Gerekli kütüphaneleri içe aktarma
2. `import pandas as pd` : pandas kütüphanesini pd takma adıyla içe aktarır
3. `# load data` : verileri yükleme
4. `data = pd.read_csv("data.csv")` : "data.csv" dosyasını okuyarak data değişkenine atar
5. `# print data` : verileri yazdırma
6. `print(data.head())` : data değişkenindeki ilk birkaç satırı yazdırır.

---

