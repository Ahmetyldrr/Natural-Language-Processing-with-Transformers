# Not Defterinde Divergent Association Görevi için Generative AI Stable Diffusion'a Gitme

Not defterindeki Generative AI Stable Diffusion for a Divergent Association Task bölümüne gidin. 16. Bölümde, Beyond Text: Vision Transformers in the Dawn of Revolutionary AI , Divergent Semantic Association'ı keşfettik ve DAT görevlerini uyguladık. Bu bölümde, ilk istem olarak spagetti yemeyi ele alalım ve sonra istem metnini daha farklı bir şeye, örneğin uzaydaki bir dönme dolapta spagetti yemeye genişletelim. Not defteri önce standart bir metinden görüntüye görevi çalıştırır: 
```python
!python -m stability_sdk generate "eating spaghetti"
```
Şimdi çıktıyı görüntüleyebiliriz:
```python
import os 
from IPython.display import display, Image 
for file_name in os.listdir('/content'): 
    if file_name.endswith('.png'):
        display(Image(filename=os.path.join('/content', file_name)))
```
Şekil 17.6'daki görüntü "spagetti yeme"nin klasik bir görüntüsünü gösterir. 
# Şekil 17.6: Çatal kullanarak oldukça büyük bir tabak spagetti yiyen bir kişi

Görüntü, dönüştürücü modellerin rastgele doğası nedeniyle çalıştırmadan çalıştırmaya değişecektir. Şimdi, bir DAT deneyelim ve modele uzaydaki bir dönme dolapta spagetti yiyen bir kişinin alışılmadık bir görüntüsünü oluşturmasını isteyelim:
```python
!python -m stability_sdk generate "eating spaghetti on a merry-go-round in space"
```
Sonuç, Şekil 17.7'de görebileceğimiz gibi daha eğlenceli bir bağlamda "spagetti yeme"dir: 
# Şekil 17.7: Uzayda spagetti yeme

Dönme dolap kolayca tanımlanabilir. Spagetti, dönme dolabın sağındaki blob olabilir. Uzay iyi temsil edilmiştir. Standart temsillerden çok yaratıcı, farklı bir görüntüdür. Yapay zeka tarafından yaratıcılıkta üstünlük sağlamak artık bize alışıyor! Projenize bağlı olarak, daha fazla veya daha az farklı görüntüler isteyebilirsiniz. Şimdi metinden görüntüye geçiş yapacağız.

**Satır satır açıklama:**

1. `!python -m stability_sdk generate "eating spaghetti"`: Bu satır, `stability_sdk` adlı Python paketini kullanarak "eating spaghetti" metni için bir görüntü oluşturur.

2. `import os`: Bu satır, işletim sistemi ile etkileşime geçmek için kullanılan `os` modülünü içe aktarır.

3. `from IPython.display import display, Image`: Bu satır, Jupyter Notebook'ta görüntüleri görüntülemek için kullanılan `display` ve `Image` sınıflarını içe aktarır.

4. `for file_name in os.listdir('/content'):`: Bu satır, `/content` dizinindeki dosyaları listeleyen bir döngü başlatır.

5. `if file_name.endswith('.png'):`: Bu satır, dosya adının `.png` ile bitip bitmediğini kontrol eder.

6. `display(Image(filename=os.path.join('/content', file_name)))`: Bu satır, eğer dosya `.png` ise, görüntüyü Jupyter Notebook'ta görüntüler.

7. `!python -m stability_sdk generate "eating spaghetti on a merry-go-round in space"`: Bu satır, `stability_sdk` adlı Python paketini kullanarak "eating spaghetti on a merry-go-round in space" metni için bir görüntü oluşturur.

---

