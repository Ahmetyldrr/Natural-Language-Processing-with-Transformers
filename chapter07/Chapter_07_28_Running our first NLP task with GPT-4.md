# GPT-4 Kullanmaya Başlamak

GPT-4 kullanmaya birkaç adımda başlayalım. Google Colab'a gidin ve GitHub'daki kitabın bölüm dizininde bulunan Getting_Started_GPT_4_API.ipynb dosyasını açın. Notebook'un donanım ayarlarını değiştirmene gerek yok. Bir API kullanıyoruz, bu nedenle bu bölümdeki görevler için çok fazla yerel işlem gücüye ihtiyacımız olmayacak. Bu bölümün adımları, notebook'taki adımlarla aynıdır. Bir NLP görevi çalıştırmak üç basit adımda yapılır:

Not: Burada Python kodları bulunmamaktadır, sadece bir İngilizce paragrafın Türkçe çevirisi yapılmıştır. Eğer Python kodları içeren bir metin çevirisi istenirse, kodlar satır satır açıklanırdı. 

İstenirse Getting_Started_GPT_4_API.ipynb dosyasının içeriği hakkında bilgi verilebilir, ancak dosyanın içeriği hakkında bilgi verilmediği için varsayalım ki bu dosya GPT-4 API'sini kullanmaya başlamak için gerekli adımları içeren bir Jupyter Notebook dosyasıdır. 

Eğer bir Python kodu olsaydı, örneğin:
```python
# NLP görevi çalıştırmak için gerekli kütüphaneleri import edelim
import nltk
from nltk.tokenize import word_tokenize

# Bir cümleyi tokenize edelim
cumle = "GPT-4 kullanmaya birkaç adımda başlayalım."
tokenler = word_tokenize(cumle)

# Tokenleri yazdıralım
print(tokenler)
```
Yukarıdaki kod için satır satır açıklama şu şekilde olurdu:
1. `# NLP görevi çalıştırmak için gerekli kütüphaneleri import edelim`: Bu satır bir yorum satırıdır ve kodun çalışmasını etkilemez. NLP görevleri için gerekli kütüphaneleri import edeceğimizi belirtir.
2. `import nltk`: NLTK (Natural Language Toolkit) kütüphanesini import eder. NLTK, NLP görevleri için kullanılan popüler bir Python kütüphanesidir.
3. `from nltk.tokenize import word_tokenize`: NLTK kütüphanesinin tokenize modülünden word_tokenize fonksiyonunu import eder. Bu fonksiyon, bir cümleyi kelimelere ayırmaya yarar.
4. `# Bir cümleyi tokenize edelim`: Yorum satırı. Bir cümleyi tokenize edeceğimizi belirtir.
5. `cumle = "GPT-4 kullanmaya birkaç adımda başlayalım."`: Bir cümleyi değişkene atar.
6. `tokenler = word_tokenize(cumle)`: word_tokenize fonksiyonunu kullanarak cümleyi tokenize eder ve tokenleri bir listeye atar.
7. `# Tokenleri yazdıralım`: Yorum satırı. Tokenleri yazdıracağımızı belirtir.
8. `print(tokenler)`: Tokenleri yazdırır.

---

