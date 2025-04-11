# Transformatör Modellerini Yorumlamak

Transformatör modellerini yorumlamak ilerlemiştir, ancak yapılacak çok şey vardır. Bazı engeller oldukça zorlayıcıdır: Gömme alt katmanı, karmaşık pozisyonel kodlamaya eklenen stokastik hesaplamalara dayanır. Çoklu dikkat kafalarının mekanizmalarının stokastik doğası, bir tokenın skorunun birkaç katmandan geçtikten sonra neden ve nasıl üstün geldiğini belirlemeyi zorlaştırır. Ham çıktılara uygulanan Softmax fonksiyonları izleri bulanıklaştırır. Dropout alt katmanları bazı izleri siler. ReLU ve GELU gibi derin öğrenme düzenlileştirmeleri, bir çıktıyı tersine mühendislik yapmayı engeller. Sayılar uyuşukluk vericidir. GPT-3 gibi eski bir modelin 175 milyar parametresi ve 9.216 dikkat kafası (96 katman x 96 kafa) vardır. Ve bunlar sadece bazı zorluklardır! İnsan değerlendirmesi, şeffaflığı artırmaya yardımcı olacak yolları değerlendirmek ve bulmak için önemli bir kaynak olarak kalır. Yapay zekayı açıklamak için artan baskı, yorumlama araçlarını ileriye doğru itiyor.

# Projeler Üzerinde Uygulama

Proje düzeyinde birçok iyi örnek ve kötü sonuç bulacaksınız. Bir transformatörün dil öğrenmede nasıl yol aldığını anlamak için iyi örneklere odaklanın. Transformatörün neden hata yaptığını anlamak için kötü sonuçlarını kullanın. Her durumda, bu sürekli evrimleşen alanın döngüsünde kalın ve dahil olun! Bu bölümde incelenen görsel arayüzler büyüleyicidir. Ancak, hala yapılacak çok iş var. İnsan değerlendirmesi, kontrolü, müdahalesi ve geliştirilmesi uzun bir süre daha gerekli olacaktır.

Python kodları bulunmamaktadır, sadece ingilizce paragrafın türkçeye birebir çevirisi yapılmıştır.

Eğer python kodları olsaydı, satır satır açıklama aşağıdaki gibi yapılırdı:

Örnek python kodu:
```python
def softmax(x):
    return x / np.sum(x)
```
Açıklama:
* `def softmax(x):` : `softmax` adında bir fonksiyon tanımlanır. Bu fonksiyon, girdi olarak `x` alır.
* `return x / np.sum(x)` : Fonksiyon, `x` değerini `np.sum(x)` ile böler ve sonucu döndürür. `np.sum(x)` ifadesi, `x` dizisinin elemanlarının toplamını hesaplar.

Ancak bu metinde python kodları bulunmamaktadır.

---

