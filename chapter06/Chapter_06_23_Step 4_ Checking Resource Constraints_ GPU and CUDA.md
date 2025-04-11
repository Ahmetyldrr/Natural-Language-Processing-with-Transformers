# PyTorch için Modelin Ön Eğitimi İçin GPU Gereksinimi

Bu modeli PyTorch için ön eğitimi için bir GPU'ya ihtiyacımız var. Bir GPU'yu etkinleştirdiğinizden emin olun ve ardından aşağıdaki kod ile sisteminizi kontrol edin: 
```python
!nvidia-smi
```
Çıktının aşağıdaki alıntısında bir GPU görmelisiniz:
```
NVIDIA-SMI 525.105.17   Driver Version: 525.105.17   CUDA Version: 12.0
```
Ayrıca, PyTorch'un CUDA'yı gördüğünden emin olun:
## PyTorch'un CUDA'yı Görüp Görmediğini Kontrol Etme
```python
#@title Checking that PyTorch Sees CUDA 
import torch
torch.cuda.is_available()
```
Bu kodun çıktısı aşağıdaki gibi olmalıdır:
```
True
```
Satır satır açıklama:

1. `!nvidia-smi`: Bu komut, sistemde yüklü olan NVIDIA GPU'nun sürücü bilgilerini ve özelliklerini gösterir. `!` işareti, Jupyter Notebook veya benzeri bir ortamda komutun işletim sistemi komutu olarak çalıştırılması gerektiğini belirtir.

2. `import torch`: PyTorch kütüphanesini Python ortamına import eder. PyTorch, derin öğrenme modelleri geliştirmek için kullanılan popüler bir kütüphanedir.

3. `torch.cuda.is_available()`: Bu fonksiyon, sistemde CUDA'nın (NVIDIA tarafından geliştirilen bir paralel hesaplama platformu ve programlama modeli) kullanılabilir olup olmadığını kontrol eder. CUDA, PyTorch'un GPU üzerinde çalışabilmesi için gereklidir. Eğer CUDA kullanılabilirse, bu fonksiyon `True` döndürür.

---

