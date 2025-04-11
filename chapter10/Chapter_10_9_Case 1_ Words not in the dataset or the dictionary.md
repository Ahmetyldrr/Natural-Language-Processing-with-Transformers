# Eksik Bir Kelimenin Sonuçları

Eksik bir kelime birçok şekilde sorun anlamına gelir. Bu durumda, benzerlik fonksiyonuna "corporations" ve "rights" kelimelerini gönderiyoruz: 
```python
word1 = "corporations"
word2 = "rights"
print("Similarity", similarity(word1, word2), word1, word2)
```
Sözlük "corporations" kelimesini içermiyor:
 Kelimenin kendisi sözlükte yok.

Similarity 0 corporations rights 
Çıkmaz! Kelime bilinmeyen bir [unk] tokenidir. 
Eğer kelime önemliyse, eksik kelime bir dizi olay ve soruna neden olacak ve transformer modelinin çıktısını bozacaktır. 
Eksik kelimeye unk diyeceğiz.

## Eksik Kelimenin İncelenmesi

Birkaç olasılık kontrol edilmelidir ve sorulara cevap verilmelidir:
- unk veri setinde vardı ancak tokenize edilmiş sözlükte yer almadı.
- unk "corporations" kelimesinde olduğu gibi veri setinde yoktu. 
Bu, bu durumda sözlükte neden yer almadığını açıklar.
- unk üretime girdiğinde, eğer kullanıcı tokeni içeren bir girdi gönderirse ve tokenize edilmezse, unk görünecektir.
- unk veri seti için önemli bir kelime değildi ancak transformer kullanımı için önemliydi.

## Eksik Kelimenin Sonuçları

Eğer transformer bazı durumlarda kötü sonuçlar üretirse, sorunların listesi büyümeye devam edecektir. 
Bir transformer modelinin belirli bir downstream görevi için eğitim aşamasında 0.8 gibi bir performans göstermesini mükemmel olarak kabul edebiliriz. 
Ama gerçek hayatta, %20 hata oranıyla çalışmak isteyen var mı: 
- Doktor mu? 
- Avukat mı? 
- Nükleer santral bakım ekibi mi?

0.8 gibi bir performans, birçok mesajın düzgün dil yapısına sahip olmadığı sosyal medya gibi bulanık bir ortamda tatmin edicidir.

## Byte-Level Byte-Pair Encoding (BPE) ile Çözüm

Şimdi en kötü kısmı geliyor. 
Diyelim ki bir NLP ekibi bu sorunu byte-level BPE ile çözmeye çalıştı, bu kitapta da yaptığımız gibi. 
Gerekirse, birkaç dakika ayırın ve 6. Bölüm: RoBERTa ile Transformer'ı Scratch'ten Eğitme, 3. Adım: Tokenizer Eğitme kısmına dönün.

Eğer bir ekip sadece byte-level BPE kullanırsa, kabus başlar:
- unk kelimesi alt kelimelere bölünecektir. 
Örneğin, "corporations" kelimesi "corp + o + ra + tion + s" haline gelebilir.
- Bu tokenlerden bir veya birkaçı veri setinde bulunma olasılığı yüksektir.
- unk, veri setinde bulunan ancak orijinal tokenin anlamını taşımayan tokenler tarafından temsil edilen bir alt kelimeler kümesi haline gelecektir.

Transformer iyi eğitim alacak ve kimse unk'nin parçalara bölündüğünü ve anlamsızca eğitildiğini fark etmeyecektir.
Transformer mükemmel sonuçlar üretebilir ve performansını 0.8'den 0.9'a çıkarabilir.
Herkes alkışlayacaktır, ta ki profesyonel bir kullanıcı kritik bir durumda hatalı bir sonuç uygulayana kadar.

Örneğin, İngilizce'de "corp" corporation veya corporal anlamına gelebilir. 
Bu, "corp" ile diğer kelimeler arasında karışıklık ve kötü çağrışımlar yaratabilir.

## Gerçek Hayatta Transformer Kullanımı

Sosyal medyanın standartları önemsiz konular için transformer kullanmak için yeterli olabilir. 
Ama gerçek hayattaki kurumsal projelerde, veri setleriyle eşleşen bir önceden eğitilmiş tokenizer üretmek çok çalışma gerektirecektir.

Gerçek hayatta, veri setleri her gün kullanıcı girdileriyle büyür.
Kullanıcı girdileri, düzenli olarak eğitilmesi ve güncellenmesi gereken modellerin veri setlerinin bir parçası haline gelir.

Örneğin, kalite kontrolü sağlamak için aşağıdaki üç adım izlenebilir:
1. Byte-level BPE algoritması ile bir tokenizer eğitimi.
2. Bu bölümün "Token-ID eşlemelerinin kalitesini analiz etme ve kontrol etme" kısmında oluşturacağımız gibi bir programla sonuçları kontrol edin.
3. Sadece kalite kontrolü için kullanılacak bir Word2Vec algoritması ile bir tokenizer eğitimi, ardından veri setini ayrıştırın, unk tokenlerini bulun ve veritabanında saklayın. Kritik kelimelerin eksik olup olmadığını kontrol etmek için sorgular çalıştırın.

## Kalite Kontrolünün Önemi

Bu süreci bu kadar ayrıntılı kontrol etmenin gereksiz olduğunu düşünebilir ve bir transformer'ın görünmeyen kelimelerle çıkarımlar yapma yeteneğine güvenebilirsiniz. 
Ancak, kritik karar verme içeren stratejik bir projede birkaç kalite kontrol yöntemi çalıştırmanızı öneririm.

Örneğin, bir hukuk özetinde, bir kelime davayı kazanmak veya kaybetmek arasındaki farkı yaratabilir.
Bir havacılık projesinde (uçaklar ve roketler), 0 hata toleransı standardı vardır.
Ne kadar çok kalite kontrol işlemi çalıştırırsanız, transformer çözümünüz o kadar güvenilir olacaktır.

## Sonuç

Güvenilir bir veri seti elde etmek çok çalışma gerektirir!
Transformerlar üzerine yazılmış her makale, kabul edilebilir veri setleri üretmek için yapılan çalışmalara bir şekilde atıfta bulunur.
Gürültülü ilişkiler de sorunlara neden olur.

---

