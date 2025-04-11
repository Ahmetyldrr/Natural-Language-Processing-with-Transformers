# Gelişmiş Büyük Çok Amaçlı Transformatör Modelleri: Temel Modeller

Gelişmiş büyük çok amaçlı transformatör modelleri, onları tanımlamak için yeni bir ad gerektiren bir paradigma değişikliği temsil eder: Temel Modeller. Buna uygun olarak, Stanford Üniversitesi Temel Modeller Araştırma Merkezi'ni (CRFM) kurdu. Ağustos 2021'de CRFM, yüzün üzerinde bilim insanı ve profesyonel tarafından yazılmış iki yüz sayfalık bir makale yayınladı: Temel Modellerin Fırsatları ve Riskleri Üzerine. Temel Modeller akademi tarafından değil, büyük teknoloji endüstrisi tarafından yaratıldı. Google, transformatör modelini icat etti ve bu da Google BERT, LLaMa, PaLM ve daha fazlasına yol açtı. Microsoft, ChatGPT, GPT-4, GPT-4o ve yakında daha fazlasını üretmek için OpenAI ile ortaklık kurdu. Büyük teknoloji, veri merkezlerine akan petabayt verilerinin üstel artışıyla başa çıkmak için daha iyi bir model bulmak zorunda kaldı. Transformatörler böylece zorunluluktan doğdu.

## Büyük Dil Modellerinin (LLM) Evrimi

LLM'lerin evrimini inceleyerek endüstriyel AI modellerine olan ihtiyacı anlayabiliriz. Transformatörlerin iki farklı özelliği vardır: yüksek düzeyde homojenleştirme ve akıllara durgunluk veren ortaya çıkma özellikleri. Homojenleştirme, çok çeşitli görevleri gerçekleştirmek için tek bir model kullanmayı mümkün kılar. Bu yetenekler, süper bilgisayarlarda milyarlarca parametreli modellerin eğitilmesiyle ortaya çıkar.

## Transformatör Modellerinin Ekosistemi

Transformatör modellerinin mevcut ekosistemi, AI'deki diğer evrimlerin aksine benzersizdir ve dört özellik ile özetlenebilir:

### Model Mimarisi

Model endüstriyel düzeydedir. Modelin katmanları özdeştir ve özellikle paralel işleme için tasarlanmıştır. Transformatörlerin mimarisini 2. Bölüm'de, Transformatör Modelinin Mimarisi ile Başlarken bölümünde ele alacağız.

### Veri

Büyük teknoloji, insanlığın tarihindeki en büyük veri kaynağına sahiptir ve bu veri çoğunlukla insan odaklı çevrimiçi aktiviteler ve etkileşimler yoluyla üretilir; bu aktiviteler arasında tarama alışkanlıkları, arama sorguları, sosyal medya gönderileri ve çevrimiçi alışverişler bulunur.

### Hesaplama Gücü

Büyük teknoloji, bu ölçekte daha önce görülmemiş bilgisayar gücüne sahiptir. Örneğin, GPT-3 yaklaşık 50 petaflop (Saniyede Kayan Noktalı İşlemler) hızında eğitildi ve Google'ın artık 80 petaflop'u aşan alan-specific süper bilgisayarları vardır. Ayrıca, GPT-4, PaLM ve diğer LLM'ler modellerini eğitmek için binlerce GPU kullanır.

### Prompt Mühendisliği

Yüksek düzeyde eğitilmiş transformatörler, bir görev yapmak üzere bir prompt ile tetiklenebilir. Prompt doğal dilde girilir. Ancak kullanılan kelimeler bir miktar yapı gerektirir ve bu da promptları bir meta dil haline getirir.

## Temel Modeller ve Transformatörler Arasındaki Fark

Tüm Temel Modeller transformatördür, ancak tüm transformatörler Temel Model değildir. Bir Temel Model, belirli görevler için eğitilmiş standart bir transformatörden daha fazlasını gerçekleştirebilir. Temel Model, yalnızca belirli görevleri çözmekle kalmayıp, genel amaçlı bir AI ajanı olarak tasarlanmıştır. Bir Temel Model, süper bilgisayarlarda milyarlarca veri kaydı ve milyarlarca parametre üzerinde eğitilmiş bir transformatör modelidir. Model, daha fazla ince ayar yapmadan geniş bir görev yelpazesini gerçekleştirebilir. Böylece, Temel Modellerin ölçeği benzersizdir. GPT-4, Google BERT, PaLM, Gemini ve birçok diğer model artık Temel Model olarak nitelendirilebilir. Bommasani ve diğerleri (2023), pazardaki (veri kümeleri, modeller ve uygulamalar) artan sayıda varlığı takip etmek için Ekosistem Grafikleri oluşturdu. Şimdi, Temel Modellerin nasıl çalıştığına ve programları nasıl geliştirdiğimize dair bir örnek inceleyeceğiz.

---

