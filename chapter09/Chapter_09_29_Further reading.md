# Verilen İngilizce Paragrafın Türkçe Çevirisi

Hoover et al. , 2021, exBERT: Transformers Modellerinde Öğrenilen Gösterimleri Keşfetmek için Görsel Bir Analiz Araçları : https://arxiv.org/abs/1910.05276  
Jesse Vig , 2019, Transformer Modelinde Dikkatin Çok Ölçekli Görselleştirilmesi : https://aclanthology.org/P19-3007.pdf  
Discord'da Topluluğumuza Katılın  
Yazarlar ve diğer okuyucularla tartışmak için topluluğumuzun Discord alanına katılın: https://www.packt.link/Transformers

# Python Kodları Yok, Sadece Çeviri İstendiği İçin Kod Bloğu Bulunmamaktadır.

Ancak, eğer bir çeviri işlemi için python kodu istenseydi, aşağıdaki gibi bir kod örneği verilebilirdi:

```python
# Çeviri yapmak için kullanılan kütüphane: googletrans
from googletrans import Translator

def ingilizce_turkce_ceviri(paragraf):
    # Çeviri nesnesi oluştur
    translator = Translator()
    
    # Çeviri yap
    ceviri = translator.translate(paragraf, dest='tr')
    
    return ceviri.text

# Çevirisi yapılacak paragraf
paragraf = """Hoover et al. , 2021, exBERT: A Visual Analysis Tool to Explore Learned Representations in Transformers Models : https://arxiv.org/abs/1910.05276 Jesse Vig , 2019, A Multiscale Visualization of Attention in the Transformer Model : https://aclanthology.org/P19-3007.pdf Join our community on Discord Join our community’s Discord space for discussions with the authors and other readers: https://www.packt.link/Transformers"""

# Çeviri işlemini gerçekleştir
ceviri = ingilizce_turkce_ceviri(paragraf)

# Çeviriyi yazdır
print(ceviri)
```

## Kod Açıklaması
### 1. Gerekli Kütüphanenin İçe Aktarılması
```python
from googletrans import Translator
```
Bu satır, `googletrans` kütüphanesinden `Translator` sınıfını içe aktarır. Bu sınıf, metinleri farklı dillere çevirmek için kullanılır.

### 2. Çeviri Fonksiyonunun Tanımlanması
```python
def ingilizce_turkce_ceviri(paragraf):
```
Bu, `ingilizce_turkce_ceviri` adlı bir fonksiyon tanımlar. Bu fonksiyon, bir paragrafı İngilizce'den Türkçe'ye çevirir.

### 3. Çeviri Nesnesinin Oluşturulması
```python
translator = Translator()
```
Bu satır, `Translator` sınıfından bir nesne oluşturur. Bu nesne, çeviri işlemlerini gerçekleştirmek için kullanılır.

### 4. Çeviri İşlemi
```python
ceviri = translator.translate(paragraf, dest='tr')
```
Bu satır, `paragraf` değişkenindeki metni Türkçe'ye (`dest='tr'`) çevirir ve sonucu `ceviri` değişkenine atar.

### 5. Çeviri Sonucunun Dönmesi
```python
return ceviri.text
```
Bu satır, çeviri sonucunu döndürür.

### 6. Çeviri İşleminin Gerçekleştirilmesi ve Yazdırılması
```python
paragraf = """..."""
ceviri = ingilizce_turkce_ceviri(paragraf)
print(ceviri)
```
Bu satırlar, çevirisi yapılacak paragrafı tanımlar, çeviri işlemini gerçekleştirir ve sonucu yazdırır.

---

