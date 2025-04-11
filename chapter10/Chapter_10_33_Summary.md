# Tokenizasyonun Dönüştürücü Modeli Üzerindeki Etkisi

Bu bölümde, tokenizasyonun bir dönüştürücü modelinin sonraki katmanları üzerindeki etkisini ölçtük. Bir dönüştürücü modeli, yalnızca bir yığının embedding ve pozisyonel kodlama alt katmanlarından tokenlara dikkat edebilir. Modelin kodlayıcı-kod çözücü, yalnızca kodlayıcı veya yalnızca kod çözücü olması önemli değildir. Ayrıca, veri kümesinin eğitmek için yeterince iyi görünmesi de önemli değildir. Tokenizasyon işlemi kısmen bile olsa başarısız olursa, dönüştürücü modelimiz kritik tokenları kaçıracaktır.

İlk olarak, ham veri kümelerinin standart dil görevleri için bir dönüştürücü eğitmek için yeterli olabileceğini gördük. Ancak, önceden eğitilmiş bir tokenizör bir milyar kelime üzerinden geçmiş olsa bile, karşılaştığı kelime hazinesinin yalnızca küçük bir kısmıyla bir sözlük oluşturduğunu keşfettik. Bizim gibi, bir tokenizör öğrendiği dilin özünü yakalar ve yalnızca en önemli kelimeleri hatırlar, eğer bu kelimeler de sıkça kullanılırsa. Bu yaklaşım standart bir görev için iyi çalışır, ancak özel görevler ve kelime hazinesi ile ilgili sorunlar yaratır.

Standart tokenizörlerin sınırları etrafında çalışmak için birçok fikir arasından bazılarını araştırdık. İşlemek istediğimiz metni, bir tokenizörün nasıl düşündüğü ve verileri kodladığı gibi, bir dil kontrol yöntemi uyguladık. Daha sonra, metin dizilerinin nasıl cümlelere ve kelimelere ayrılabileceğini anlamak için cümle ve kelime tokenizörlerini araştırdık. Cümle tokenizasyonu ve düzenli ifade tokenizasyonu dahil olmak üzere çeşitli cümle ve kelime tokenizörlerini inceledik.

Cümle ve kelime tokenizörleri, bazı durumlarda dönüştürücü modeli eğitimi için veri kümelerini ön işlemek dahil olmak üzere birçok Doğal Dil İşleme (NLP) görevi için kullanışlıdır. Ancak, büyük ölçekli derlemlerde, dönüştürücünün eğitim sürecini yavaşlatacak büyük sözlükler üreteceklerdir. Bu nedenle, Unigram dil modeli tokenizasyonu, SentencePiece, BPE ve WordPiece gibi alt kelime tokenizörlerini araştırdık.

Token-ID eşlemelerini ayrıntılı olarak incelemek için WordPiece tokenizörlerine odaklandık. Tokenizasyonun becerisi, bilgiyi korumak ve hesaplama performansını optimize etmek arasında denge kurmayı gerektirir. Görevinize ve modelinize uygun bir yöntem seçmelisiniz. Bir projenin tokenizasyon aşaması tamamlandıktan sonra, embedding bir sonraki mantıksal adımdır.

Sonraki bölüm, "İnce Ayar yerine Alternatif olarak LLM Embedding'leri Kullanma", bizi embedding'lere ve aktarım öğrenmeye götürecektir.

Python kodları bulunmamaktadır, ancak tokenizasyon ile ilgili bazı kütüphaneler ve teknikler aşağıdaki gibidir:

*   SentencePiece: Metni alt kelimelere ayırmak için kullanılan bir kütüphanedir.
*   BPE (Byte Pair Encoding): Metni tokenize etmek için kullanılan bir algoritmadır.
*   WordPiece: Google'ın BERT modelinde kullandığı tokenizasyon yöntemidir.

Bu teknikler ve kütüphaneler, metni tokenize etmek ve NLP görevleri için hazırlamak için kullanılır.

---

