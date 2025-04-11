# LIME (Yerel Yorumlanabilir Model-Agnostik Açıklamalar)

LIME, Yerel Yorumlanabilir Model-Agnostik Açıklamalar anlamına gelir. Bu açıklanabilir AI yönteminin adı kendi adına konuşur. Model-agnostiktir. Böylece, sözlük öğrenimi yoluyla transformatör görselleştirme yöntemi hakkında anında sonuçlar çıkarabiliriz: Bu yöntem, transformatör katmanlarının matrislerine, ağırlıklarına ve matris çarpımlarına girmez. Yöntem, Chapter 2'de yaptığımız gibi bir transformatör modelinin nasıl çalıştığını açıklamaz, Transformatör Modelinin Mimarisine Giriş. Bu bölümde, yöntem, transformatör faktörlerinin seyrek doğrusal süperpozisyonları tarafından sağlanan matematiksel çıktılara bakar. LIME, bir veri kümesindeki tüm bilgilerin ayrıştırılmasına çalışmaz. Bunun yerine, bir tahmin etrafındaki özellikleri inceleyerek modelin yerel olarak güvenilir olup olmadığını belirler. LIME, modele global olarak uygulanmaz. Bunun yerine, bir tahminin yerel ortamına odaklanır. Bu, LIME'ın bir kelimenin bağlamını keşfetmesi ve modelin çıktısı hakkında paha biçilmez bilgiler sağlaması nedeniyle Doğal Dil İşleme (NLP) ile uğraşırken özellikle etkilidir.

# Görselleştirme Yöntemi

Sözlük öğrenimi yoluyla görselleştirmede, bir örnek `x` şu şekilde temsil edilebilir:
```python
# Burada python kodu yok, ancak bir örnek gösterimi var
# x = [bir dizi özellik]
```
Bu örneğin yorumlanabilir temsili bir ikili vektördür:
```python
# Yorumlanabilir temsil
# x_interpretable = [0, 1, 0, 1]  # ikili vektor
```
Amaç, bir özelliğin veya birkaç özelliğin yerel varlığını veya yokluğunu belirlemektir. NLP'de, özellikler kelimelere yeniden yapılandırılabilen tokenlerdir.

# LIME'ın Çalışma Prensibi

LIME için `g`, bir transformatör modelini veya başka bir makine öğrenimi modelini temsil eder. `G`, `g` içeren bir dizi transformatör modelini temsil eder:
```python
# G = {g1, g2, g3, ...}  # transformatör modelleri kümesi
# g ∈ G  # g, G kümesinin bir elemanı
```
LIME'ın algoritması böylece herhangi bir transformatör modeline uygulanabilir.

# LIME'ın Özellikleri

Bu noktada, şunları biliyoruz:
- LIME, bir kelimeye hedefler ve diğer kelimeler için yerel bağlamı arar.
- LIME, böylece o kelimenin neden tahmin edildiğini ve başka bir kelimenin neden tahmin edilmediğini açıklamak için bir kelimenin yerel bağlamını sağlar.

LIME hakkında daha fazla bilgi için Referanslar bölümüne bakınız.

# Görselleştirme Arayüzünün Keşfi

Şimdi, görselleştirme arayüzünü keşfedelim.

---

