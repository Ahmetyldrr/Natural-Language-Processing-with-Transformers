# İngilizce Paragrafın Türkçe Çevirisi

Şimdi rutinimize yerleşmiş bulunuyoruz ve bir yarış arabasını pilotluk etmenin rahatlığına alışıyoruz! 
Talimatları hızlı bir şekilde sağlıyor ve talimatları alıyoruz: 
Denis Rothman: Tamam. Google Colab'da Python'da başka bir program oluşturmak istiyorum. 
Bu sefer IMDB'den film eleştirilerini görüntüleyen ve Google Colab not defterinde görüntüleyen bir program yazmak istiyorum. 
Bunu nasıl yaparım? 
GPT-4: Python kullanarak bir Google Colab not defterinde IMDb'den film eleştirilerini görüntülemek için, HTML'i getirmek üzere requests kütüphanesini kullanabilirsiniz... 
Not defterinde GPT-4'ün talimatlarının geri kalanını okuyun ve kodu çalıştırın. 
İlk önce web sayfalarını kazımak için beautifulsoup4'ü kurarız: 
```bash
pip install beautifulsoup4 lxml
```
Daha sonra GPT-4 tarafından sağlanan kodu çalıştırırız:

```python
import requests 
from bs4 import BeautifulSoup 
from IPython.display import display, Markdown 

# IMDb'den film eleştirilerini görüntüleme fonksiyonu
def display_imdb_reviews(movie_id, num_reviews=5):
    # IMDb film eleştirileri sayfasının URL'sini oluştur
    url = f"https://www.imdb.com/title/{movie_id}/reviews"
    
    # URL'ye GET isteği gönder
    response = requests.get(url)
    
    # İstek başarılı değilse hata mesajı yazdır
    if response.status_code != 200:
        print("IMDb eleştirilerini getirilemedi")
        return
    
    # HTML içeriğini BeautifulSoup ile ayrıştır
    soup = BeautifulSoup(response.text, "lxml")
    
    # Eleştirileri içeren div etiketlerini bul
    reviews = soup.find_all("div", class_="imdb-user-review")
    
    # İlk num_reviews adet eleştiriyi işle
    for idx, review in enumerate(reviews[:num_reviews]):
        # Eleştiri başlığını, yazarını, tarihini ve içeriğini çıkar
        title = review.find("a", class_="title").text.strip()
        author = review.find("span", class_="display-name-link").text.strip()
        date = review.find("span", class_="review-date").text.strip()
        content = review.find("div", class_="text").text.strip()
        
        # Eleştiriyi Markdown formatında görüntüle
        display(Markdown(f"**İnceleme {idx + 1}: {title}**"))
        display(Markdown(f"_by {author} on {date}_"))
        display(Markdown(f"{content}\n\n---"))

# İstenen film için IMDb ID'sini movie_id değişkenine atayın
movie_id = "tt1375666"  # Inception (2010)
display_imdb_reviews(movie_id)
```

### Kod Açıklaması

1. `import requests`: HTTP istekleri göndermek için requests kütüphanesini içe aktarır.
2. `from bs4 import BeautifulSoup`: HTML ve XML dokümanlarını ayrıştırmak için BeautifulSoup'u içe aktarır.
3. `from IPython.display import display, Markdown`: Jupyter Notebook'larda Markdown formatında metin görüntülemek için display ve Markdown'u içe aktarır.
4. `def display_imdb_reviews(movie_id, num_reviews=5)`: IMDb'den film eleştirilerini görüntülemek için bir fonksiyon tanımlar. 
   - `movie_id`: IMDb'de filmin ID'si.
   - `num_reviews`: Görüntülenmek üzere eleştiri sayısı (varsayılan 5).
5. `url = f"https://www.imdb.com/title/{movie_id}/reviews"`: IMDb film eleştirileri sayfasının URL'sini oluşturur.
6. `response = requests.get(url)`: URL'ye bir GET isteği gönderir.
7. `if response.status_code != 200`: İstek başarılı değilse (HTTP durum kodu 200 değilse), hata mesajı yazdırır ve fonksiyondan çıkar.
8. `soup = BeautifulSoup(response.text, "lxml")`: HTML içeriğini BeautifulSoup ile ayrıştırır.
9. `reviews = soup.find_all("div", class_="imdb-user-review")`: Eleştirileri içeren div etiketlerini bulur.
10. `for idx, review in enumerate(reviews[:num_reviews])`: İlk `num_reviews` adet eleştiriyi işler.
11. Eleştiri başlığı, yazarı, tarihi ve içeriği için ilgili HTML etiketlerini bulur ve metinlerini çıkarır.
12. `display(Markdown(f"**İnceleme {idx + 1}: {title}**"))`: Eleştiriyi Markdown formatında görüntüler.

### Çıktı

İstenen film için IMDb'den çekilen eleştiriler, Markdown formatında görüntülenir. Örneğin:
**İnceleme 1: A one-of-a-kind mind-blowing masterpiece!**
_by adrien_ngoc_1701 on 1 March 2019_
My 3rd time watching this movie! Yet, it still stunned my mind,…

---

