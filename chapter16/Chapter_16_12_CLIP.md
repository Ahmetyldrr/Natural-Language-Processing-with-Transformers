# Contrastive Language-Image Pre-Training (CLIP) Nedir?

Contrastive Language-Image Pre-Training (CLIP), görüntü sınıflandırma için kullanılabilen çok modlu bir transformatördür. CLIP'in süreci aşağıdaki gibi özetlenebilir: ViT gibi bir özellik çıkarıcı, görüntü tokenleri üretir. Metin de ViT'de olduğu gibi tokenler halinde girdidir. Dikkat katmanı, görüntü tokenleri ve metin tokenleri arasındaki ilişkileri bir tür "çapraz dikkat" ile öğrenir. Çıktı da ViT'de olduğu gibi ham logittir. CLIP'i kodda çalıştırmadan önce CLIP'in temel mimarisine göz atacağız.

Not: Python kodları bulunmamaktadır, sadece ingilizce paragrafın türkçeye birebir çevirisi yapılmıştır.

Eğer ilgili python kodları verilseydi, satır satır açıklamalar yapilacaktı. Örnek bir CLIP kodu aşağıdaki gibidir:

```python
import torch
import clip

# CLIP modelini yükleme
device = "cuda" if torch.cuda.is_available() else "cpu"
model, preprocess = clip.load("ViT-B/32", device=device)

# Burada model ve preprocess değişkenleri CLIP modelini ve görüntü ön işleme fonksiyonunu içerir.
```

# Açıklamalar:

1. `import torch`: PyTorch kütüphanesini içe aktarır.
2. `import clip`: CLIP kütüphanesini içe aktarır.
3. `device = "cuda" if torch.cuda.is_available() else "cpu"`: Cuda kullanılabilir ise "cuda" değilse "cpu" ataması yapar.
4. `model, preprocess = clip.load("ViT-B/32", device=device)`: CLIP modelini belirtilen cihazda yükler ve model ile ön işleme fonksiyonunu döndürür. 

Bu şekilde her satır için açıklama yapılabilir.

---

