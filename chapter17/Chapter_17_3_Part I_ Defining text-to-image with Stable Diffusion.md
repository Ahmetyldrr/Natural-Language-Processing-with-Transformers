# Stable Diffusion'ın Keras Sürümünün İncelenmesi

Şekil 17.2'de gösterildiği gibi, Keras sürümünün ana Python dosyalarını çok düşük bir seviyede inceleyeceğiz. Tam kod şu adreste bulunabilir: https://github.com/keras-team/keras-cv/tree/master/keras_cv/models/stable_diffusion : 

# Şekil 17.2: Stable Diffusion, Keras Uygulaması

Şekil 17.2, keşfedeceğimiz kodun Stable Diffusion mimarisini göstermektedir ve beş aşamada özetlenebilir:
- Metin yerleştirme (Text embedding)
- Rastgele görüntü oluşturma (Random image creation)
- Stable Diffusion altörnekleme (Stable Diffusion downsampling)
- Kod çözücü üstörnekleme (Decoder upsampling)
- Çıktı görüntüsü (Output image)

Keras Stable Diffusion kodu kendisi sadece 500 satır uzunluğundadır! 
Her fonksiyonun işlevini açıklayacağız, yüksek seviyeli matematiksel bir temsil yapacağız ve süreci yürüten Python sınıflarını bulacağız. Analizi, ustaca kompakt kod yaklaşımını gösteren bir Keras not defterini çalıştırarak sonlandıracağız.

Python kodları bulunmamaktadır, sadece ingilizce paragrafın türkçe çevirisi yapılmıştır.

---

