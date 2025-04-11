# İlk olarak, Stability AI'a kaydolduğunuzdan ve API anahtarınızın olduğundan emin olun: https://platform.stability.ai/docs/features/animation

Şimdi animasyonlar için Stability SDK'yı kuracağız: 
```python
!pip install "stability_sdk[anim_ui]"  # Animasyon SDK'sını kur
!git clone --recurse-submodules https://github.com/Stability-AI/stability-sdk  # stability-sdk deposunu klonla
```
API'ı içe aktarıyoruz ve host'u başlatıyoruz. Ayrıca API anahtarımızı belirliyoruz:
```python
from stability_sdk import api
STABILITY_HOST = "grpc.stability.ai:443"  # Stability AI host'u
STABILITY_KEY = [BURAYA ANAHTARINIZI GİRİN]  # API anahtarınız
context = api.Context(STABILITY_HOST, STABILITY_KEY)  # API context'i oluştur
```
Şimdi modülleri içe aktarıyoruz ve parametreleri yapılandırıyoruz. Aşağıdaki kod, varsayılan Stability AI argümanlarını kullanıyor:
```python
from stability_sdk.animation import AnimationArgs, Animator  # AnimationArgs ve Animator sınıflarını içe aktar

# Animasyon argümanlarını yapılandır
args = AnimationArgs()
args.interpolate_prompts = True  # Prompt'ları çerçeveler arasında enterpolasyon yap
args.locked_seed = True  # Seed'i kilitle, deterministik animasyon oluştur
args.max_frames = 48  # Maksimum çerçeve sayısı
args.seed = 42  # Rastgele seed
args.strength_curve = "0:(0)"  # Difüzyon eğrisinin gücünü belirt
args.diffusion_cadence_curve = "0:(4)"  # Difüzyon eğrisinin kadansını belirt
args.cadence_interp = "film"  # Kadans enterpolasyon yöntemini belirt
```
Varsayılan argümanlar:
- `args = AnimationArgs()`: AnimationArgs sınıfının bir örneğini oluşturur. Bu nesne, animasyonu yapılandırmak için kullanılır.
- `args.interpolate_prompts = True`: Prompt'ları çerçeveler arasında enterpolasyon yapar.
- `args.locked_seed = True`: Seed'i kilitler, deterministik animasyon oluşturur.
- `args.max_frames = 48`: Maksimum çerçeve sayısını 48 olarak belirler.
- `args.seed = 42`: Rastgele seed'i 42 olarak belirler.
- `args.strength_curve = "0:(0)"`: Difüzyon eğrisinin gücünü belirtir.
- `args.diffusion_cadence_curve = "0:(4)"`: Difüzyon eğrisinin kadansını belirtir.
- `args.cadence_interp = "film"`: Kadans enterpolasyon yöntemini "film" olarak belirtir.

Şimdi animasyon için başlangıç ve bitiş resimlerinin metnini tanımlıyoruz:
```python
animation_prompts = {
    0: "fantastik bir uzay gemisinin fotoğrafı",
    24: "fantastik bir ay iniş modülünün fotoğrafı",
}

negative_prompt = ""  # Görmek istemediğiniz şeyleri negative prompt'a ekleyebilirsiniz. Örneğin: negative_prompt = "kamyonlar, bulutlar, Dünya"
```
Şimdi animator nesnesini oluşturuyoruz:
```python
# Animator nesnesini oluştur
animator = Animator(
    api_context=context,
    animation_prompts=animation_prompts,
    negative_prompt=negative_prompt,
    args=args
)
```
Oluşturulan her çerçeveyi kaydediyoruz:
```python
# Animasyonun her bir çerçevesini render et
for idx, frame in enumerate(animator.render()):
    frame.save(f"frame_{idx:05d}.png")  # Çerçeveyi PNG olarak kaydet
```
Animator nesnesi şimdi animasyon çerçevelerini oluşturuyor ve ardından bir video oluşturuyor:
```python
from stability_sdk.utils import create_video_from_frames
from tqdm import tqdm

# Animator nesnesini oluştur
animator = Animator(
    api_context=api.Context(STABILITY_HOST, STABILITY_KEY),
    animation_prompts=animation_prompts,
    negative_prompt=negative_prompt,
    args=args,
    out_dir="video_01"  # Çıktı dizini
)

# Animasyon çerçevelerini render et
for _ in tqdm(animator.render(), total=args.max_frames):
    pass

# Çerçevelerden video oluştur
create_video_from_frames(animator.out_dir, "video.mp4", fps=24)
```
Daha sonra videoyu görüntüleyebiliriz:
```python
from IPython.display import display, Video

# Videoyu görüntüle
display(Video("/content/video.mp4", embed=True))
```
Çıktı etkileyici ve potansiyel sınırsız! 

# Kararlı Difüzyon ile oluşturulan bir uzay gemisi videosu

Animasyonu not defterinde çalıştırabilirsiniz. Üretilen örnek animasyonlardan birini aşağıdaki bağlantıdan indirebilirsiniz: https://github.com/Denis2054/Transformers-for-NLP-and-Computer-Vision-3rd-Edition/blob/main/Chapter17/Stability_Animation.mp4.

Şimdi metinden videoya sentezini çalıştıracağız.

---

