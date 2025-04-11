# Raffel ve Ekibi (2019) tarafından Yapılan Çalışma: Görev-Spesifik Formatların Birleştirilmesi

Raffel ve ekibi (2019) hala bir problemi çözmek zorundaydı: görev-spesifik formatları birleştirmek. Fikir, transformatöre gönderilen her görev için bir girdi formatı bulmaktı. Bu şekilde, model parametreleri, bir metinden-metin formatında her tür görev için eğitilecekti. Google T5 ekibi basit bir çözüm üretti: bir girdi dizisine önek eklemek.

# Önek Kullanımının Önemi

Binlerce ek kelime haznesine birçok dilde ihtiyaç duyulmayacaktı, eğer bir önek icat edilmeseydi. Örneğin, "prepayment", "prehistoric", "Precambrian" ve binlerce başka kelimeyi tanımlamak için kelimeler bulmak zorunda kalacaktık, eğer "pre" gibi bir önek kullanmasaydık. Raffel ve ekibi (2019) bir girdi dizisine önek eklemeyi önerdi. T5 öneki, bazı transformer modellerinde sınıflandırma için [CLS] gibi bir etiket veya gösterge değildir. Bunun yerine, bir T5 öneki, bir transformatörün çözmesi gereken bir görevin özünü içerir.

# Öneklerin Anlamı

Bir önek, aşağıdaki örneklerde olduğu gibi anlam taşır:
- "translate English to German: " + [sequence] çeviriler için, Chapter 4'te yaptığımız gibi.
- "cola sentence: " + [sequence] The Corpus of Linguistic Acceptability (CoLA) için, Chapter 5'te BERT transformer modelini fine-tune ettiğimiz gibi.
- "stsb sentence 1: " + [sequence] semantic textual similarity benchmarks için.
- "summarize " + [sequence] metin özetleme problemleri için, bu bölümün Metin Özetleme ile T5 kısmında çözeceğimiz gibi.

# Birleştirilmiş Girdi Formatı

Şimdi, Şekil 13.2'de ifade edilen geniş bir NLP görevleri yelpazesi için birleştirilmiş bir format elde ettik:

Şekil 13.2: Transformatör modelinin girdi formatını birleştirmek

Birleştirilmiş girdi formatı, T5'te hangi problemi çözmesi gerektiğine bakılmaksızın bir sonuç dizisi üreten bir transformatör modeline yol açar. Birçok NLP görevinin girdisi ve çıktısı birleştirilmiştir, Şekil 13.3'te gösterildiği gibi:

Şekil 13.3: T5 metin-metin çerçevesi

# Birleştirme İşleminin Faydaları

Birleştirme işlemi, geniş bir görev yelpazesi için aynı modeli, hiperparametreleri ve optimize edicileri kullanmayı mümkün kılar. Chapter 4'te çevirileri keşfettik. Chapter 5'te The Corpus of Linguistic Acceptability (CoLA) üzerinde bir modeli fine-tune ettik. Bu bölümde, T5'i özetleme görevlerine uygulayacağız.

# T5 Transformatör Modelinin Mimarisi

Standart metin-metin girdi-çıktı formatını inceledik. Şimdi, T5 transformatör modelinin mimarisine bakalım.

Python kodları bulunmamaktadır, eğer python kodları olsaydı satır satır açıklama verilecekti.

---

