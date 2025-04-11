# Bu Bölümde
Bu bölümde, geliştirme odağı OpenAI transformer modellerinin mimarisinde olacaktır. Odaklanılacak dört iyileştirme vardır: sadece kod çözücü, ölçek, görev genelleştirme ve yeni terminoloji.

## Sadece Kod Çözücü
Bölüm 2'de, Transformer Modelinin Mimarisine Başlarken, orijinal Transformer'ı bir kodlayıcı ve kod çözücü yığını olarak tanımladık. Bölüm 5'te, BERT aracılığıyla İnce Ayarlamaya Dalmak, sadece kodlayıcı yığını olan BERT'i tanıttı. Bu bölümde, sadece kod çözücü yığını sunulacaktır. Bu konfigürasyonlardan birini seçmeye götüren matematiksel mantık zinciri veya kanıtın ne olduğunu kendinize sorabilirsiniz. Hiçbiri! Transformer modellerinin geliştirilmesi, ampirik veri odaklı içgörülere, donanım kısıtlamalarına ve değerlendirmelere dayanır. Bu, onların mimarlarının sezgisel ve yaratıcı zihinleri aracılığıyla sürekli olarak gelişeceğini açıklar.

## Ölçek
Ölçek, transformer modellerinde kritik bir özellik olmaya devam etmektedir. GPT modelleri, bu bölümde keşfedeceğiniz gibi, boyut olarak büyüdü. Neden? Hedef, kelimeler ve bağlamlar arasındaki birçok bağı yakalamaktır. Bir kelimenin birçok farklı anlamı olabilir, bağlama bağlı olarak. Örneğin, "eat" fiili basit görünüyor. Doğru mu? Ancak birisinin bir şeyi yediğini veya bir şeyin yenebileceğini, birisinin yemek istemeyebileceğini veya belki de yiyebileceğini çabucak keşfederiz. Liste neredeyse sonsuzdur! Bu incelikleri ifade etmek için birçok parametre oluşturabiliriz. Sorun, doğru sayıda parametreyi bulmaktır. Çok fazla parametre maliyetli ve işe yaramaz olabilir. Çok az parametre doğruluk azaltabilir. Doğru parametre sayısı deneme yanılma yoluyla elde edilecektir.

## Görev Genelleştirme
Bir model belirli bir göreve eğitilirse, Bölüm 5'te ince ayarladığımız ve eğittiğimiz model gibi göreve özgüdür. Giriş sağlar ve bir kelime, sınıflandırma, soruya cevap ve diğer NLP görevleri gibi çıkış alırız. Ancak, potansiyel olarak yüzlerce görevle karşı karşıya kaldığımızda, yüzlerce göreve özgü model oluşturmayı hayal bile edemeyiz! İşte OpenAI GPT modelleri gibi Üretken Yapay Zeka modelleri burada devreye giriyor. Bunu şöyle özetleyebilirsiniz: "Bir cümleyi başlatıyoruz ve model onu bitiriyor." Örneğin, bir arkadaşınıza "Bana lezzetli elma pastan için tarifini ver, lütfen" diyebilirsiniz. Düşünün. Ne beklersiniz? Bir araba listesi mi? Bir ev inşa etme talimatları mı? Hayır, bir bileşen listesi ve elma pastası pişirme talimatları beklersiniz. Transformer modelleri büyük veri kümelerine eğitilmiştir ve istatistiksel olarak sonraki kelime(leri) belirleyecektir. Cümleyi "prompt" tasarlayarak başlattınız, diğer kişi veya GPT cümleyi "yanıt" üreterek devam ettirecektir. Basitçe net bir bağlamla bir cümleyi başlatıp GPT'nin devam etmesini bekleyerek oluşturabileceğiniz binlerce görevi kolayca hayal edebilirsiniz! İşte genel amaçlı, Üretken Yapay Zeka dünyasına girdiniz.

## Yeni Terminoloji
LLM'ler, Üretken Yapay Zeka ve Temel Modeller gibi en son teknolojiyle yeni kelimeler ortaya çıkıyor. Bu terimlere ve temsil ettikleri kavramlara kendinizi kaptırmayın. Onlara diğer yeni kelimeler gibi alışın. Örneğin, OpenAI GPT modelleri artık doğal dili işlemek için milyarlarca parametreye sahip. Bu nedenle, "Büyük Dil Modelleri"dir. Bir GPT modeli bir cümleyi, bir "prompt"ı devam ettirebilir, bu nedenle Üretken Yapay Zeka modelleridir. GPT modelleri kelimeleri, resimleri ve sesleri işleyebilir. Kabiliyetleri üzerine yüzlerce görev inşa edebiliriz. Bu, diğer sistemleri inşa edebileceğimiz Temel Modeller haline getirir. Bu bölümde ilerlerken bu ana noktaları aklınızda tutun. GPT'lerin yayılmasında kendimizi yönlendirmek de aynı derecede önemlidir.

Python kodları bulunmamaktadır, bu nedenle satır satır açıklama gerekmemektedir. Çeviri, orijinal metnin birebir çevirisidir.

---

