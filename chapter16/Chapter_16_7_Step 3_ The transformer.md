# Görüntü Dizilerini Transformer'a Uyarlama

Kelime benzeri görüntü dizileri bir transformer'a sığabilir. Sorun şu ki, onlar hala görüntüdür! Google Research, Şekil 16.4'te gösterildiği gibi, hibrit bir girdi modelinin işe yarayacağına karar verdi: 
Yamaları gömmek için bir evrişimli ağ ekleyin. 
Orijinal görüntünün yapısını korumak için konumsal kodlama ekleyin. 
Daha sonra, gömülü girdiyi standart bir orijinal BERT benzeri kodlayıcı ile işleyin. 
Son olarak, transformer, bir örnekleyicinin etiket lojitslerine uyan olasılıklara dönüştüreceği ham lojits çıktısı üretir. Sonuç bir etiket olacaktır.

# Şekil 16.4: Hibrit Girdi Altkatmanı ve Standart Kodlayıcı

Google Research, bir NLP transformer modelini bir görüntü transformer'ına dönüştürmenin akıllıca bir yolunu buldu. Modelin mimarisinin Orijinal Transformer (Vaswani ve diğerleri, 2017) ile çok yakından takip ettiği görülmektedir. 
ViT mimarisinin avantajları ve faydaları üç noktada özetlenebilir:
- ViT mimarisi, Orijinal Transformer modelinin ölçekleme yeteneklerini devralır. 
- ViT mimarisi böylece uzun vadeli bağımlılıkları evrişimli sinir ağı (CNN)-sadece mimarilerden daha iyi bir şekilde yakalar. 
- ViT, dikkat katmanlarındaki tüm yamalar arasındaki ilişkiyi öğrenecek ve daha doğru tahminler sağlayacaktır.

Şimdi, bir Hugging Face örnek görüntü transformer'ını kodda uygulayalım.

Python kodu bulunmamaktadır, eğer uygulama kısmında kod örneği verilirse satır satır açıklayabilirim.

---

