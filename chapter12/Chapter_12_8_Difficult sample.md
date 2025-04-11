# Bu Bölümün Çevirisi
Bu bölüm, transformatörün çözmesi gereken zor yapılar içeren örnekleri çalıştıracaktır. Karmaşık bir örnekle başlayalım: cümle="Şimdi, diskleri buzlayın çocuklar!" Bu örnek, genellikle sadece bir isim olduğunu düşündüğümüz bir kelimeyi gösterir. Ancak, şüphe ettiğimizden daha fazla kelime hem isim hem de fiil olabilir. Örneğin, buzlamak (ice) hokeyde diski tüm pist boyunca ve rakibin gol çizgisinin ötesine vurmak için kullanılan bir fiildir. Disk (puck) hokeyde kullanılan bir disktir. Bir hokey koçu, günün başlangıcını takıma diskleri buzlamak (icing pucks) için antrenman yapmalarını söyleyerek yapabilir. Koç "Şimdi, diskleri buzlayın çocuklar!" diye bağırdığında emir cümlesini elde ederiz. Kolaylıkla anlaşılacağı üzere, günlük dilde "çocuklar" (guys) kelimesi, cinsiyet ayrımı gözetmeksizin kişileri ifade edebilir. Şimdi ChatGPT'nin bu zor cümleye nasıl tepki verdiğini görelim: Aşağıdaki cümle için uygun SRL etiketleriyle semantik rol etiketlemesi yapın: Şimdi, diskleri buzlayın çocuklar! ChatGPT, görev spesifik eğitimi olmadan ve sözdizimi içermeyen yaklaşımıyla, tuzağa düşmez: "Şimdi, diskleri buzlayın çocuklar!" cümlesi için Semantik Rol Etiketlemesi (SRL), anahtar elemanları ve onların semantik rollerini tanımlamayı içerir. Bu cümle, gayet resmi olmayan ve emir verici doğası nedeniyle biraz zorlayıcıdır. İşte bu cümle için SRL'ye bir girişim: 
1. Şimdi - ArgM-TMP (Zaman Değiştiricisi): Eylemin zamanlamasını belirtir. 
2. buzlayın - Fiil: Bu biraz alışılmadık, ancak bu bağlamda "buzlayın" (ice) emir kipinde bir fiil olarak kullanılıyor gibi görünmektedir, yani diskleri kullanma veya yerleştirme anlamına gelir. 
3. diskleri - Arg1 (Tema): Etkilenilen nesne veya şey, bu durumda 'diskler'. 
4. çocuklar - Arg0 (Etmen): Eylemi gerçekleştirmek üzere talimat verilen veya hitap edilen kişiler. Böyle bir emir cümlesinde, özne (siz) genellikle ima edilir, ancak burada "çocuklar" eylemi gerçekleştirmesi gerekenler olarak açıkça belirtilmiştir. Dolayısıyla, "Şimdi, diskleri buzlayın çocuklar!" cümlesi, "çocuklar"a "diskler" üzerinde (muhtemelen onları kullanıma sokma veya yerleştirme anlamında) şu anda hareket etmeleri talimatını verir. LLM'miz ChatGPT, bu durumda mükemmel bir iş çıkardı! Sözdizimi yapılarını açıkça öğrenmeden bulan bir modelin gücüne hayran olmamak elde değil! Ancak, ne yazık ki NLP'de hiçbir şey mükemmel değildir. Şimdi SRL'nin kapsamını sorgulayalım.

# Python Kodları Yok
Bu metinde herhangi bir Python kodu bulunmamaktadır. 

Eğer bir kod pasajı olsaydı, satır satır açıklamalar yapılırdı. Ancak bu metin sadece bir İngilizce paragrafın Türkçe çevirisini içermektedir.

---

