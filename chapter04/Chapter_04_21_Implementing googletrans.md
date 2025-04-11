# Google Translate AJAX API Wrapper'ı Çalıştırma

Bölümün ikinci kısmı, Trax_Google_Translate.ipynb, googletrans'i yükleyerek başlar: 
```python
!pip install googletrans==4.0.0-rc1 -q
```
Daha fazla bilgi için https://pypi.org/project/googletrans/ adresine gidin. 
Artık bir çeviri nesnesi oluşturabilir ve kütüphanenin metotlarını çağırabiliriz.

## Translator Sınıfının Bir Örneğini Oluşturma
Translator sınıfının bir örneğini oluşturmak bir satır kod alır:
```python
from googletrans import Translator
translator = Translator()
```
Çeviri nesnesi artık oluşturuldu ve Translator sınıfının metotlarını çağırabiliriz.

## İngilizceden Fransızcaya Metin Çevirme
Aşağıdaki hücre, translate metodunu çağırır:
```python
import googletrans
translator = googletrans.Translator()
# "Google Trax can translate to French" metninin çevirisini al
translation = translator.translate("Google Trax can translate to French", src="en", dest="fr")
# Çeviriyi yazdır
print(translation.text)
```
Çıktı doğru çeviridir: Google Trax peut se traduire en français

## Bir Metnin Dilini Algılama
Ayrıca detect metodu ile bir dili algılayabiliriz:
```python
lang = translator.detect('이 문장은 한글로 쓰여졌습니다.')
print(lang)
```
Metod, giriş dizisinin dilini görüntüler: Detected(lang=ko, confidence=None)
Bu durumda algılanan dil Korece. Güven seviyesi her zaman görüntülenmez.

## Çoklu Dillere Çevirme
Translate metodunu birkaç dil için çağırabiliriz:
```python
from googletrans import Translator
translator = Translator()
languages = ['en', 'es', 'fr']
for language in languages:
    print(translator.translate('안녕하세요', dest=language).text)
```
Çıktı, Korece "merhaba" için İngilizce, İspanyolca ve Fransızca çevirileri sağlar:
hello
Hola
Bonjour

Daha fazla özellik için: https://py-googletrans.readthedocs.io/en/latest/. 
Google Translate'i keşfettik. Şimdi, son kullanıcı olarak Generative AI ile çeviriler yapacağız.

---

