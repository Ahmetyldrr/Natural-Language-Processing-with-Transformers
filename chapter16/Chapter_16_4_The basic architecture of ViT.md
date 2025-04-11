# ViT'nin Görüntü İşleme Yöntemi
ViT, bir görüntüyü kelime yamaları olarak işleyebilir. Bu bölümde, süreci üç adımda inceleyeceğiz: 
Görüntüyü bir özellik çıkarıcı ile yamalara ayırma. 
Özellik çıkarıcı ile görüntü yamalarının bir sözlüğünü oluşturma. 
Yamalar, transformer encoder-only modelinin girdisi haline gelir.

# İşlem Adımları
Model, girdiyi gömme işlemine tabi tutar. 
Ham logitler çıktısı üretecektir, bu çıktı pipeline fonksiyonları tarafından son olasılıklara dönüştürülecektir. 
İlk adım, görüntüyü eşit büyüklükte yamalar halinde **BÖLME** işlemidir.

Python kodu bulunmamaktadır, sadece bir ingilizce paragrafın türkçeye çevirisi yapılmıştır.

Eğer bir python kodu olsaydı, satır satır açıklama aşağıdaki gibi olurdu:

Örneğin varsayımsal bir python kodu:
```python
# Görüntüyü yamalar halinde bölme
def split_image_into_patches(image, patch_size):
    # Görüntüyü yatay ve dikey olarak yamalar halinde bölme
    patches = []
    for i in range(0, image.shape[0], patch_size):
        for j in range(0, image.shape[1], patch_size):
            patch = image[i:i+patch_size, j:j+patch_size]
            patches.append(patch)
    return patches

# Özellik çıkarıcı kullanarak yamalardan sözlük oluşturma
def build_vocabulary(patches, feature_extractor):
    # Yamaları özellik çıkarıcı ile işleme
    features = []
    for patch in patches:
        feature = feature_extractor(patch)
        features.append(feature)
    return features

# Transformer encoder-only modelini kullanarak sınıflandırma yapma
def classify_image(patches, model):
    # Yamaları modele verme
    outputs = model(patches)
    return outputs
```
Satır satır açıklama:
1. `def split_image_into_patches(image, patch_size):` Görüntüyü yamalar halinde bölme fonksiyonu tanımı.
2. `patches = []` Yamaları saklamak için boş bir liste oluşturma.
3. `for i in range(0, image.shape[0], patch_size):` Görüntüyü yatay olarak yamalar halinde bölme döngüsü.
4. `for j in range(0, image.shape[1], patch_size):` Görüntüyü dikey olarak yamalar halinde bölme döngüsü.
5. `patch = image[i:i+patch_size, j:j+patch_size]` Bir yama oluşturma.
6. `patches.append(patch)` Yamayı listeye ekleme.
7. `return patches` Yamaları döndürme.

ve diğer fonksiyonlar için de benzer şekilde açıklama yapılabilir.

---

