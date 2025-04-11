# SST-2 Veri Seti ve İkili Sınıflandırma Görevi

SST-2 film eleştirilerini içerir. Bu bölüm, SST-2 (ikili sınıflandırma) görevini açıklayacaktır. Ancak, veri setleri bunun ötesine geçer ve duygu durumunu 0 (negatif) ile n (pozitif) arasında sınıflandırmak mümkündür. Socher ve diğerleri (2013), duygu analizi konusunu ikili pozitif-negatif NLP sınıflandırmasının ötesine taşıdı. Bu bölümde, ikili sınıflandırmayı göstermek için Hugging Face transformer pipeline modelinde SST'den alınan bir örneği çalıştıracağız.

# Kodları Çalıştırma

Open `Transformer_tasks.ipynb` dosyasını açın ve aşağıdaki hücreyi çalıştırın. Bu hücre, SST-2'den alınan pozitif ve negatif film eleştirilerini içerir:
```python
# transformers kütüphanesinden pipeline fonksiyonunu içe aktarın
from transformers import pipeline

# "sentiment-analysis" görevi için bir pipeline oluşturun
# Model olarak "distilbert-base-uncased-finetuned-sst-2-english" kullanılmıştır
nlp = pipeline("sentiment-analysis", model="distilbert-base-uncased-finetuned-sst-2-english")

# İlk cümle için duygu analizi yapın
print(nlp("If you sometimes like to go to the movies to have fun, Wasabi is a good place to start."), 
      "If you sometimes like to go to the movies to have fun, Wasabi is a good place to start.")

# İkinci cümle için duygu analizi yapın
print(nlp("Effective but too-tepid biopic."), "Effective but too-tepid biopic.")
```
# Çıktı

Çıktı doğrudur:
```
[{'label': 'POSITIVE', 'score': 0.9998257756233215}] If you sometimes like to go to the movies to have fun, Wasabi is a good place to start.
[{'label': 'NEGATIVE', 'score': 0.9974064230918884}] Effective but too-tepid biopic.
```
# Değerlendirme

SST-2 görevi doğruluk metriği kullanılarak değerlendirilir. Bir dizinin duygu durumunu sınıflandırıyoruz. Şimdi, bir dizideki iki cümlenin paraphrase olup olmadığını görelim.

---

