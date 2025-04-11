# İngilizce Paragrafın Türkçe Çevirisi

Giriş: URL Listesi 
Çıkış: Sağlanan tüm URL'lerden birleştirilmiş metin

## Kod Açıklaması

Aşağıdaki python kodunu kullanarak, verilen URL listesindeki tüm metinleri birleştirebiliriz.

```python
import requests
from bs4 import BeautifulSoup

def concatenate_text_from_urls(url_list):
    concatenated_text = ""
    for url in url_list:
        try:
            # URL'ye GET isteği gönder
            response = requests.get(url)
            
            # İstek başarılı olduysa (200 durum kodu) içeriği işle
            if response.status_code == 200:
                # HTML içeriğini ayrıştır
                soup = BeautifulSoup(response.text, 'html.parser')
                
                # Sayfadaki tüm metni çıkar
                text = soup.get_text()
                
                # Çıkarılan metni birleştir
                concatenated_text += text + "\n\n"
            else:
                print(f"{url} için istek başarısız oldu. Durum kodu: {response.status_code}")
        except Exception as e:
            print(f"{url} için hata oluştu: {str(e)}")
    
    return concatenated_text

# Kullanım örneği
url_list = ["http://example.com", "http://example.org"]
print(concatenate_text_from_urls(url_list))
```

### Kodun Satır Satır Açıklaması

1. `import requests`: `requests` kütüphanesini içe aktarır. Bu kütüphane, HTTP istekleri göndermek için kullanılır.
2. `from bs4 import BeautifulSoup`: `BeautifulSoup` sınıfını `bs4` kütüphanesinden içe aktarır. Bu sınıf, HTML ve XML belgelerini ayrıştırmak için kullanılır.
3. `def concatenate_text_from_urls(url_list):`: `concatenate_text_from_urls` adlı bir fonksiyon tanımlar. Bu fonksiyon, bir URL listesi alır ve listedeki tüm URL'lerden metinleri birleştirir.
4. `concatenated_text = ""`: Birleştirilmiş metni saklamak için boş bir string değişkeni tanımlar.
5. `for url in url_list:`: Verilen URL listesi üzerinde döngü yapar.
6. `try:`: Hata yakalamak için bir `try` bloğu başlatır.
7. `response = requests.get(url)`: Belirtilen URL'ye bir GET isteği gönderir ve yanıtı `response` değişkenine atar.
8. `if response.status_code == 200:`: İsteğin başarılı olup olmadığını (200 durum kodu) kontrol eder.
9. `soup = BeautifulSoup(response.text, 'html.parser')`: Yanıttaki HTML içeriğini `BeautifulSoup` kullanarak ayrıştırır.
10. `text = soup.get_text()`: Ayrıştırılan HTML'den metni çıkarır.
11. `concatenated_text += text + "\n\n"`: Çıkarılan metni birleştirilmiş metne ekler ve iki satır boşluk bırakır.
12. `except Exception as e:`: Herhangi bir hata oluşursa yakalar ve hata mesajını yazdırır.
13. `return concatenated_text`: Birleştirilmiş metni döndürür.

### Kullanım

- `concatenate_text_from_urls` fonksiyonuna bir URL listesi vererek çağırabilirsiniz.
- Fonksiyon, listedeki tüm URL'leri ziyaret eder, metinleri çıkarır ve birleştirir.
- Birleştirilmiş metni döndürür.

---

