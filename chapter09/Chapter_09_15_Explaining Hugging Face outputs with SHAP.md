# SHAP'ı Hugging Face Dönüştürücüleri Kullanarak Duygu Analizi Çıktısını Analiz Etme

Hugging Face dönüştürücüleri üzerinde SHAP'ı uygulayarak bir duygu analizi çıktısını analiz edeceğiz. GitHub deposunda bu bölüm için olan klasörde bulunan `Hugging_Face_SHAP.ipynb` dosyasını açın.

## Gerekli Paketlerin Kurulumu

İlk olarak, gerekli paketleri kuracağız:
```python
# Hugging Face Dönüştürücüleri
!pip install transformers
# Dönüştürücü yapı taşları
!pip install xformers
# SHAP
!pip install shap
```
Hugging Face dönüştürücüleri kütüphanesini, dönüştürücü yapı taşları içeren `xformers`ı ve SHAP'ı kurduk.

## Duygu Analizi Uygulaması

Şimdi, Hugging Face dönüştürücüleri için SHAP'ı keşfetmek istediğiniz cümleyi girebilirsiniz:
```python
#@title Cümlenizi buraya girin:
sentence = 'SHAP is a useful explainer'  #@param {type:"string"}
```
Standart bir duygu analizi `distilbert-base-uncased-finetuned-sst-2-english` modeli kullanılarak gerçekleştirilir:
```python
import transformers

# Bir dönüştürücü pipeline modeli yükleyin
model = transformers.pipeline('sentiment-analysis', model='distilbert-base-uncased-finetuned-sst-2-english')

# Giriş cümlesinin duygu analizini yapın
result = model(sentence)[0]
print(result)
```
Çıktı, etiketi ve skoru sağlar:
```json
{'label': 'POSITIVE', 'score': 0.9869391918182373}
```
Skorlar, cümle ve modelin eğitim seviyesine göre değişecektir.

## SHAP Açıklayıcısının Uygulanması

Şimdi, SHAP açıklayıcısını uygulayabilir, değerleri hesaplayabilir ve sonucu çizebiliriz:
```python
import shap

# Giriş cümlesi üzerinde modelin açıklamasını yapın
explainer = shap.Explainer(model)
shap_values = explainer([sentence])

# Tahmin edilen sınıf için ilk tahminin açıklamasını görselleştirin
predicted_class = result['label']
shap.plots.text(shap_values[0, :, predicted_class])
```
Çıktı, duygu analizi sınıfının etiketini ve sınıflandırmaya katkıda bulunan kelimeleri gösterir:
### SHAP Grafiği

Soldaki çubuk (kırmızı) sınıflandırmaya katkıda bulunan kelimeleri gösterir. Sağdaki çubuk (mavi) sınıflandırmayı iten kelimeleri içerir. Sınıflandırmadan bağımsız olarak (pozitif veya negatif), sağdaki kelimeler skoru sınıflandırmaya doğru iter ve soldaki kelimeler skoru geri iter.

## Her Kelimenin Skorunu Görüntüleme

Her kelimenin skorunu görüntüleyebiliriz:
```python
# Duygu skorunu alın
sentiment_score = model(sentence)[0]['score']

# Her kelime için SHAP değerlerini yazdırın
words = sentence.split(' ')
for word, shap_value in zip(words, shap_values.values[0, :, 0]):
    print(f"Kelime: {word}, SHAP değeri: {shap_value}")
```
Her kelimenin bireysel skoru bir etiket (pozitif veya negatif) değildir. Kelimenin nihai çıktıya marjinal matematiksel katkısıdır:
```
Kelime: SHAP, SHAP değeri: 0.0
Kelime: is, SHAP değeri: 0.12446051090955734
Kelime: a, SHAP değeri: 0.17050934582948685
Kelime: useful, SHAP değeri: -0.11854982748627663
Kelime: explainer, SHAP değeri: -0.09484541043639183
```
Kelimenin marjinal katkısının sınıflandırmayı nasıl etkilediğini görmek için kendi cümlelerinizi girerek deneyler yapabilirsiniz.

## Sonuç

Dönüştürücü katmanlarını sözlük öğrenimi yoluyla görselleştirmeye devam edeceğiz.

---

