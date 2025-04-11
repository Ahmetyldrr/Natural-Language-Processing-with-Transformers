# Transformer Faktörü ve Seyrek Doğrusal Gösterim

Bir transformer faktörü, bağlamsallaştırılmış kelimeleri içeren bir gömme vektörüdür. Bağlamdan yoksun bir kelimenin birçok anlamı olabilir, bu da çokanlamlılık sorununa yol açar. Örneğin, "separate" kelimesi bir fiil veya sıfat olabilir. Ayrıca, "separate" kelimesi ayırmak, ayırt etmek, dağıtmak ve diğer birçok anlamı ifade edebilir. Yun ve arkadaşları (2021) bu nedenle bağlamsallaştırılmış kelimeler içeren bir gömme vektörü oluşturdular. Bir kelime gömme vektörü, kelime faktörlerinin seyrek doğrusal gösterimleri ile oluşturulabilir.

Örneğin, bir veri kümesindeki cümlelerin bağlamına bağlı olarak, "separate" şu şekilde temsil edilebilir:
```python
separate = 0.3 * "ayır" + 0.3 * "farklı" + 0.1 * "ayırt et" + 0.1 * "ayır" + 0.1 * "dağıt" + 0.1 * "saç"
```
Doğrusal gösterimin seyrek kalmasını sağlamak için, sıfır faktörleri eklemiyoruz, bu da sıfır değerli büyük matrisler oluşturur. Böylece, aşağıdaki gibi işe yaramaz bilgileri dahil etmiyoruz:
```python
separate = 0.0 * "bir araya getirme" + 0.0 * "aynı"
```
Buradaki amaç, faktörlerin katsayılarını sıfırdan büyük olmaya zorlayarak gösterimi seyrek tutmaktır. Her kelimenin gizli durumu her katman için alınır. Her katman, cümlelerin veri kümesinde kelimenin temsilini anlamada ilerledikçe, gizli bağımlılıklar oluşur.

Bu seyrek doğrusal transformer faktörlerinin süperpozisyonu, aşağıdaki gibi özetlenebilecek bir sözlük matrisi haline gelir:
```
X = ϕ * α
```
Burada:
- `ϕ` sözlük matrisidir
- `α` tahmini seyrek katsayılar vektörüdür

Yun ve arkadaşları (2021) algoritmayı daha derin temsiller aramaya zorlamak için Gauss gürültü örnekleri eklediler. Ayrıca, gösterimin seyrek kalmasını sağlamak için denklem aşağıdaki gibi yazılmalıdır:
```
X ≈ ϕ * α
```
Yazarlar, `X`'i katmanların gizli durumları kümesi olarak, `x`'i ise `X`'e ait transformer faktörlerinin seyrek doğrusal süperpozisyonu olarak adlandırırlar. Seyrek sözlük öğrenme modelilerini güzel bir şekilde aşağıdaki gibi özetlerler:
```
X = ϕ * α, burada ϕ = [:,c]
```
Sözlük matrisinde, `:,c` bir sütunu ifade eder ve bir transformer faktörü içerir. `:,c` üç seviyeye ayrılır:
- Düşük seviyeli transformer faktörleri, kelime düzeyinde belirsizliği çözerek çokanlamlılık sorunlarını çözer.
- Orta seviyeli transformer faktörleri, düşük seviyeye hayati bağlam getiren cümle düzeyindeki desenleri ortaya koyar.
- Yüksek seviyeli transformer desenleri, uzun menzilli bağımlılıkları anlamaya yardımcı olur.

Yöntem yenilikçi, heyecan verici ve verimlidir. Ancak, şu anda görselleştirme işlevi yoktur. Bu nedenle, Yun ve arkadaşları (2021) LIME adlı standart bir yorumlanabilir AI yöntemi için gerekli bilgileri oluşturdu. Etkileşimli transformer görselleştirme sayfası, çıktılarını LIME'e dayandırır.

Aşağıdaki bölüm, LIME'e kısa bir giriş niteliğindedir.

---

