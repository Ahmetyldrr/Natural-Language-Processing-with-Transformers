# Hugging Face Transformer Model ile Makine Çevirisi

Bu bölümde öğrendiklerimizi hazır kullanıma hazır Hugging Face transformer modeline yoğunlaştırabiliriz. Hugging Face ile makine çevirisini üç satır kod ile uygulayabiliriz! Google Colaboratory'de Multi_Head_Attention_Sub_Layer.ipynb dosyasını açın. Notebook'u Google Drive'ınıza kaydedin (Gmail hesabınızın olduğundan emin olun). Sonra, son iki hücreye gidin. Öncelikle Hugging Face transformerlarının yüklendiğinden emin oluyoruz: 

```python
!pip -q install transformers
```

İlk hücre, çeşitli transformer kullanımlarını içeren Hugging Face pipeline'ı içe aktarır:
```python
#@title Retrieve pipeline of modules and choose English to French translation
from transformers import pipeline
```

Daha sonra, hazır kullanıma sahip fonksiyonları içeren Hugging Face pipeline'ını uyguluyoruz. Bizim durumumuzda, bu bölümün Transformer modelini göstermek için, çeviri modelini etkinleştiriyoruz ve İngilizce'den Fransızca'ya çevirmek için bir cümle giriyoruz:
```python
translator = pipeline("translation_en_to_fr")  # Tek satır kod!
print(translator("It is easy to translate languages with transformers", max_length=40))
```

Ve voilà! Çeviri görüntülenir: `[{'translation_text': 'Il est facile de traduire des langues à l'aide de transformateurs.'}]`

Hugging Face, transformer mimarilerinin hazır kullanıma sahip modellerde nasıl kullanılabileceğini gösterir.

**Kod Açıklaması:**

1. `!pip -q install transformers`: Bu satır, Hugging Face transformer kütüphanesini yükler. `!pip` komutu, Google Colaboratory'de Python paketlerini yüklemek için kullanılır. `-q` parametresi, yükleme işleminin sessizce yapılmasını sağlar.

2. `from transformers import pipeline`: Bu satır, Hugging Face kütüphanesinden `pipeline` fonksiyonunu içe aktarır. `pipeline` fonksiyonu, çeşitli doğal dil işleme görevleri için hazır kullanıma sahip modeller sağlar.

3. `translator = pipeline("translation_en_to_fr")`: Bu satır, İngilizce'den Fransızca'ya çeviri yapmak için bir `pipeline` nesnesi oluşturur.

4. `print(translator("It is easy to translate languages with transformers", max_length=40))`: Bu satır, oluşturulan `translator` nesnesini kullanarak bir cümleyi İngilizce'den Fransızca'ya çevirir. `max_length` parametresi, çeviri sonucunun maksimum uzunluğunu belirler. Çeviri sonucu, bir liste içinde bir sözlük olarak döndürülür.

---

