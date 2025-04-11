# Kodun İlk Bölümü

Kodun ilk kısmı, gerekli kütüphaneleri kurar ve PyAv kullanarak videoyu okumak, frame örneklerini çıkarmak ve TimeSformer için bir liste içinde saklamak için bir fonksiyon oluşturur.

İlk olarak, transformerları kurarız: 
```python
!pip install transformers
```
Şimdi, FFmpeg'in multimedya kütüphaneleri için PyAv arayüzünü kurarız, böylece Python'da FFmpeg'i kontrol edebiliriz: 
```python
!pip install av
```
Videoyu görüntülemek ve Hugging Face Hub'ı kullanmak için gerekli modülleri içe aktarırız: 
```python
from IPython.display import HTML
from base64 import b64encode
from huggingface_hub import hf_hub_download
```
Şimdi, hedef videoyu Hugging Face Hub'dan indirir ve okuruz: 
```python
file_path = hf_hub_download(repo_id="nielsr/video-demo", filename="eating_spaghetti.mp4", repo_type="dataset")
# Videoyu aç
with open(file_path, 'rb') as f:
    video_data = f.read()
```
Kodun çalıştığını doğrulamak için videoyu görüntüleriz: 
```python
# Videoyu görüntüle
HTML("""
<video width="320" height="240" controls>
  <source src="data:video/mp4;base64,{0}" type="video/mp4">
</video>
""".format(b64encode(video_data).decode()))
```

# TimeSformer Modelinin Tanımlanması

Şimdi, notebook TimeSformer'ı model olarak tanımlar: 
```python
from transformers import TimesformerConfig, TimesformerModel

# TimeSformer timesformer-base stil konfigürasyonunu başlatma
configuration = TimesformerConfig()
# Konfigürasyondan bir model başlatma
model = TimesformerModel(configuration)
# Model konfigürasyonuna erişme
configuration = model.config
```

# Sınıflandırma Modüllerinin İçe Aktarılması

Sınıflandırma modüllerini içe aktarır ve rastgele bir tohum etkinleştiririz: 
```python
import av
import torch
import numpy as np
from transformers import AutoImageProcessor, TimesformerForVideoClassification
from huggingface_hub import hf_hub_download

np.random.seed(0)
```
Rastgele tohumun 0'a ayarlanması, deneyin her seferinde yeniden üretilmesini sağlar.

# PyAv ile Video Kod Çözme

Şimdi, PyAv ile videoyu kod çözmek ve her bir frame'i frame listesinde saklamak için bir fonksiyon tanımlarız. Frame listesi, videoyu kod çözdükçe frame frame eklenir: 
```python
def read_video_pyav(container, indices):
    '''
    PyAV kod çözücü ile videoyu kod çözme.

    Args:
    container (`av.container.input.InputContainer`): PyAV konteyner.
    indices (`List[int]`): Kod çözülecek frame indeksleri listesi.

    Returns:
    result (np.ndarray): (num_frames, height, width, 3) şeklinde kod çözülmüş frame'lerin np dizisi.
    '''
    frames = []
    container.seek(0)
    start_index = indices[0]
    end_index = indices[-1]
    for i, frame in enumerate(container.decode(video=0)):
        if i > end_index:
            break
        if i >= start_index and i in indices:
            frames.append(frame)
    return np.stack([x.to_ndarray(format="rgb24") for x in frames])
```

# Frame Örnekleme Fonksiyonu

Saniyede belirli sayıda frame örneklemek için bir örnekleme fonksiyonuna ihtiyacımız var, örneğin, videonun uzunluğu için: 
```python
def sample_frame_indices(clip_len, frame_sample_rate, seg_len):
    converted_len = int(clip_len * frame_sample_rate)
    end_idx = np.random.randint(converted_len, seg_len)
    start_idx = end_idx - converted_len
    indices = np.linspace(start_idx, end_idx, num=clip_len)
    indices = np.clip(indices, start_idx, end_idx - 1).astype(np.int64)
    return indices
```

# Video Klibi İçin Frame Örnekleme

Video klibi 10 saniyelik 30 frame/sn'den oluşur: 
```python
# Video klibi 300 frame'den oluşur (30 FPS'de 10 saniye)
file_path = hf_hub_download(repo_id="nielsr/video-demo", filename="eating_spaghetti.mp4", repo_type="dataset")
container = av.open(file_path)
```
Şimdi, 8 frame örnekleriz: 
```python
# 8 frame örnekle
indices = sample_frame_indices(clip_len=8, frame_sample_rate=1, seg_len=container.streams.video[0].frames)
video = read_video_pyav(container, indices)
```
Program, 10 saniyelik bir klibin 8 saniyelik kısmını, clip_len=8, 1 örnekleme oranıyla, frame_sample_rate=1, yani toplam 8 frame seçer.

---

