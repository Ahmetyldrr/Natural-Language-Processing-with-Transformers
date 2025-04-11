# Torch için CUDA Kullanımının Belirtilmesi

Şimdi, torch'un çoklu baş dikkat modelimiz için NVIDIA kartın paralel hesaplama gücünü kullanmak üzere Compute Unified Device Architecture (CUDA) kullandığını belirtelim: 
```python
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
```
Bu kod satırında:
- `torch.device()`: Torch'un hangi cihazı kullanacağını belirtmek için kullanılır.
- `"cuda" if torch.cuda.is_available() else "cpu"`: Eğer sistemde CUDA destekli bir NVIDIA kart varsa ve `torch.cuda.is_available()` fonksiyonu `True` döndürürse, `"cuda"` string'i döndürülür, aksi takdirde `"cpu"` string'i döndürülür. Yani eğer CUDA kullanılabilirse, Torch işlemleri GPU'da yapılır, yoksa CPU'da yapılır.

```python
!nvidia-smi
```
Bu komut:
- `!`: Google Colab gibi Jupyter tabanlı ortamlarda sistem komutlarını çalıştırmak için kullanılır.
- `nvidia-smi`: NVIDIA kartın durumunu, özelliklerini ve kullanımını gösteren bir komuttur. Bu komut NVIDIA kartın modelini, sürücüsünü, sıcaklığını, hafıza kullanımını ve daha fazlasını gösterir.

Çıktı, Google Colab konfigürasyonlarına göre değişebilir. Örneğin: 
# NVIDIA-SMI Çıktısı

Şimdi veri setini yükleyeceğiz.

---

