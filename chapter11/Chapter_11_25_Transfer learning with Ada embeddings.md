# Bölüm Çevirisi

Bu bölümde, daha ileri gideceğiz, bir embeddings fonksiyonu çalıştıracağız, k-means kümeleme algoritması ile embeddings kümeleri oluşturacağız ve davinci'ye her bir kümenin temasını ilgili yorumlarla birlikte metin formatında tanımlamasını soracağız.

# Kodları İnceleme

Github deposundaki chapter notebook klasöründe bulunan `Transfer_Learning_with_Ada_Embeddings.ipynb` dosyasını açın.

## Not
Bazı durumlarda, bir proje kritik, maliyetli olabilir ve kararlılık gerektirebilir. Proje yönetimi prosedürleri olmadan kaynak kodunu güncellemek her zaman mümkün değildir. Bu durumda, geriye dönük uyumluluk için bu bölümde yaptığımız gibi OpenAI'ın sürümünü sabitleyebiliriz: 
```python
!pip install openai==0.28
```
## Notebook İçeriği

Notebook'un ilk hücreleri OpenAI, tiktoken ve Kaggle'ı kurar. Ardından notebook, OpenAI ve Kaggle için API anahtarlarını ayarlar. OpenAI ve Kaggle için bir hesaba ihtiyacınız olacak.

### Açıklamalar

1. `!pip install openai==0.28` : Bu komut, OpenAI kütüphanesini belirli bir sürümde (0.28) kurar. 
   - `!` işareti, Jupyter notebook içinde komut çalıştırma özelliğini kullanır.
   - `pip install` komutu Python paketlerini kurmak için kullanılır.
   - `openai==0.28` ifadesi, kurulacak paketin OpenAI olduğunu ve 0.28 sürümünde olmasını gerektiğini belirtir.

2. API anahtarlarının ayarlanması genellikle aşağıdaki gibi yapılır:
   ```python
import openai
openai.api_key = "API-ANAHTARINIZ"
```
   - Burada "API-ANAHTARINIZ" kısmına OpenAI'den alınan gerçek API anahtarınız yazılır.

3. Kaggle API anahtarını ayarlamak için ise genellikle aşağıdaki komut kullanılır:
   ```python
import os
os.environ['KAGGLE_USERNAME'] = "KAGGLE-KULLANICI-ADINIZ"
os.environ['KAGGLE_KEY'] = "KAGGLE-API-ANAHTARINIZ"
```
   - Burada "KAGGLE-KULLANICI-ADINIZ" ve "KAGGLE-API-ANAHTARINIZ" kısımlarına sırasıyla Kaggle kullanıcı adınız ve API anahtarınız yazılır.

---

