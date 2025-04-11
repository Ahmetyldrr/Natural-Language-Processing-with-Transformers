# İngilizce Paragrafın Türkçe Çevirisi

Geliştirici istemi sağlar ve GPT-4 talimatlarla yanıt verir: Denis Rothman: Google Colab'da wikiart'tan resimleri görüntüleyebilen bir Python programı yazmak istiyorum. Nasıl başlarım? GPT-4:Python kullanarak bir Google Colab not defterinde Wikiart'tan resimleri görüntülemek için şu adımları takip edebilirsiniz... GPT-4'ün talimatlarının geri kalanını not defterinde okuyun ve kodu çalıştırın:

# Python Kodları ve Açıklamaları

```python
# Gerekli kütüphaneleri içe aktarın
import requests 
from IPython.display import Image, display

# Wikiart'tan bir resmi görüntülemek için fonksiyon
def display_wikiart_image(url):
    # URL'ye GET isteği gönder
    response = requests.get(url)
    
    # İstek başarılıysa (200 durum kodu)
    if response.status_code == 200:
        # Yanıt içeriğinden bir Image nesnesi oluştur
        img = Image(data=response.content)
        # Resmi görüntüle
        display(img)
    else:
        # İstek başarısızsa hata mesajı yazdır
        print("Resim alınamadı")

# Aşağıdaki URL'yi istenen Wikiart resmi URL'si ile değiştirin
wikiart_image_url = "https://uploads7.wikiart.org/images/salvador-dali/the-persistence-of-memory-1931.jpg"

# Fonksiyonu çağırarak resmi görüntüle
display_wikiart_image(wikiart_image_url)
```

Her bir fonksiyonun çalışması bir dakikadan daha kısa sürer.

---

