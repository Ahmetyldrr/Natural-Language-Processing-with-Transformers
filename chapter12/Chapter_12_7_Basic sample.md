# Temel Örneklerin Analizi ve Semantic Role Labeling (SRL)

Temel örnekler sezgisel olarak basit görünse de analiz edilmesi zor olabilir. Bileşik cümleler, sıfatlar, zarflar ve kipler tanımlanması zor olan ögelerdir. İlk örnek uzun, ancak transformer için nispeten kolay: Bob gerçekten 50 kişiye sadece birkaç saat içinde yemek hazırlayabileceğini düşündü mü? PropBank (Proposition Bank) yapısına dayanan veri setinin argümanlarının tanımını GitHub'da kullanabiliriz: https://github.com/propbank/propbank-documentation/blob/master/annotation-guidelines/Propbank-Annotation-Guidelines.pdf. Örneğin, bu alıntıdaki "think" fiili şu şekilde yorumlanabilir: V, "think" fiilini tanımlar. ARG0, ajanı tanımlar; böylece Bob, ajan veya "pro-ajan"dır. ARGM-ADV, "really"yi bir zarf (ADV) olarak tanımlar, ARGM zarfın bir ek (gereksiz) sağladığını ve bu nedenle numaralandırılmadığını belirtir.

## Fiillerin Tanımlanması

İlk fiil "Did"dir: 
Şekil 12.3: "Did" fiilinin tanımlanması

İkinci tanımlanan fiil "think"dir: 
Şekil 12.4: "think" fiilinin tanımlanması

Bu gösterimi yakından incelediğimizde, SRL'nin bazı ilginç özelliklerini tespit edebiliriz:
- "think" fiilinin tespit edilmesi
- Ana fiil olarak yorumlanabilecek "prepare" tuzaktan kaçınmak. Bunun yerine, "prepare" "think" argümanının bir parçası olarak kaldı.
- Bir zarfın tespit edilmesi ve etiketlenmesi

Üçüncü fiil "could"dir: 
Şekil 12.5: "could" fiilinin ve argümanının tanımlanması

Şimdi "prepare" fiiline geçelim, etiketleyelim ve bağlamını analiz edelim: 
Şekil 12.6: "prepare" fiilinin, argümanlarının ve değiştiricilerinin tanımlanması

Bu cümleyi analiz ettikten sonra, ChatGPT with GPT-4'e aynı görevi yapmasını isteyelim: Aşağıdaki cümle için uygun SRL etiketleriyle semantic role labeling yapın: Bob gerçekten 50 kişiye sadece birkaç saat içinde yemek hazırlayabileceğini düşündü mü?

ChatGPT'nin yanıtı oldukça inandırıcı, eğitiminin görev-specifik ve sözdiziminden bağımsız olduğunu düşünürsek:
Semantic Role Labeling (SRL), yüklemi (genellikle bir fiil) ve argümanlarını (yüklemle ilgili çeşitli rolleri yerine getiren varlıklar veya öbekler) tanımayı içerir. İşte cümlenin SRL ayrıştırması: "Bob gerçekten 50 kişiye sadece birkaç saat içinde yemek hazırlayabileceğini düşündü mü?"

1. Yüklem: "think"
   - Arg0 (Ajan, Düşünen): Bob - Düşünen kişi.
   - ArgM-ADV (Zarf Değiştiricisi): really - Düşünmenin nasıl yapıldığını değiştirir.
   - Arg1 (Düşünce İçeriği): [he could prepare a meal for 50 people in only a few hours] - Bob'un düşündüğü şey.

2. Arg1 içinde başka bir yüklem var: "prepare"
   - Arg0 (Ajan, Hazırlayan): he (Bob'a atıfta bulunarak) - Hazırlayan kişi.
   - Arg1 (Tema, Hazırlanan Şey): a meal - Hazırlanan nesne.
   - Arg2 (Çıkar Sağlanan): for 50 people - Yemek kimler için hazırlanıyor.
   - ArgM-TMP (Zaman Değiştiricisi): in only a few hours - Yemek hazırlama zaman dilimi.

Cümle ayrıca yardımcı fiiller ve soru öğeleri içerir, ancak bunlar genellikle standart SRL ek açıklamalarının odak noktası değildir. Ana odak, "think" ve "prepare" yüklemleri ve ilgili argümanlarıdır.

## Keskin Kenarlı LLM'lerin Özellikleri

Gelişmiş bir LLM'nin devrim niteliğindeki özelliklerini görebiliriz:
- Sözdiziminden bağımsız: Görev-specifik değildir ve sözdizimi kuralları veya ağaçları yoktur.
- Genel amaçlı: Belirli bir görev için eğitilmemiştir.
- Stokastik: Her seferinde bir isteğe kelimesi kelimesine cevap verecek şekilde eğitilmemiştir.

## Stokastik Doğanın İncelenmesi

7. Bölüm'de, ChatGPT ile Üretken Yapay Zeka Devrimi'nde gördüğümüz gibi, GPT modellerinin (ve diğer önde gelen LLM'lerin) stokastik doğası, sıcaklık, top-k ve top-p ile kontrol edilebilir, böylece model az veya çok yaratıcı olur.

Aynı isteği ChatGPT'ye tekrar gönderelim. Amacımız, yanıtın güvenilir olup olmadığını görmek, kelimesi kelimesine aynı açıklamayı tekrar edip etmediğini görmek değil:
Aşağıdaki cümle için uygun SRL etiketleriyle semantic role labeling yapın: Bob gerçekten 50 kişiye sadece birkaç saat içinde yemek hazırlayabileceğini düşündü mü?

ChatGPT with GPT-4 yine güvenilir bir yanıt veriyor, ancak önceki yanıtın kelimesi kelimesine aynısı değil:
Semantic Role Labeling (SRL), bir cümledeki temel öğeleri ve rollerini tanımayı içerir. İşte cümlenizin SRL'i:
1. Did Bob really think - Bu ana cümledir.
   - Bob: Arg0 (Ajan) - Düşünen kişi.
   - think: Fiil - Cümlenin eylemi.

2. he could prepare a meal for 50 people in only a few hours - Bu, Bob'un ne düşündüğünü temsil eden alt cümledir.
   - he: Arg0 (Ajan) - Bob, yemeyi hazırlayan kişi.
   - could prepare: Fiil - Hazırlama eylemi.
   - a meal: Arg1 (Tema) - Hazırlanan şey.
   - for 50 people: Arg2 (Çıkar Sağlanan) - Yemek kimler için hazırlanıyor.
   - in only a few hours: ArgM-TMP (Zaman Değiştiricisi) - Eylem için zaman dilimini belirtir.

Böylece, cümle bu anlamsal rollere ayrılır, kim ne yaptığında, kime ve ne zaman olduğunu gösterir.

Yanıtın güvenilir olduğunu, ancak kelimesi kelimesine tutarlı olmadığını görebiliriz.

## Sonuç

Şimdi, ChatGPT with GPT-4 gibi gelişmiş LLM'lerin genel amaçlı, sözdiziminden bağımsız ve stokastik doğasını inceledik.

---

