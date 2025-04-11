# Görüntü İşlemede Kullanılan Kodun Ana Bölümleri
Bu bölümde, görme transformerlarının özel mimarisine ilişkin kodun ana bölümlerine odaklanacağız. İki ana bileşen vardır: Özellik çıkarıcı (Feature Extractor) ve Transformer.

Open `ViT_CLIP.ipynb` dosyasını, bu bölüm için GitHub deposunda bulabilirsiniz. Google Colab VM'leri, `torch` ve `torchvision` gibi önceden yüklenmiş birçok paket içerir. İlk hücredeki komutu açıklamayı kaldırarak ve `!pip list -v` komutunu çalıştırarak bunları görüntüleyebilirsiniz.

İlk olarak, ViT'yi göstermek için kullanacağımız bir görüntüyü indireceğiz:
```python
# Üretim aşamasına geçerken silinecek
!curl -L https://raw.githubusercontent.com/Denis2054/Transformers_3rd_Edition/master/Chapter16/generate_an_image_of_a_car_in_space.jpg --output "generate_an_image_of_a_car_in_space.jpg"
```
Bu komut, belirtilen URL'den bir görüntüyü indirir ve `generate_an_image_of_a_car_in_space.jpg` olarak kaydeder.

Daha sonra, notebook IPython modülünü görüntü oluşturma için içe aktarır ve görüntüyü indirir:
```python
from IPython.display import Image  # Bu, notebook'ta görüntü oluşturmak için kullanılır
```
Notebook daha sonra görüntüyü görüntüler:
```python
from PIL import Image  # Görüntü işleme için kullanılır

# Görüntünün yolu
image_path = "/content/generate_an_image_of_a_car_in_space.jpg"

# Görüntüyü aç
image = Image.open(image_path)
```
Görüntü, Şekil 16.5'te gösterildiği gibi, bir Generative AI Stable Diffusion modeli ile oluşturulmuş uzayda bir arabadır:
# Şekil 16.5: Telif Hakkı 2023 Denis Rothman: Görüntü, bir Stable Diffusion transformer tarafından oluşturuldu

Şimdi, işlem hattının bu önemli bileşenini anlamak için bir özellik çıkarıcı simülatörü oluşturalım.

---

