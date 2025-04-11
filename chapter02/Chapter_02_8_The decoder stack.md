# Transformer Modelinin Çözücü Katmanları

Transformer modelinin çözücü katmanları, kodlayıcı katmanları gibi katman yığınlarından oluşur. Çözücü yığınının her bir katmanı aşağıdaki yapıya sahiptir: 

Şekil 2.22: Transformer Çözücü Yığınının Bir Katmanı 
Transformer modelinin N = 6 katmanının tümü için çözücü katmanının yapısı kodlayıcı ile aynı kalır. Her bir katman üç alt katman içerir: çok başlı maskeli dikkat mekanizması, çok başlı dikkat mekanizması ve tamamen bağlı konum bazlı ileri beslemeli ağ. Çözücü, üçüncü ana alt katmana sahiptir, bu da maskeli çoklu dikkat mekanizmasıdır. Bu alt katman çıktısında, belirli bir konumda, sonraki kelimeler maskelenir, böylece Transformer, dizinin geri kalanını görmeden varsayımlarını çıkarır. Bu şekilde, bu modelde, dizinin gelecekteki bölümlerini göremez.

# Katman Normalizasyonu ve Artık Bağlantılar

Transformer modelindeki üç ana alt katmanın her birini, kodlayıcı yığında olduğu gibi, bir artık bağlantı, Sublayer(x), çevreler: 
LayerNormalization(x + Sublayer(x))

# Embedding Katmanı

Embedding katmanı alt katmanı, yalnızca yığının alt seviyesinde, kodlayıcı yığında olduğu gibi, mevcuttur. Çözücü yığınının her bir alt katmanının çıktısı, embedding katmanı ve artık bağlantıların çıktısı dahil olmak üzere, d_model gibi sabit bir boyuta sahiptir. 

Görüldüğü gibi, tasarımcılar simetrik kodlayıcı ve çözücü yığınları oluşturmak için çok çalıştılar. Her bir alt katmanın yapısı ve çözücünün işlevi kodlayıcıya benzer. Bu bölümde, gerektiğinde aynı işlevsellik için kodlayıcıya başvurabiliriz. Sadece çözücü ve kodlayıcı arasındaki farklılıklara odaklanacağız.

Python kodu içermiyor, sadece metin çevirisi yapıldı. Eğer bir kod snippet'i olsaydı, satır satır açıklama yapılacaktı. 

Örneğin, eğer `LayerNormalization(x + Sublayer(x))` kodu için açıklama yapılsaydı, şöyle olacaktı:

```python
# LayerNormalization: Katman normalizasyonu uygular
# x: Girdi vektörü
# Sublayer(x): Alt katman fonksiyonu
LayerNormalization(x + Sublayer(x)) 
# Burada, x ve Sublayer(x) toplanır ve ardından katman normalizasyonu uygulanır.
```

---

