# Kodun Belge Erişim Bölümü

Kodun belge erişim bölümü, iki işlev içerir: URL erişimi ve kullanıcı isteğine göre URL işleme. İlk işlev, kullanıcı isteğine göre bir URL erişim işlevidir: `def select_urls_based_on_query(user_query):`

## Kullanıcı İsteğine Göre URL Seçimi

URL'ler, kullanıcının isteğinde geçen bir anahtar kelime kullanılarak seçilir. Başka herhangi bir yöntem de uygulanabilir. Aşağıdaki kod, kullanıcının isteğinde tespit edilen anahtar kelimelere göre bir bilgi tabanında URL'leri seçer:

```python
def select_urls_based_on_query(user_query):
    # 'climate' ile ilgili URL'ler
    climate_urls = [
        "https://en.wikipedia.org/wiki/Climate_change",  # Gerçek URL'lerle değiştirin
        "https://en.wikipedia.org/wiki/Effects_of_climate_change"
    ]
    # 'RAG' ile ilgili URL'ler
    rag_urls = [
        "https://en.wikipedia.org/wiki/Large_language_model",  # Gerçek URL'lerle değiştirin
        "https://huggingface.co/blog/ray-rag"
    ]
    # Kullanıcı sorgusunda 'climate' varsa
    if "climate" in user_query.lower():
        return climate_urls
    # Kullanıcı sorgusunda 'RAG' varsa
    elif "RAG" in user_query:
        return rag_urls
    # Anahtar kelime eşleşmezse varsayılan dönüş
    return []
```

İstediğiniz başka bir yöntemi kullanabilirsiniz, örneğin veritabanı sorguları ve listeleri. Otomasyonun herhangi bir biçimini de uygulayabilirsiniz. Hatırlanması gereken ana kavram, aramanın kullanıcının isteğine dayalı olması ve buna uyum sağlamasıdır.

## Belge İşleme ve Özetleme

İkinci işlev, belgeleri kazır ve özetler. İlk olarak, bir özetleyici tanımlanır:

```python
def fetch_and_summarize(user_query):
    urls = select_urls_based_on_query(user_query)
    summarizer = pipeline("summarization", model="sshleifer/distilbart-cnn-12-6")
```

Alınan içerik işlenir:

```python
summaries = []
for url in urls:
    page = requests.get(url)
    soup = BeautifulSoup(page.content, 'html.parser')
    # Ana makale metnini daha doğru bir şekilde çıkarmaya çalışın
    # Bu genel bir örnektir ve belirli web siteleri için ayarlanması gerekebilir
    article = soup.find('article')
    if article:
        article_text = article.get_text()
    else:
        paragraphs = soup.find_all('p')
        article_text = ' '.join([para.get_text() for para in paragraphs])
    # Model için çok uzun ise kısaltın
    if len(article_text) > 1024:
        article_text = article_text[:1024]
```

Özetleyici daha sonra alınan içeriği özetlemek için etkinleştirilir:

```python
summary = summarizer(article_text, max_length=130, min_length=30, do_sample=False)[0]['summary_text']
summaries.append(summary)
```

Son olarak, özet GPT-4 işlevine döndürülür:

```python
return summaries
```

Artık bir kullanıcının isteğine göre veri almanın birçok yolundan birini gördük. Şimdi, bilgiyi bir GPT-4 girdisine nasıl entegre edeceğimize bakalım.

# Python Kodlarının Açıklaması

1. `def select_urls_based_on_query(user_query):` 
   - Kullanıcı isteğine göre URL'leri seçen işlevi tanımlar.

2. `climate_urls` ve `rag_urls` listeleri:
   - Belirli anahtar kelimelere göre önceden tanımlanmış URL'leri içerir.

3. `if "climate" in user_query.lower():` ve `elif "RAG" in user_query:` 
   - Kullanıcı sorgusundaki anahtar kelimeleri kontrol eder ve ilgili URL listesini döndürür.

4. `def fetch_and_summarize(user_query):`
   - Kullanıcı isteğine göre URL'leri seçen ve bu URL'lerdeki içeriği özetleyen işlevi tanımlar.

5. `summarizer = pipeline("summarization", model="sshleifer/distilbart-cnn-12-6")`
   - Hugging Face Transformers kütüphanesini kullanarak bir özetleme modeli yükler.

6. `page = requests.get(url)` ve `soup = BeautifulSoup(page.content, 'html.parser')`
   - Belirtilen URL'deki sayfayı indirir ve HTML içeriğini ayrıştırır.

7. `article = soup.find('article')` ve `paragraphs = soup.find_all('p')`
   - Sayfadaki ana makale metnini veya paragrafları çıkarmaya çalışır.

8. `summary = summarizer(article_text, max_length=130, min_length=30, do_sample=False)[0]['summary_text']`
   - Çıkarılan metni özetler.

9. `return summaries`
   - Özetlenen metinleri döndürür.

---

