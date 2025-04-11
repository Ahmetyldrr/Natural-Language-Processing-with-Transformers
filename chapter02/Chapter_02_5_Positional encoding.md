# Konumsal Kodlama (Positional Encoding)

Transformer'ın konumsal kodlama fonksiyonuna, bir dizideki bir kelimenin pozisyonu hakkında hiçbir fikir olmadan gireriz: 
Şekil 2.5: Konumsal Kodlama 
Transformer'ın eğitim hızına yüksek bir maliyet getirecek ve dikkat alt katmanlarını çalışması zorlaştıracak bağımsız konumsal vektörler oluşturamayız. 
Bir dizideki bir tokenin pozisyonunu tanımlamak için ek vektörlere sahip olmak yerine, girdi embedding'ine bir konumsal kodlama değeri eklemek fikri vardır. 
Orijinal Transformer modeli, yalnızca kelime embedding ve pozisyon kodlamasını içeren bir vektöre sahiptir. 
Transformer, konumsal kodlama fonksiyonunun çıktısının her bir vektörü için sabit bir boyut d_model = 512 (veya model için başka bir sabit değer) bekler.

Eğer kelime embedding alt katmanında kullandığımız cümleye geri dönersek, "black" ve "brown" kelimelerinin anlamsal olarak benzer olabileceğini, ancak cümlede birbirlerinden uzak olduklarını görebiliriz: 
"The black brown cat sat on the couch and the dog slept on the rug."
"black" kelimesi 2. pozisyonda, pos=2, ve "brown" kelimesi 10. pozisyonda, pos=10. 
Sorunumuz, her kelimenin kelime embedding'ine, bu bilgiyi içerecek bir değer eklemenin bir yolunu bulmaktır. 
Ancak, d_model = 512 boyutlarına bir değer eklememiz gerekiyor!

Her kelime embedding vektörü için, "black" ve "brown" kelimelerinin kelime embedding vektörünün (0,512) aralığındaki her bir i boyutu için bilgi sağlamanın bir yolunu bulmalıyız. 
Konumsal kodlama elde etmek için birçok yol vardır. 
Bu bölüm, tasarımcıların birim küre kullanarak pozisyon kodlamasını temsil etme yöntemine odaklanacaktır. 
Vaswani ve diğerleri (2017), her pozisyon ve her boyut i için konumsal kodlama (PE) için farklı frekanslar üretebilmemiz için sinüs ve kosinüs fonksiyonları sağlar: 
Eğer kelime embedding vektörünün başlangıcından başlarsak, i=0 ile başlayacağız ve i=511 ile biteceğiz. 
Bu, sinüs fonksiyonunun çift sayılara ve kosinüs fonksiyonunun tek sayılara uygulanacağı anlamına gelir. 
Bazı implementasyonlar bunu farklı şekilde yapar. 
Bu durumda, sinüs fonksiyonunun tanım kümesi , ve kosinüs fonksiyonunun tanım kümesi olabilir. 
Bu, benzer sonuçlar üretecektir. 
Bu bölümde, Vaswani ve diğerleri (2017) tarafından açıklandığı şekilde fonksiyonları kullanacağız.

Python pseudo-koduna kelimesi kelimesine çevirisi aşağıdaki kodu üretir:
```python
def positional_encoding(pos, pe):
    for i in range(0, 512, 2):
        pe[0][i] = math.sin(pos / (10000 ** ((2 * i) / d_model)))
        pe[0][i + 1] = math.cos(pos / (10000 ** ((2 * i) / d_model)))
    return pe
```
Google Brain Trax ve Hugging Face gibi kütüphaneler, kelime embedding bölümü ve mevcut konumsal kodlama bölümü için kullanıma hazır kütüphaneler sağlar. 
Böylece, bu bölümde paylaştığım kodu çalıştırmanıza gerek yoktur. 
Ancak, kodu keşfetmek isterseniz, GitHub deposundaki bu bölümün dizininde positional_encoding.ipynb not defterinde bulacaksınız.

# Konumsal Kodlamanın Uygulanması

Örneğin, pos=2 için sinüs fonksiyonunun grafiğini görmek isteyebilirsiniz. 
Aşağıdaki grafiği Google'da arayabilirsiniz: 
plot y=sin(2/10000^(2*x/512))

Grafiği girin: 
Şekil 2.6: Google ile Grafik Çizme

Aşağıdaki grafiği elde edeceksiniz: 
Şekil 2.7: Grafik

Eğer bu bölümde ayrıştırdığımız cümleye geri dönersek, "black" kelimesinin pos=2 ve "brown" kelimesinin pos=10 pozisyonunda olduğunu görebiliriz: 
"The black brown cat sat on the couch and the dog slept on the rug."

Eğer sinüs ve kosinüs fonksiyonlarını pos=2 için kelimesi kelimesine uygularsak, boyutu 512 olan bir konumsal kodlama vektörü elde ederiz: 
PE(2)= 
[[ 9.09297407e-01 -4.16146845e-01  9.58144367e-01 -2.86285430e-01
   9.87046242e-01 -1.60435960e-01  9.99164224e-01 -4.08766568e-02
   ...
   5.47683925e-08  1.00000000e+00  5.09659337e-08  1.00000000e+00
   4.74274735e-08  1.00000000e+00  4.41346799e-08  1.00000000e+00]]

Ayrıca, pos=10 için boyutu 512 olan bir konumsal kodlama vektörü elde ederiz: 
PE(10)= 
[[-5.44021130e-01 -8.39071512e-01  1.18776485e-01 -9.92920995e-01
   6.92634165e-01 -7.21289039e-01  9.79174793e-01 -2.03019097e-01
   ...
   2.73841977e-07  1.00000000e+00  2.54829672e-07  1.00000000e+00
   2.37137371e-07  1.00000000e+00  2.20673414e-07  1.00000000e+00]]

Vaswani ve diğerleri (2017) fonksiyonlarının sezgisel bir kelimesi kelimesine çevirisini Python'a uyguladığımızda elde ettiğimiz sonuçlara baktıktan sonra, sonuçların anlamlı olup olmadığını kontrol etmemiz gerekir. 
Kelime embedding için kullanılan kosinüs benzerlik fonksiyonu, pozisyonların yakınlığını daha iyi görselleştirmek için kullanışlıdır: 
cosine_similarity(pos(2), pos(10))= [[ 0.8600013 ]]

"black" ve "brown" kelimelerinin pozisyonu arasındaki benzerlik ve kelime alanı (birlikte kullanılan kelime grupları) benzerliği farklıdır: 
cosine_similarity(black, brown)= [[ 0.9998901 ]]

Pozisyon kodlamasının benzerlik değeri, kelime embedding benzerliğinden daha düşüktür. 
Konumsal kodlama, bu kelimeleri birbirinden ayırmıştır.

# Konumsal Kodlamanın Kelime Embedding Vektörüne Eklenmesi

Transformer'ın yazarları, konumsal kodlama vektörünü kelime embedding vektörüne basitçe ekleyerek buldular: 
Şekil 2.8: Konumsal Kodlama

Eğer geri dönüp "black" kelimesinin kelime embedding'ini alırsak, örneğin, ve buna y1 = black adını verirsek, konumsal kodlama fonksiyonları ile elde ettiğimiz pozisyon vektörü pe(2)'ye eklemeye hazırız. 
"black" girdi kelimesinin konumsal kodlamasını pc(black) elde edeceğiz: 
pc(black) = y1 + pe(2)

Aşağıdaki örnekte, "black" kelimesinin embedding vektörüne pozisyon vektörünü ekleriz, her ikisi de aynı boyutta (512): 
```python
for i in range(0, 512, 2):
    pe[0][i] = math.sin(pos / (10000 ** ((2 * i) / d_model)))
    pc[0][i] = (y[0][i] * math.sqrt(d_model)) + pe[0][i]

    pe[0][i + 1] = math.cos(pos / (10000 ** ((2 * i) / d_model)))
    pc[0][i + 1] = (y[0][i + 1] * math.sqrt(d_model)) + pe[0][i + 1]
```
Elde edilen sonuç, d_model = 512 boyutlu nihai konumsal kodlama vektörüdür: 
pc(black)= 
[[ 9.09297407e-01 -4.16146845e-01  9.58144367e-01 -2.86285430e-01
   ...
   4.74274735e-08  1.00000000e+00  4.41346799e-08  1.00000000e+00]]

Aynı işlem, "brown" kelimesine ve bir dizideki diğer tüm kelimelere uygulanır.

"black" ve "brown" kelimelerinin konumsal kodlama vektörlerine kosinüs benzerlik fonksiyonunu uygulayabiliriz: 
cosine_similarity(pc(black), pc(brown))= [[0.9627094]]

Şimdi, "black" ve "brown" kelimelerini temsil eden üç durum için uyguladığımız üç kosinüs benzerlik fonksiyonu aracılığıyla konumsal kodlama sürecini net bir şekilde görüyoruz: 
[[0.99987495]] kelime benzerliği
[[0.8600013]] konumsal kodlama vektör benzerliği
[[0.9627094]] nihai konumsal kodlama benzerliği

İlk kelime benzerliğinin yüksek olduğunu, 0.99 değerinde olduğunu gördük. 
Daha sonra, 2 ve 10 pozisyonlarının konumsal kodlama vektörünün bu iki kelimeyi daha düşük bir benzerlik değeri olan 0.86 ile birbirinden ayırdığını gördük. 
Son olarak, her kelimenin kelime embedding vektörünü kendi konumsal kodlama vektörüne ekledik. 
Bu, iki kelimenin kosinüs benzerliğini 0.96'ya getirdi. 
Her kelimenin konumsal kodlaması artık ilk kelime embedding bilgisini ve konumsal kodlama değerlerini içerir.

Konumsal kodlamanın çıktısı, çoklu kafalı dikkat alt katmanına yol açar.

---

