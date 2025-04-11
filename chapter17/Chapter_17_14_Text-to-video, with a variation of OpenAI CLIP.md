# OpenAI CLIP'in Metinden Videoya Sentez Uygulaması

Bu bölüm, Hugging Face tarafından barındırılan metinden videoya sentez için OpenAI CLIP'in bir uygulamasını çalıştıracaktır. 16. Bölüm'de, "Beyond Text: Vision Transformers in the Dawn of Revolutionary AI" başlıklı bölümde, CLIP'in görüntü mimarisini inceledik. Bir video, bir dizi görüntü karesidir, bu da CLIP'in metinden videoya, difüzyon işlevselliği dahil olmak üzere nasıl kullanıldığını görmek için ilginçtir. Model yaklaşık 1,7 milyar parametre ile eğitilmiştir.

Depo'nun bölüm dizininde bulunan `Open Text_to_video_synthesis.ipynb` dosyasını açın. İlk olarak gerekli kütüphaneleri kuracağız ve modülleri içe aktaracağız:

```python
!pip install modelscope==1.4.2
!pip install open_clip_torch
!pip install pytorch-lightning
from modelscope.pipelines import pipeline
from modelscope.outputs import OutputKeys
```

## Kurulum ve İçe Aktarma İşlemleri

*   `!pip install modelscope==1.4.2`: Bu komut, makine öğrenimi modellerinin performansını izlemek, takip etmek ve açıklamak için ModelScope kütüphanesini kurar.
*   `!pip install open_clip_torch`: Bu komut, metinden görüntüye işlemleri için Open-CLIP kütüphanesini kurar.
*   `!pip install pytorch-lightning`: Bu komut, PyTorch modellerini geliştirmeyi ve eğitmayı kolaylaştıran PyTorch Lightning kütüphanesini kurar.
*   `from modelscope.pipelines import pipeline`: Bu komut, `modelscope.pipelines` modülünden `pipeline` fonksiyonunu içe aktarır. `pipeline` fonksiyonu, bir makine öğrenimi modelini izlemek ve takip etmek için bir işlem hattı oluşturmak için kullanılabilir.
*   `from modelscope.outputs import OutputKeys`: Bu komut, `modelscope.outputs` modülünden `OutputKeys` sınıfını içe aktarır. `OutputKeys` sınıfı, ModelScope tarafından izlenebilen çıktıların adlarını tanımlar.

## Metinden Videoya Sentez Modeli ile Video Oluşturma

```python
p = pipeline('text-to-video-synthesis', 'damo/text-to-video-synthesis')
test_text = {'text': 'A car flying in space.'}
output_video_path = p(test_text,)[OutputKeys.OUTPUT_VIDEO]
print('You can play or save the video from the output_video_path:', output_video_path)
```

*   `p = pipeline('text-to-video-synthesis', 'damo/text-to-video-synthesis')`: Bu satır, metinden videoya sentez modeli için bir işlem hattı oluşturur.
*   `test_text = {'text': 'A car flying in space.'}`: Bu satır, modele giriş olarak kullanılacak metni tanımlar.
*   `output_video_path = p(test_text,)[OutputKeys.OUTPUT_VIDEO]`: Bu satır, modele metni giriş olarak verir ve oluşturulan videonun yolunu `output_video_path` değişkenine atar.
*   `print('You can play or save the video from the output_video_path:', output_video_path)`: Bu satır, oluşturulan videonun yolunu yazdırır.

## Oluşturulan Videoyu Görüntüleme ve Kaydetme

```python
from IPython.display import display, Video
display(Video(output_video_path, embed=True))
```

*   Bu kod, oluşturulan videoyu görüntüler.

```python
# Download result
from google.colab import files
files.download(output_video_path)
```

*   Bu kod, oluşturulan videoyu indirir.

Bu deneysel modelle bazı istemleri deneyerek neler olacağını görün! Şimdi Meta'nın videodan metne modelini çalıştıracağız.

---

