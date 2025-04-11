# Transformatör Modellerinin Temeli

Transformatör modellerinin temel taşı dikkat alt katmanlarında yatmaktadır. Buna karşılık, dikkat alt katmanlarının ana özelliği, içerik boyutunu işleme yöntemidir. İçerik boyutu, insanların ve makinelerin dil öğrenmesinin ana yollarından biridir. İçerik boyutu ne kadar büyükse, bir diziyi o kadar iyi anlayabiliriz. Ancak, içerik boyutunun dezavantajı, bir kelimenin neye atıfta bulunduğunu anlamak için gereken mesafedir. Uzun vadeli bağımlılıkları analiz etmek için alınan yol, tekrarlayan katmanlardan dikkat katmanlarına geçmeyi gerektirir.

Aşağıdaki cümle, "it" zamirinin neye atıfta bulunduğunu bulmak için uzun bir yol gerektirir: "Evimiz bir kanepe, büyük bir masa ve böyle küçük bir alanda sahip olmayı istediğimiz diğer mobilyaları sığdırmak için çok küçüktü. Bir süre kalmayı düşündük, ancak sonunda satmaya karar verdik." "It" zamirinin anlamı, ancak cümlenin başındaki "ev" kelimesine geri giderek açıklanabilir. Bu, bir makine için oldukça uzun bir yol!

Vaswani ve diğerleri (2017), orijinal Transformatör modelinde içerik analizinin tasarımını optimize etti. Dikkat, işlemleri bire bir token işlemine indirir. Tüm katmanlar aynıdır, bu da transformatör modellerinin boyutunu büyütmeyi çok daha kolay hale getirir.

Transformatörlerin esnek ve optimize edilmiş mimarisi, diğer birkaç faktöre de etki etti: Vaswani ve diğerleri (2017), 36 milyon cümle ile state-of-the-art bir transformatör modeli eğitti. Brown ve diğerleri (2020), Common Crawl verilerinden çıkarılan 400 milyar byte-pair-encoded token ile bir GPT-3 modeli eğitti.

Büyük transformatör modelleri eğitmek, dünya çapında yalnızca birkaç ekibin erişebileceği makine gücüne ihtiyaç duyar. Brown ve diğerleri (2020), GPT-3 175B'yi eğitmek için toplam 2.14\*10^23 FLOPS harcadı. Transformatörlerin mimarisini tasarlamak, dünya çapında yalnızca birkaç kuruluş tarafından finanse edilebilecek yüksek nitelikli takımlara ihtiyaç duyar. Boyut ve mimari gelişmeye devam edecektir. Süper bilgisayarlar, transformatörleri eğitmek için gerekli kaynakları sağlamaya devam edecektir. Şimdi, sıfır-shot modellerinin nasıl elde edildiğini göreceğiz.

Python kodları bulunmamaktadır, ancak FLOPS hesaplaması aşağıdaki gibi açıklanabilir:

*   FLOPS (Floating Point Operations Per Second), bir bilgisayarın saniyede gerçekleştirebileceği kayan noktalı işlem sayısını ölçen bir birimdir.
*   2.14\*10^23 FLOPS, GPT-3 175B modelinin eğitimi sırasında gerçekleştirilen toplam kayan noktalı işlem sayısını temsil eder.

Bu değerin hesaplanması genellikle aşağıdaki gibi yapılır:

```python
# FLOPS hesaplaması
flops = 2.14 * (10 ** 23)
print(flops)
```

Bu kod, 2.14\*10^23 sayısını hesaplar ve sonucu `flops` değişkenine atar.

---

