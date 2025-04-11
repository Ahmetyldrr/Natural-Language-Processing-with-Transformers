# BERT Hakkında Doğru/Yanlış Soruları

Aşağıdaki paragrafın birebir Türkçe çevirisi yapılmıştır.

BERT, Transformers'dan Bidirectional Encoder Representations'ın kısaltmasıdır. (Doğru/Yanlış) 
BERT, iki adımlı bir çerçevedir. 1. Adım ön eğitimdir (pretraining). 2. Adım ise ince ayardır (fine-tuning). (Doğru/Yanlış) 
Bir BERT modelini ince ayar yapmak, sıfırdan parametreleri eğitmek anlamına gelir. (Doğru/Yanlış) 
BERT, yalnızca tüm aşağı akış görevlerini kullanarak ön eğitim yapar. (Doğru/Yanlış) 
BERT, MLM ile ön eğitim yapar. (Doğru/Yanlış) 
BERT, NSP ile ön eğitim yapar. (Doğru/Yanlış) 
BERT, matematiksel fonksiyonlar üzerinde ön eğitim yapar. (Doğru/Yanlış) 
Soru-cevap görevi bir aşağı akış görevidir. (Doğru/Yanlış) 
Bir BERT ön eğitim modeli, tokenizasyon gerektirmez. (Doğru/Yanlış) 
Bir BERT modelini ince ayar yapmak, ön eğitim yapmaktan daha az zaman alır. (Doğru/Yanlış)

Paragraf çevirisi dışında Python kodları bulunmamaktadır. Eğer BERT ile ilgili Python kodları verilseydi, satır satır açıklamalar yapılabilirdi. Ancak bu metinde kod bulunmamaktadır.

BERT ile ilgili temel kavramlar:
- **BERT (Bidirectional Encoder Representations from Transformers)**: Transformers mimarisine dayanan çift yönlü kodlayıcı temsilleri.
- **Pretraining (Ön Eğitim)**: Modelin büyük bir veri seti üzerinde önceden eğitilmesi.
- **Fine-tuning (İnce Ayar)**: Önceden eğitilmiş modelin spesifik bir görev için daha küçük bir veri seti üzerinde eğitilmesi.
- **MLM (Masked Language Modeling)**: Bazı kelimelerin maskelendiği ve modelin bu kelimeleri tahmin etmeye çalıştığı bir ön eğitim yöntemi.
- **NSP (Next Sentence Prediction)**: İki cümlenin birbirini takip edip etmediğini tahmin etmeye dayanan bir ön eğitim yöntemi.
- **Tokenization**: Metni modelin işleyebileceği token adı verilen birimlere ayırma işlemi.
- **Downstream Task (Aşağı Akış Görevi)**: Önceden eğitilmiş bir modelin ince ayar yapılarak uygulanacağı spesifik görevler (örneğin, soru-cevap, duygu analizi).

---

