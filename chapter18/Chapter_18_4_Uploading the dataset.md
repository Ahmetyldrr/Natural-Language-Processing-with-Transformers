# İlk olarak, Şekil 18.2'de gösterildiği gibi Eğitim Dosyası(ları) Yükle'ye tıklayın
Şekil 18.2: Eğitim veri kümesini yükleme 
Arayüz gelişebilir, ancak veri yüklemeniz gerekecek. Verilerinizi hazırlamak için Hugging Face platformundaki belgeleri dikkatlice okumanız gerekecek. Arayüz, son teknoloji AI pazarını takip etmek için sürekli olarak gelişiyor. Yönteminizi seçin, ancak görev üzerinde odaklanın: veri yükleme. Hugging Face'ın veri biçimlendirme prosedürlerini takip etmeniz gerekecek: https://huggingface.co/docs/autotrain/image_classification . Güncellemeleri düzenli olarak okuduğunuzdan emin olun. Yine de buna değer! 
Bu durumda, Şekil 18.3'teki alıntılarda gösterildiği gibi CIFAR-10 resimlerini yüklüyoruz: 
Şekil 18.3: CIFAR-10 taşıma resimlerinin alıntısı 
Bu bölümdeki CIFAR-10 resimleri "Learning Multiple Layers of Features from Tiny Images" , Alex Krizhevsky , 2009: https://www.cs.toronto.edu/~kriz/learning-features-2009-TR.pdf kaynağından alınmıştır. Bunlar CIFAR-10 ve CIFAR-100 veri kümelerinin bir parçasıdır (toronto.edu): https://www.cs.toronto.edu/~kriz/cifar.html . 
Dört sınıfa ayrılan 8.941 resim üzerinde eğitim yapacağız: uçak, otomobil, gemi ve kamyon. Veri kümesini eğitim ve doğrulama resimlerine ayırmamız gerekecek. Doğrulama dosyaları hazır olduktan sonra, Şekil 18.4'te gösterildiği gibi Doğrulama Verileri (isteğe bağlı) üzerine tıklayın: 
Şekil 18.4: Doğrulama dosyalarını yükleme 
Dosyalar hazır olduktan sonra, Şekil 18.5'te gösterildiği gibi bir Görev ve bir Temel Model seçmeliyiz: 
Şekil 18.5: Bir Görev ve Temel Model seçme 
Bir LLM görevi veya bir vizyon görevi seçebilirsiniz. Bu durumda, Şekil 18.6'da gösterildiği gibi Görüntü Sınıflandırma'yı seçtik: 
Şekil 18.6: Bir görev seçme 
Birkaç Hugging Face modeli arasından bir Temel Model seçebilirsiniz (bkz. Şekil 18.7): 
Şekil 18.7: Bir temel model seçme 
Bu durumda, görevi Görüntü Sınıflandırma olarak ve eğitmek istediğimiz ilk modeli, örneğin google/vit-base-patch16-224 olarak seçiyoruz. Arayüz gelişebilir, ancak her zaman bir eğitim işi çalıştırmadan önce verileri hazırlamamız ve bir görev ve model seçmemiz gerekecek. 
Her şey yolunda görünüyor. Bir dakika! Veri kümesi nasıl hazırlandı?

Python kodları bulunmamaktadır. 

Eğer ingilizce metinde kod var ise belirtirdim ve kodları satır satır açıklardım. 

Ancak, ingilizce metinde bazı linkler ve referanslar bulunmaktadır. Bunlar:
- https://huggingface.co/docs/autotrain/image_classification 
- https://www.cs.toronto.edu/~kriz/learning-features-2009-TR.pdf 
- https://www.cs.toronto.edu/~kriz/cifar.html 

Bu linkler sırasıyla Hugging Face'ın veri biçimlendirme prosedürleri, CIFAR-10 veri kümesinin kaynakları ve CIFAR-10 ve CIFAR-100 veri kümeleri hakkında bilgi içermektedir.

---

