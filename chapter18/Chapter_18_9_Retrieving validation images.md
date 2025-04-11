# Notebook İlk Aşama: IPython İçe Aktarma ve Resim İşleme

Notebook ilk olarak medya işleme için IPython'u içe aktarır: 
```python
from IPython.display import Image
```
# Bu, notebook'ta resimlerin işlenmesi için kullanılır

İlk resim nispeten kolay sınıflandırılır: `generate_an_image_of_a_car_in_space.jpg`. Şimdi indireceğimiz bu resim, 16. Bölüm'de, "Beyond Text: Vision Transformers in the Dawn of Revolutionary AI" başlıklı bölümde, bir vizyon transformatörü tarafından sınıflandırıldı:

# Geliştirme erişimi, üretim aşamasına geçerken silinecek!
```bash
!curl -L https://raw.githubusercontent.com/Denis2054/Transformers_3rd_Edition/master/Chapter16/generate_an_image_of_a_car_in_space.jpg --output "generate_an_image_of_a_car_in_space.jpg"
```
Program şimdi resmi görüntüler:
```python
from PIL import Image

# Resminizin yolu tanımlanır
image_path = "/content/generate_an_image_of_a_car_in_space.jpg"

# Resim açılır
image = Image.open(image_path)
image
```
Çıktı, resmin nispeten kolay sınıflandırıldığını doğrular: 
# Şekil 18.14: Stable Diffusion modeli tarafından üretilen uzaydaki araba. Telif hakkı 2023, Denis Rothman

Şimdi sınıflandırmak için zor bir resim indiriyoruz:
# Geliştirme erişimi, üretim aşamasına geçerken silinecek!
```bash
!curl -L https://raw.githubusercontent.com/Denis2054/Transformers_3rd_Edition/master/Chapter18/car_in_fog.png --output "car_in_fog.png"
```
Resim, sisli bir gecede bir araba içerir, aşağıdaki gibi görüntülenir:
```python
image_path = "car_in_fog.png"
image = Image.open(image_path)
image
```
# Bir insan, `car_in_fog.png` resminde araçları tespit edebilir. Bir makine, çıkarımlamayı zor bulur ve genellikle resmin sınıflandırılmasında başarısız olur. Bir AI uzmanı olmayan bir profesyonel, çözümler bulmak için bir AI uzmanına ihtiyaç duyacaktır: 
# Şekil 18.15: Midjourney'e gönderilen bir istem tarafından üretilen sis içindeki araba. Telif hakkı 2023, Denis Rothman

Gerçek hayatta, resimler her zaman kolayca sınıflandırılmaz! İnsan sürücüler karanlık, sis, pus ve diğer elverişsiz koşullarla yüzleşmek zorundadır. Kendi kendine giden arabalar da olumsuz durumlarda zorluklarla karşılaşır - örneğin, radyo frekanslı radarlar yağmur, sis ve kar koşullarında arızalanır. İnsanlar, yolda iki araç olduğunu, bunlardan birinin orta şeritte olduğunu nispeten kolay bir şekilde tespit edebilir.

---

