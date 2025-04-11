# Vertex AI Platformunun Sürekli Evrimi

Vertex AI platformu sürekli olarak gelişmektedir. Siz en son teknolojinin sınırında bulunuyorsunuz! Kullandığımız modeller zaman zaman güncellenmektedir. Bu güncellemeler sonuçlarda veya işleyişte küçük farklılıklara neden olabilir. En son sürüm en kararlı sürüm olmayabilir. Gözünüzü dört açmanız ve Google'ın sürüm belgelemesini düzenli olarak kontrol etmeniz gerekecektir: https://cloud.google.com/vertex-ai/docs/generative-ai/learn/model-versioning . Piyasada zirvede olmak için ödenmesi gereken bedel budur! Ancak modellerin gücü PaLM 2'yi keşfetmeye değer kılıyor. Modeller stabil hale geldiğinde, rakiplerinizin çok ilerisinde olacaksınız. O halde, emniyet kemerlerinizi takın ve API'yi çalıştıralım!

## Çok Sayıda Doğal Dil İşleme Görevi

Yüzlerce bilinen Doğal Dil İşleme (NLP) görevi vardır ve her gün yüzlercesi daha ana akım kullanıcılar tarafından icat edilmektedir. Hepsini bir anda uygulayamazsınız. Keşfettiğiniz görevleri derinlemesine anlamaya odaklanın. Daha sonra yeni görevlere uyum sağlayabileceksiniz.

## Google Vertex AI Notebook'unu Açma

GitHub deposunun chapter dizininde bulunan Google_Vertex_AI.ipynb dosyasını açın. Notebook'un ilk bölümü kurulum ve kimlik doğrulama işlemlerini gerçekleştirmektedir.

### Kurulum ve Kimlik Doğrulama

İlk olarak, yanıtları düzgün bir biçimde sarmak için `textwrap` modülünü içe aktarıyoruz:
```python
import textwrap
```
Ardından, Google Cloud AI kütüphanesini yüklüyoruz:
```bash
!pip install google-cloud-aiplatform
```
İstendiğinde çalışma zamanını yeniden başlatın. Ardından, "Runtime" menüsüne gidin ve "Run all" seçeneğini seçin.

### Google Cloud Hesabına Giriş Yapma

Google Cloud'da kaydolmanız, bir proje oluşturmanız ve verilen talimatları izlemeniz gerekecektir: https://console.cloud.google.com/ .

### Basitleştirilmiş Kimlik Doğrulama

Bu notebook, Google Cloud hesabına bağlı basit bir kimlik doğrulama kullanmaktadır:
```python
from google.colab import auth as google_auth
google_auth.authenticate_user()
```
Vertex AI içe aktarılıyor:
```python
import vertexai
```
Her şey hazır!

### İlk İstek: Soru-Cevap Görevi

Bu bölümdeki bölüm başlıkları, notebook'taki bölüm başlıklarıdır. İlk istek bir Soru-Cevap (QA) görevidir.

---

