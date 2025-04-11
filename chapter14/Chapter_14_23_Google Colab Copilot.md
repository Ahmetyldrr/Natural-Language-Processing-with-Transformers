# Google Colab Copilot Hakkında

Google Colab Copilot, 7. Bölüm'de, GitHub Copilot kod asistanı bölümünde kullandığımız GitHub Copilot'a benzer. Google Colab Copilot, Google Colab'a entegre edilmiştir: https://blog.google/technology/developers/google-colab-ai-coding-features/. Bu normal bir evrimdir. Akıllı telefonlar ve bilgisayarlar, tüm GPT'ler gibi aynı temel işlevlere sahiptir. Colab Generative AI gibi yapay zeka destekli copilotlar da istisna değildir. Google Colab'ı çalıştırmak için bir Google hesabına ihtiyacınız olacak. Google Colab'a gidin, bir not defteri oluşturun ve copilot'u ilk kez kullandığınızda bir pencere açılacaktır: 

## Şekil 14.6: Colab'da Generative AI Hizmet Şartları

Her zaman olduğu gibi, arada sırada ürettiği yanlışlıklar nedeniyle Generative AI için bir sorumluluk reddi beyanı göreceksiniz. Yapay zeka copilot'u çalıştırmayı seçerseniz, bir istem metin kutusu görünecektir: 

## Şekil 14.7: Yapay Zeka Copilot İstem Kutusy

İlk olarak, aşağıdaki gibi bir istem girin: 10'a kadar Fibonacci fonksiyonu oluştur 
Kod, istemle otomatik olarak oluşturulur:
```python
# istem: 10'a kadar Fibonacci fonksiyonu oluştur
def fibonacci(n):
    if n == 0:
        return 0
    if n == 1:
        return 1
    return fibonacci(n-1) + fibonacci(n-2)
print(fibonacci(10))
```
Çıktı 55'tir, bu doğru. Şimdi, kodun hata ürettiği bir örneği simüle edelim, örneğin `n == 0` yerine `n = 0`:
## Şekil 14.8: Hata Açıklama Özelliği

Daha zor hatalar için bir açıklama ve kod elde etmek için HATA AÇIKLA düğmesine tıklayabiliriz. Hücrelerde bir tamamlama işlevi de vardır:
## Şekil 14.9: Colab'da Yapay Zeka ile Üretme Seçeneği

Klasik yazılım editörlerinde olduğu gibi, kodlamaya başlayarak tamamlama önerileri alabilirsiniz, ancak bu sefer birkaç satır kod üretecektir! İstediğinizde oluştur'a da tıklayabilirsiniz ve oluşturma metin kutusu istemi görünecektir. Bu işlevi kullanmak, geliştirme çabasını azaltacak ve yaratıcılığınızı sınırlarına kadar zorlayacaktır! Ortama alıştığınızda, gezegendeki en hızlı arabalarla Indy 500 sürücüsü gibi kod yazabileceksiniz! Şimdi, Vertex AI PaLM 2'yi çalıştırmaya başlamak için Google Cloud'un Yapay Zeka platformuna geçeceğiz. 

Python kodları için satır satır açıklama:
```python
# istem: 10'a kadar Fibonacci fonksiyonu oluştur
def fibonacci(n):  # n parametre olarak alan fibonacci adında bir fonksiyon tanımlar
    if n == 0:  # eğer n 0'a eşitse
        return 0  # 0 döndürür
    if n == 1:  # eğer n 1'e eşitse
        return 1  # 1 döndürür
    return fibonacci(n-1) + fibonacci(n-2)  # fibonacci(n-1) ve fibonacci(n-2) değerlerinin toplamını döndürür (özyinelemeli çağrı)
print(fibonacci(10))  # fibonacci fonksiyonunu 10 parametresi ile çağırır ve sonucu yazdırır
```

---

