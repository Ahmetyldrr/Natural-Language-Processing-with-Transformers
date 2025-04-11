# Stability AI ve Stable Diffusion'a Giriş
Stability AI, Generative AI alanında liderdir. Hızla büyüyen AI projelerinden biri olan Stable Diffusion'ı ürettiler. Bu bölüm sizi Stable Diffusion'ın ön saflarında gezdiriyor. Başlamak için, bir API anahtarı almanız ve kaydolmanız gerekir: https://platform.stability.ai/docs/getting-started/python-sdk. Stable Diffusion modelini çalıştırmadan önce fiyatlandırma politikasını kontrol edin.

# Stable Diffusion'ı Kurma ve Çalıştırma
Open Stable _Vision_Stability_AI.ipynb dosyasını açın. İlk olarak SDK'yı kurarız:
```python
!pip install stability-sdk
```
Ardından Stability modüllerini klonlarız:
```python
!git clone --recurse-submodules https://github.com/Stability-AI/stability-sdk
```
Stability API sunucusuna bağlanmak için Stability host'unu ve anahtarımızı tanımlarız, ya da isteği yaparken tanımlarız:
```bash
!export STABILITY_HOST=grpc.stability.ai:443
#!export STABILITY_KEY=[YOUR_KEY]
```
Şimdi Stability'den aşağıdaki isteme dayalı bir resim oluşturmasını isteyebiliriz:
```bash
!python -m stability_sdk generate "A stunning spaceship with stars as lights and fantastic buildings inside."
```
Eğer API anahtarınızı isteğe dahil etmediyseniz veya anahtar dikkate alınmadıysa, anahtarı girmeniz istenecektir (bir veya iki kez):
```
Please enter your API key from dreamstudio.ai or set the STABILITY_KEY environment variable to skip this prompt.
Enter your Stability API key:[YOUR_KEY]
```
API anahtarınızı birden fazla kez girdiğinizde yeni bir resim elde edeceksiniz.

# Oluşturulan Resmi Görüntüleme
Resim oluşturulduktan sonra, onu görüntüleyebiliriz:
```python
import os
from IPython.display import display, Image

for file_name in os.listdir('/content'):
    if file_name.endswith('.png'):
        display(Image(filename=os.path.join('/content', file_name)))
```
Çıktı, her zamanki gibi diffusion modelleriyle çarpıcıdır:
## Figure 17.5: Stable Diffusion tarafından oluşturulan bir uzay gemisi resmi

# Stability AI'nın Daha Fazlasını Keşfetme
Stability AI'nın daha fazlasını keşfetmeye devam edelim! Stable Diffusion'dan bir DAT gerçekleştirmesini isteyelim.

---

