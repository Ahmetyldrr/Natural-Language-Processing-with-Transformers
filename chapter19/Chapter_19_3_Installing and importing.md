# Bölüm Çevirisi

Bu bölümde, gelişmiş Yapay Zeka platformlarının kod gerektirmeyen işlevselliğinden yararlanacağız. Open Computer_Vision_Analysis.ipynb, Google Cloud Vision, HuggingGPT, Midjourney ve Runway Gen-2 ile etkileşimlerin sonuçlarını içeren bölüm not defterini açın. Not defteri, Generative AI videolarını görüntülemek için moviepy'i kurar: 
```python
!pip install moviepy -qq 
```
IPython.display, Generative AI resimlerini görüntülemek için kuruludur: 
```python
from IPython.display import Image 
# Bu, not defterinde resimleri işlemek için kullanılır
```
json, görme modellerinin çıktısını ayrıştırmak için içe aktarılır ve pandas, JSON içeriğini görüntülemek için kullanılır: 
```python
import json 
import pandas as pd 
```
Şimdi, asistanslı sürüş araştırmamız için doğrulama setini indireceğiz.

# Kod Açıklamaları

1. `!pip install moviepy -qq` : 
   - Bu satır, Jupyter Notebook veya benzeri bir ortamda moviepy kütüphanesini yüklemek için kullanılır.
   - `!` işareti, Jupyter'de komut satırı komutlarını çalıştırmak için kullanılır.
   - `-qq` parametresi, yükleme işleminin çıktılarını susturmak için kullanılır, böylece yükleme işlemi sessizce gerçekleşir.

2. `from IPython.display import Image` : 
   - Bu satır, IPython.display modülünden Image sınıfını içe aktarır.
   - Image sınıfı, Jupyter Notebook içinde resim görüntülemek için kullanılır.

3. `import json` : 
   - Bu satır, json modülünü içe aktarır.
   - json modülü, JSON (JavaScript Object Notation) formatındaki verileri ayrıştırmak ve üretmek için kullanılır.

4. `import pandas as pd` : 
   - Bu satır, pandas kütüphanesini içe aktarır ve ona `pd` takma adını verir.
   - pandas, veri işleme ve analizi için kullanılan güçlü bir kütüphanedir. Burada JSON içeriğini daha okunabilir bir biçimde görüntülemek için kullanılır.

---

