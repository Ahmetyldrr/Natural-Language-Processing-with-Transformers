# Google Cloud Vision ve ChatGPT'nin Entegrasyonu

Google Cloud Vision bölümünün çok zor bir görüntü için ürettiği ilginç bir çıktı oldu. Ancak, model sadece bir olasılık listesi görüntüledi. Bu, insanların düşünme şekli değil. İnsanlar, özellikleri ve olasılıkları yorumlamak için anlamsal yeteneklere sahiptir. İnsanlar, Google Cloud Vision tarafından çok zor bir görüntü için üretilen ve güven seviyesi 0.8'in üzerinde olan özellikleri izole edebilir ve bunları kümelere ayırabilir: 
Hava = {Bulut, Atmosfer, Gökyüzü, Su, Sis, Atmosferik olay}
Taşıt = {Taşıt, Otomotiv aydınlatması}
Yol = {Yol yüzeyi}
Diğer = {Elektrik}

Bir insan, anlamsal ve muhakeme yeteneklerimizi kullanarak, 0.8'den yüksek bir olasılığı aşan özellikleri analiz ederken mantıksal bir sonuç zinciri oluşturabilir: 
Bulutlu, sisli havalarda yolda bir araba var.

ChatGPT, muhakeme yapmak üzere eğitilmiştir. Google Cloud Vision'un çıktısını ChatGPT, GPT-4'e bağlayalım ve ne olacağını görelim:

## DR 1. Bir görüntünün etiketlerini (açıklamalarını) ve puanlarını analiz edin.
## 2. Taşıtlar ve yollarla ilgili olan ve 0.8'den yüksek puana sahip tüm etiketleri çıkarın.
## 3. Görüntüde bir araba olup olmadığını belirleyin.

İşte etiketler ve puanlar:
| Açıklama | Puan |
| --- | --- |
| 0 Bulut | 0.957413 |
| 1 Atmosfer | 0.948181 |
| 2 Gökyüzü | 0.945039 |
| 3 Su | 0.938452 |
| 4 Sis | 0.850576 |
| 5 Taşıt | 0.848766 |
| 6 Gri | 0.841551 |
| 7 Otomotiv aydınlatması | 0.831509 |
| 8 Atmosferik olay | 0.830896 |
| 9 Elektrik | 0.829284 |
| 10 Yol yüzeyi | 0.814302 |
| 11 Peyzaj | 0.764860 |
| 12 Alacakaranlık | 0.758024 |
| 13 Parkur | 0.752574 |
| 14 Ufuk | 0.746588 |
| 15 Asfalt | 0.744103 |
| 16 Pus | 0.730276 |
| 17 Yol | 0.724686 |
| 18 Sis | 0.716356 |
| 19 Gece yarısı | 0.716127 |
| 20 Havai güç hattı | 0.684156 |
| 21 Karanlık | 0.682619 |
| 22 Ağaç | 0.677585 |
| 23 Kamu hizmeti | 0.661300 |
| 24 Bina olmayan yapı | 0.642936 |
| 25 Akşam | 0.640874 |
| 26 Şafak | 0.637772 |
| 27 Simetri | 0.615672 |
| 28 Doğal peyzaj | 0.612960 |
| 29 Okyanus | 0.603301 |
| 30 Otoyol | 0.602228 |
| 31 Karayolu | 0.601216 |
| 32 Şerit | 0.587314 |
| 33 Gece | 0.576490 |
| 34 Monokrom | 0.556066 |
| 35 Lens parlaması | 0.555109 |
| 36 Yolculuk | 0.527954 |
| 37 Elektrik kaynağı | 0.505197 |

ChatGPT, GPT-4 ile birlikte güçlü muhakeme yetenekleri gösterir:
İlk olarak, verilen etiketleri ve puanları analiz edelim:
Listeden, taşıtlar ve yollarla ilgili olabilecek etiketler şunlardır:
Taşıt
Otomotiv aydınlatması
Yol yüzeyi
Parkur
Asfalt
Yol
Otoyol
Karayolu
Şerit
Yolculuk

0.8'den yüksek puana sahip ve taşıtlar ve yollarla ilgili olan tüm etiketleri çıkarmak ve listelemek için:
Taşıt: 0.848766
Otomotiv aydınlatması: 0.831509
Yol yüzeyi: 0.814302

Görüntüde bir araba olup olmadığını belirlemek için:
"Taşıt" etiketi 0.848766 puanı ile görünmektedir, ancak bunun özellikle bir araba olduğu anlamına gelmez. "Taşıt", arabalar, bisikletler, otobüsler vb. gibi herhangi bir ulaşım modunu temsil edebilir. 
Ancak, "Otomotiv aydınlatması" etiketinin (puan: 0.831509) varlığı, bir arabanın muhtemelen var olduğunu kuvvetle önerir, çünkü otomotiv aydınlatması tipik olarak araçlardaki, özellikle arabalardaki ışııkları ifade eder.

Sonuç olarak:
Taşıtlar ve yollarla ilgili ve 0.8'den yüksek puana sahip etiketler şunlardır:
Taşıt
Otomotiv aydınlatması
Yol yüzeyi

Görüntüde bir araba olma ihtimali yüksektir, özellikle "Otomotiv aydınlatması" etiketinden dolayı. 
Ancak, sadece verilen verilere dayanarak %100 kesinlik ile söyleyemeyiz.

ChatGPT, araştırmamızda büyük bir adım atmıştır. İnsan gibi, bir araba olma ihtimalini düşünmektedir. 
Ancak, henüz problemimizin bağlamını sağlamadık. ChatGPT'ye daha fazla bilgi verelim:
Sizin cevabınıza ve aynı zamanda cevabınızın bir destekli sürüş araba yazılımı olması bağlamına dayanarak, bu durumda sürücüye hangi mesajı gönderirdiniz?

ChatGPT'nin eşsiz, insana yakın muhakeme yetenekleri vardır. 
Problemimizin çözümünü nihayet elde edecek miyiz? ChatGPT'nin cevabını okuyalım:
Destekli bir sürüş araba yazılımında, güvenlik ve netlik önceliklidir. 
Yazılım, bir taşıt, yol koşulları ve otomotiv aydınlatması öneren öğeleri tespit etmiştir. 
Buna dayanarak, sürücüye ihtiyatlı bir mesaj şu olabilir:
"Öndeki taşıt aktif ışıklarla tespit edildi. Güvenli mesafeyi koruyun ve dikkatli sürün."

Bu mesaj, sürücüyü öndeki potansiyel taşıt ve ışıklardan haberdar etmeyi amaçlar ve güvenli bir takip mesafesi korumalarını ve uyanık olmalarını hatırlatır.

Evet! ChatGPT, doğru mesajın sürücüye gönderilmesini önerir: 
"Öndeki taşıt aktif ışıklarla tespit edildi. Güvenli mesafeyi koruyun ve dikkatli sürün."

Çoklu platform ve model zincirleme, kesinlikle F-AGI yolunu açabilir. 
Yaratıcı becerilerimizi geliştirmemiz ve HuggingGPT'nin yaptığı gibi mevcut en iyi modelleri bir araya getirme yollarını bulmamız gerekir. 
İmajdan videoya çoklu platform model zincirleme yaparak eğlenelim.

Python kodları bulunmamaktadır.

---

