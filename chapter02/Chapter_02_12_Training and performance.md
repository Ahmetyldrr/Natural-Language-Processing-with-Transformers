# Orijinal Transformer Modelinin Eğitimi

Orijinal Transformer, 4.5 milyon cümle çiftinden oluşan İngilizce-Almanca veri seti ve 36 milyon cümle çiftinden oluşan İngilizce-Fransızca veri seti üzerinde eğitilmiştir. Veri setleri, Makine Çevirisi üzerine yapılan Dokuzuncu Çalıştay'dan (WMT) gelmektedir ve WMT veri setlerini keşfetmek isterseniz aşağıdaki bağlantıda bulunabilir: http://www.statmt.org/wmt14/. Orijinal Transformer temel modellerinin eğitimi, 8 NVIDIA P100 GPU'lu bir makinede 100.000 adım için 12 saat sürdü. Büyük modeller 300.000 adım için 3,5 gün sürdü.

# Orijinal Transformer Modelinin Başarısı

Orijinal Transformer, BLEU skoru 41,8 ile önceki tüm makine çevirisi modellerini geride bıraktı. Sonuç, WMT İngilizce-Fransızca veri setinde elde edildi. BLEU, Çift Dilli Değerlendirme Çalışması anlamına gelir. Makine çeviri sonuçlarının kalitesini değerlendiren bir algoritmadır.

# Optimizasyon Stratejileri

Google Araştırma ve Google Brain ekibi, Transformer'ın performansını artırmak için optimizasyon stratejileri uyguladı. Örneğin, Adam optimizasyon algoritması kullanıldı, ancak öğrenme oranı önce doğrusal bir oranla ısınma durumlarından geçerek değişti ve daha sonra azaldı. Gömmelerin toplamlarına artık dropout ve dropout gibi farklı düzenleme teknikleri uygulandı. Ayrıca, Transformer, aşırı güvenilir one-hot çıktılarıyla aşırı uyuma önlemek için etiket yumuşatma uygular. Daha az doğru değerlendirmeler sunar ve modelin daha fazla ve daha iyi eğitim yapmasını sağlar.

# Transformer Modelinin Varyasyonları

Diğer birkaç transformer model varyasyonu, sonraki bölümlerde keşfedeceğimiz diğer modellere ve kullanımlara yol açmıştır. Bölümün sonuna gelmeden önce, örneğin Hugging Face'de kullanıma hazır transformer modellerinin basitliğini hissedelim.

Python kodları bulunmamaktadır, ancak BLEU skorunun hesaplanması için kullanılan NLTK kütüphanesindeki `bleu_score` fonksiyonu gibi bir kod örneği aşağıdaki gibi olabilir:

```python
import nltk.translate.bleu_score as bleu

# Referans çeviriler
references = [["Bu", "bir", "referans", "çeviridir"], ["Bu", "başka", "bir", "referans", "çeviridir"]]

# Tahmin edilen çeviri
hypothesis = ["Bu", "bir", "tahmin", "çeviridir"]

# BLEU skorunun hesaplanması
score = bleu.sentence_bleu(references, hypothesis)

print("BLEU Skoru:", score)
```

Bu kod örneğinde:

1. `nltk.translate.bleu_score` modülü içe aktarılır.
2. Referans çeviriler ve tahmin edilen çeviri tanımlanır.
3. `bleu.sentence_bleu` fonksiyonu kullanılarak BLEU skoru hesaplanır.
4. BLEU skoru yazdırılır.

---

