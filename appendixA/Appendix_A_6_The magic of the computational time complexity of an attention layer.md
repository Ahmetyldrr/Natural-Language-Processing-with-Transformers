# Dikkat Katmanı ve Zaman Karmaşıklığı

Dikkat katmanı, O(1) bellek zaman karmaşıklığından yararlanır. Bu, her bir kelime arasındaki nokta çarpımını gerçekleştirmek için O(n^2 * d) hesaplama zaman karmaşıklığını sağlar. Makine öğreniminde, bu, her bir kelimenin temsilini (d) başka bir kelimeyle çarpmak anlamına gelir. Böylece bir dikkat katmanı, tüm ilişkileri tek bir matris çarpımı ile öğrenebilir! O(n * d^2) hesaplama zaman karmaşıklığına sahip bir tekrarlayan katman, O(n) doğrusal, sıralı süreci tarafından engellenir. Dikkat katmanıyla aynı görevi gerçekleştirmek daha fazla işlem gerektirir. Şimdi, bu teoriyi pratikte görmek için Python, PyTorch ve TensorFlow not defterinde dikkat zaman karmaşıklığı modelini ve tekrarlayan zaman karmaşıklığı modelini simüle edeceğiz. Hesaplamalar kavramsaldır. Bu bölümde merkezi işlem birimi (CPU), grafik işlem birimi (GPU) ve tensor işlem birimi (TPU) ile simülasyonlar çalıştıracağız:

## İşlem Birimleri

*   **CPU**: Bu, bir bilgisayarın birincil bileşenidir.
*   **GPU**: Bir GPU, özel bir işlem birimidir. İlk olarak 3D görüntü oluşturma için kullanılan GPU'lar, matris çarpımları gibi makine öğrenimi görevlerini gerçekleştirmek için evrimleşmiştir.
*   **TPU**: TPU, Google tarafından geliştirilen ve TensorFlow için optimize edilen bir makine öğrenimi iş yükü işlemcisini hızlandıran bir işlem birimidir.

Depo dizinindeki Chapter01 klasöründe bulunan `O-1_and_Accelerators.ipynb` dosyasını açın. CPU'larla başlayacağız.

Aşağıda python kodları bulunmamaktadır, eğer python kodlarını açıklayacaksanız kodları paylaşmanız gerekmektedir.

---

