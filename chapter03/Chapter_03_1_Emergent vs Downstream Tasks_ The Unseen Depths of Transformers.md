# Transformers ile Doğal Dil Anlama

Transformers, önceden eğitilmiş modelleri serbest bıraktığımızda ve onların aşağı akış Doğal Dil Anlama (NLU) görevlerinde nasıl performans gösterdiklerini gözlemlediğimizde tam potansiyellerini ortaya koyarlar. Bir transformer modelini önceden eğitmek ve ince ayar yapmak çok zaman ve çaba gerektirir, ancak çoklu milyar parametreli bir transformer modelinin bir dizi NLU görevinde eylem halinde görülmesi çabaya değer. Gelişmiş NLP modelleri, insan temelini aşma arayışını başarmıştır. İnsan baz çizgisi, insanların NLU görevlerindeki performansını temsil eder. İnsanlar, erken yaşta transdüksiyon öğrenir ve hızla tümevarımsal düşünme geliştirir. Biz insanlar, dünyayı doğrudan duyularımızla algılarız. Makine zekası, dilimizi anlamlandırmak için tamamen kelimelere yazılmış algılarımıza güvenmektedir. Yine de makine zekası, artık temel insan baz çizgisini aşmıştır. Öncelikle, Bölüm 2'de ele aldığımız transformerların işlevsel ve matematiksel mimarisi arasındaki boşluğu, ortaya çıkış kavramını tanıtarak kapatacağız. Tüm makine modelleri, ortaya çıkış yeteneklerine ve bağımsız olarak yeni şeyler öğrenme kapasitesine sahiptir, ancak transformer'ın benzersiz mimarisi, dil anlayışını başka bir seviyeye taşımıştır. Daha sonra transformerların performansını nasıl ölçeceğimizi göreceğiz. Doğal Dil İşleme (NLP) görev performansını ölçmek, doğru ve yanlış sonuçlara dayanan çeşitli biçimlerdeki doğruluk skorlarını içeren basit bir yaklaşım olarak kalmaktadır. Bu sonuçlar, ölçüt görevleri ve veri kümeleri aracılığıyla elde edilir. SuperGLUE, örneğin, Google DeepMind, Facebook AI, New York Üniversitesi, Washington Üniversitesi ve diğerlerinin NLP performanslarını ölçmek için yüksek standartlar belirlemek üzere nasıl birlikte çalıştığının harika bir örneğidir. Son olarak, Stanford Sentiment TreeBank (SST-2), dilbilimsel kabul edilebilirlik ve Winograd şemaları gibi çeşitli aşağı akış görevlerini keşfedeceğiz. Transformers, iyi tasarlanmış ölçüt görevlerinde diğer modelleri geride bırakarak NLP'yi hızla bir sonraki seviyeye taşıyor. Alternatif transformer mimarileri ortaya çıkmaya ve gelişmeye devam edecektir.

Bu bölüm aşağıdaki konuları kapsamaktadır:
- Transformer dikkat başlıkları çıktıları nasıl üretir?
- Transformer performansını İnsan Baz Çizgisine karşı ölçme
- Ölçüm yöntemleri (Doğruluk, F1-skoru ve MCC)
- Ölçüt görevleri ve veri kümeleri
- SuperGLUE aşağı akış görevleri
- CoLA ile dilbilimsel kabul edilebilirlik
- SST-2 ile duygu analizi
- Winograd şemaları

Bu son teknoloji alanında yapılan tüm yenilikler ve kütüphane güncellemeleri ile paketler ve modeller düzenli olarak değişmektedir. Lütfen en son kurulum ve kod örnekleri için GitHub deposuna gidin: https://github.com/Denis2054/Transformers-for-NLP-and-Computer-Vision-3rd-Edition/tree/main/Chapter03 . Bu veya herhangi bir bölümdeki kodu çalıştırırken sorun yaşarsanız, Discord topluluğumuza bir mesaj gönderin ( https://www.packt.link/Transformers ). Makinaların dili nasıl temsil ettiğini anlamakla başlayalım.

Python kodları bulunmamaktadır.

---

