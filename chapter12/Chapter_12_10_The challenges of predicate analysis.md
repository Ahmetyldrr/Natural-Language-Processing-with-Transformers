# SRL (Semantik Rol Etiketleme) ve Zorlukları

SRL, yüklemlere (predicates) dayanır. SRL, yalnızca bir fiil (verb) sağladığınız sürece çalışır. Ancak milyonlarca cümle fiil içermez (eksiltili cümleler - ellipsis). Eğer bir LLM'ye (Büyük Dil Modeli) yalnızca bir iddia (assertion) sağlarsanız, bu işe yarar. Peki ya iddianız bir soruya cevap ise? Soru bir fiil içerebilir, örneğin: Kişi 1: İsterseniz ne içmek isterdiniz? Ancak cevap veren kişi fiil içermez: Kişi 2: Bir fincan kahve, lütfen.

GPT-4 ile ChatGPT'ye soralım: Aşağıdaki cümle için uygun SRL etiketleriyle semantik rol etiketleme yapın: Bir fincan kahve, lütfen.

ChatGPT dikkat çekici bir analiz sağlar:
"Bir fincan kahve, lütfen" cümlesi için Semantik Rol Etiketleme (SRL), temel bileşenleri ve anlamsal rollerini tanımayı içerir. Bu cümle kibar bir istektir ve bir ölçüde eksiltilidir, yani bağlamdan anlaşılan bazı öğeleri atlar. İşte bu cümle için SRL:
1. Bir fincan kahve - Arg1 (Tema): Bu, istenen nesne veya şeydir. Cümlenin ana odağıdır.
2. lütfen - ArgM-ADV (Zarf Değiştiricisi): Bu, bir nezaket işaretidir. İsteği kibarca yaptığını belirtir, istek kipini değiştirir.

Tam bir cümlede, "[Ben/biz] isterdik" gibi ima edilen bir Arg0 (Ajan) olabilir, ancak bu durumda konuşmacı atlanır çünkü istek bağlamında anlaşılır. Ana fiil (örneğin "isterdik") de atlanır ancak anlaşılır.

ChatGPT'nin istisnai öngörüsü vardır ve bu cümleyi analiz eder, her ne kadar eksiltili olsa da. Yüklem (predicate) örtüktür, açıkça ifade edilmez. SRL, bir fiili tespit etmeye dayanır, ancak ChatGPT bunu ima edilmiş olarak buldu!

Eksiltinin tanımı, bir cümleden anlaşılması gerekmeyen bir veya birkaç kelimeyi çıkarmaktır. Her gün yüz milyonlarca eksiltili cümle konuşulur ve yazılır.

Aşağıdaki soru nispeten basit, ancak cevap sadece bir isim içerir:
S: Bugün işe nasıl gittin?
C: Metro.

ChatGPT'yi zorlayalım ve zorluk çıkaralım: Aşağıdaki cümle için uygun SRL etiketleriyle semantik rol etiketleme yapın. Eksik olanı tahmin etmeye çalışın: metro.

ChatGPT gücünü konuşturur ve mükemmel bir yanıt verir:
"Metro" gibi tek bir kelime için Semantik Rol Etiketleme (SRL) zorlayıcıdır çünkü SRL genellikle farklı öğelerin rollerini anlamak için tam bir cümle gerektirir. Ancak, "metro"nun bir cümlede oynayabileceği rollere ve tam bir anlamsal yapı için ne gibi öğelerin eksik olabileceğine dair varsayımlar yapabilirim.
1. Metro - Bu, şu şekilde hizmet edebilir:
   - Arg1 (Tema): Eğer "metro" cümlenin nesnesiyse, tartışılan veya üzerinde hareket edilen şey olabilir. Örneğin, "Metro alıyorum" cümlesinde "metro" alınan şeydir.
   - Arg0 (Ajan): Farklı bir bağlamda, "metro" özne veya bir eylem gerçekleştiren ajan olabilir. Örneğin, "Metro istasyonda durur" cümlesinde "metro" durma eylemini gerçekleştiren varlıktır.

"Metro"yu içeren bir cümlede eksik olan öğeler şunları içerebilir:
- Fiil: Bir eylem veya durum, "çalışır", "durur" veya "kalabalıktır" gibi. Bu, metronun ne yaptığını veya ne durumda olduğunu anlamak için gereklidir.
- Arg0 (Ajan) veya Arg1 (Tema): Cümleye bağlı olarak, bir eylem gerçekleştiren bir ajan (metro kullanan bir kişi gibi) veya bir tema (hareket halinde olan metro gibi) olabilir.
- ArgM-LOC (Yer Değiştiricisi): "Şehir merkezinden" veya "ana istasyonda" gibi yer bilgisi.
- ArgM-TMP (Zaman Değiştiricisi): "Yoğun saatlerde" veya "9'da" gibi zaman bilgisi.
- ArgM-DIR (Yön Değiştiricisi): "Şehir merkezine" veya "havalimanından" gibi yön bilgisi.

Örneğin, "Metro şehir boyunca çalışır" gibi tam bir cümlede, "metro" Arg0 (Ajan), "çalışır" fiil ve "şehir boyunca" ArgM-LOC (Yer Değiştiricisi) olur.

Yüklem içermeyen cümleleri anlamanın zor olduğu milyonlarca örnek daha bulabiliriz. Bazı durumlarda, LLM'ler eksiltikleri tespit etmede ve boşlukları doldurmada başarılı olacaktır. Bazen, bağlam eksikliği sadece eksik olanın ne olduğunu tahmin etmeye yol açabilir.

Bu bölüm, SRL'nin zorluklarını gösterdi. Şimdi SRL'yi yeniden tanımlayalım ve nasıl yönetileceğini gösterelim.

Python kodu bulunmamaktadır, bu nedenle açıklama yapılmamıştır. Çeviri, orijinal metnin birebir çevirisidir.

---

