# Bu Alt Bölümde Yapılacaklar

Bu alt bölümde, Hugging Face'in çerçevesini kuracağız ve ardından bir T5 modelini başlatacağız. İlk olarak Hugging Face'in transformerlarını kuracağız: 
```python
!pip install transformers -qq
```
Not : Hugging Face transformerları sürekli olarak gelişmekte, piyasaya uyum sağlamak için kütüphaneleri ve modülleri güncellemektedir. Varsayılan sürüm çalışmazsa, başka bir sürümü `!pip install transformers==[diğer fonksiyonlarla çalışan sürüm]` komutu ile kurmanız gerekebilir. 
Notebook'un Hugging Face ile olabildiğince stabil kalmasını sağlamak için sentencepiece'ın 0.1.94 sürümünü kurduk: 
```python
!pip install sentencepiece==0.1.94
```
sentencepiece, bir metni ayrı cümlelere böler. Bir paragrafı veya belgeyi cümle birimlerine ayırır. Gerekirse, 10. Bölüm'deki "Cümle ve Kelime Tokenizasyonu" bölümünü gözden geçirin, "Tokenleştiricilerin Transformer Modellerini Şekillendirmedeki Rolünü Araştırma". 
Hugging Face'in klonlanabilen bir GitHub deposu vardır. Ancak, Hugging Face'in çerçevesi, uygulayabileceğimiz bir dizi yüksek seviyeli transformer fonksiyonu sağlar. 
Modeli başlattığımızda modelin mimarisini göstermek veya göstermemek arasında seçim yapabiliriz: 
```python
display_architecture = True
```
Eğer `display_architecture` değişkenini `True` olarak ayarlarsak, kodlayıcı katmanlarının, kod çözücü katmanlarının ve ileri beslemeli alt katmanların yapısı gösterilecektir. Bu özellik, modelin mimarisine dair içgörüler sağlar. 
Program şimdi torch ve json'u içe aktarıyor: 
```python
import torch
import json
```
Transformerlar üzerinde çalışmak, araştırma kuruluşlarının bizimle paylaştığı birçok transformer mimarisi ve çerçevesine açık olmayı gerektirir. Ayrıca, her iki ortamda da alışkanlık kazanmak için PyTorch ve TensorFlow'u olabildiğince kullanmanızı öneririm. Önemli olan, transformer modelinin soyutlama seviyesi (özel görev modelleri veya sıfır-shot modelleri) ve genel performansıdır. 
Tokenizer, generation ve konfigürasyon sınıflarını içe aktaralım: 
```python
from transformers import T5Tokenizer, T5ForConditionalGeneration, T5Config
```
Burada T5-large modelini kullanacağız, ancak bu bölümün Hugging Face kısmında incelediğimiz Hugging Face listesinde diğer T5 modellerini seçebilirsiniz. 
Şimdi metin oluşturmak için T5-large conditional generation modelini ve T5-large tokenizer'ı içe aktaracağız: 
```python
model = T5ForConditionalGeneration.from_pretrained('t5-large')
tokenizer = T5Tokenizer.from_pretrained('t5-large')
```
İndirdiğimiz t5-large modelinin 770 milyon parametresi vardır. Hugging Face modeli güncellerse veya değiştirirse parametre sayısı değişebilir. 
Program şimdi torch.device'ı 'cpu' ile başlatıyor. Bu notebook için bir CPU yeterlidir. torch.device nesnesi, torch tensörlerinin tahsis edileceği cihazdır: 
```python
device = torch.device('cpu')
```
T5 modelinin mimarisini keşfetmeye hazırız.

---

