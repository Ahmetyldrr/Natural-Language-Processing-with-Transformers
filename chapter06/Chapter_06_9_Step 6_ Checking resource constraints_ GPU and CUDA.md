# KantaiBERT'in Çalıştırılması ve GPU Kontrolü

KantaiBERT, Grafik İşleme Birimi (GPU) ile en uygun hızda çalışır. Öncelikle bir NVIDIA GPU kartının var olup olmadığını kontrol etmek için bir komut çalıştıracağız: `!nvidia-smi`

Çıktı, çalıştığınız makineye bağlı olarak kart üzerindeki bilgi ve sürümünü gösterir. Bu durumda, Tesla V100-SXM2 idi: 
Şekil 6.3: NVIDIA kart bilgisi 
Çıktı, her Google Colab VM yapılandırmasıyla değişebilir. Şimdi PyTorch'un CUDA'yı gördüğünden emin olmak için kontrol edeceğiz:

```python
import torch
torch.cuda.is_available()
```

 Sonuç `True` olmalıdır: `True`

Hesaplama Birleştirilmiş Cihaz Mimarisi (CUDA), NVIDIA tarafından GPU'larının paralel hesaplama gücünü kullanmak için geliştirilmiştir. Şimdi modelin yapılandırmasını tanımlamaya hazırız.

**Python Kodlarının Açıklaması**

1. `import torch` : 
   - Bu satır, PyTorch kütüphanesini içe aktarır. PyTorch, derin öğrenme modelleri oluşturmak ve eğitmek için kullanılan popüler bir kütüphanedir.

2. `torch.cuda.is_available()` : 
   - Bu fonksiyon, CUDA'nın mevcut olup olmadığını kontrol eder. CUDA, NVIDIA GPU'larında çalışan uygulamalar geliştirmek için kullanılan bir platformdur.
   - Eğer bir NVIDIA GPU'su varsa ve doğru şekilde yapılandırılmışsa, bu fonksiyon `True` döndürür. Aksi takdirde `False` döndürür.

Bu kodlar, KantaiBERT modelini çalıştırmak için gerekli olan GPU ve CUDA yapılandırmasının doğru şekilde yapılıp yapılmadığını kontrol etmek için kullanılır.

---

