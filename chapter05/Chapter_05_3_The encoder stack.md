# Orijinal Transformer Modelinden İlk Yapı Taşı: Encoder Katmanı

İlk yapı taşı olarak Orijinal Transformer modelinden bir encoder katmanı alacağız. Encoder katmanı, 2. Bölüm'de anlatıldığı gibi, Transformer Modelinin Mimarisi ile Başlarken, Şekil 5.1'de gösterilmektedir: 
Şekil 5.1: Encoder katmanı 
BERT modeli decoder katmanları kullanmaz. Bir BERT modelinde encoder yığını vardır, ancak decoder yığını yoktur. BERT modeli, bazı girdi tokenlarının gizlendiği ("maskelendiği") Maskeli Dil Modellemesi (MLM) kullanır ve dikkat katmanları bağlamı anlamayı öğrenmelidir. Model, aşağıdaki bölümlerde bir BERT encoder katmanını incelediğimizde göreceğimiz gibi, gizli tokenları tahmin edecektir.

Orijinal Transformer, N = 6 katmanlı bir yığın içerir. Orijinal Transformer'ın boyut sayısı d<sub>model</sub> = 512'dir. Orijinal Transformer'ın dikkat başlıklarının sayısı A = 8'dir. Orijinal Transformer'ın başlık boyutları:
 
BERT encoder katmanları Orijinal Transformer modelinden daha büyüktür. Encoder katmanları ile farklı boyutlarda BERT modelleri oluşturulabilir:

*   **BERT BASE**, N = 12 encoder katmanlı bir yığın içerir. d<sub>model</sub> = 768, BERT makalesinde olduğu gibi H = 768 olarak da ifade edilebilir. Çoklu dikkat alt katmanı A = 12 başlık içerir. Her bir başlığın boyutu z<sub>A</sub> Orijinal Transformer modelinde olduğu gibi 64 olarak kalır: 
    Her bir çoklu dikkat alt katmanının çıktısı, 12 başlığın çıktısı olacaktır: 
    output_multi-head_attention={z<sub>0</sub>, z<sub>1</sub>, z<sub>2</sub>,…, z<sub>11</sub>}
*   **BERT LARGE**, N = 24 encoder katmanlı bir yığın içerir. d<sub>model</sub> = 1024. Çoklu dikkat alt katmanı A = 16 başlık içerir. Her bir başlığın boyutu z<sub>A</sub> Orijinal Transformer modelinde olduğu gibi 64 olarak kalır: 
    Her bir çoklu dikkat alt katmanının çıktısı, 16 başlığın çıktısı olacaktır: 
    output_multi-head_attention={z<sub>0</sub>, z<sub>1</sub>, z<sub>2</sub>,…, z<sub>15</sub>}

Modellerin boyutları aşağıdaki gibi özetlenebilir:
Şekil 5.2: Transformer modelleri 

BERT modelleri, BERT modellerinin ana yönlerini gösteren bu konfigürasyonlarla sınırlı değildir. Çok sayıda varyasyon mümkündür. Boyut ve ölçüler, BERT tarzı ön eğitimde önemli bir rol oynar. BERT modelleri insan gibidir; daha fazla çalışma belleği (boyutlar) ve bilgi (veri) ile daha iyi sonuçlar üretirler. Büyük miktarda veri öğrenen büyük transformer modelleri, aşağı akış NLP görevleri için daha iyi ön eğitim alacaktır.

İlk alt katmana gidip bir BERT modelinde girdi embedding ve pozisyonel kodlamanın temel yönlerini görelim.

Bu çeviride python kodları bulunmamaktadır.

---

