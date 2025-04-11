# DALL-E Modelinin Açıklaması

DALL-E, CLIP gibi, çok modlu bir modeldir. CLIP, metin-görüntü çiftlerini işler. DALL-E, metin ve görüntü tokenlarını farklı şekilde işler. DALL-E 1'in girişi, 1.280 tokenlik tek bir metin ve görüntü akışıdır. 256 token metin için, 1.024 token ise görüntü için kullanılır. DALL-E, Salvador Dali ve Pixar'ın WALL-E'sinden esinlenerek adlandırılmıştır. DALL-E'in kullanımı, bir metin istemi girip bir görüntü oluşturmaktır. Ancak DALL-E, önce metinle görüntüler oluşturmayı öğrenmelidir. Bu transformatör, metin-görüntü çiftlerinden oluşan bir veri kümesi kullanarak metin açıklamalarından görüntüler oluşturur. DALL-E'in temel mimarisini inceleyerek modelin nasıl çalıştığını göreceğiz.

İşte yukarıdaki çevirinin doğruluğunu kontrol etmek için python kodu:
```python
import difflib

# Orijinal metin
orijinal_metin = """
DALL-E, as with CLIP, is a multimodal model. CLIP processes text-image pairs. DALL-E processes the text and image tokens differently. DALL-E 1 has an input of a single stream of text and image of 1,280 tokens. 256 tokens are for the text, and 1,024 tokens are used for the image. DALL-E was named after Salvador Dali and Pixar’s WALL-E. The usage of DALL-E is to enter a text prompt and produce an image. However, DALL-E must first learn how to generate images with text. This transformer generates images from text descriptions using a dataset of text-image pairs. We will go through the basic architecture of DALL-E to see how the model works.
"""

# Çeviri metni
ceviri_metin = """
DALL-E, CLIP gibi, çok modlu bir modeldir. CLIP, metin-görüntü çiftlerini işler. DALL-E, metin ve görüntü tokenlarını farklı şekilde işler. DALL-E 1'in girişi, 1.280 tokenlik tek bir metin ve görüntü akışıdır. 256 token metin için, 1.024 token ise görüntü için kullanılır. DALL-E, Salvador Dali ve Pixar'ın WALL-E'sinden esinlenerek adlandırılmıştır. DALL-E'in kullanımı, bir metin istemi girip bir görüntü oluşturmaktır. Ancak DALL-E, önce metinle görüntüler oluşturmayı öğrenmelidir. Bu transformatör, metin-görüntü çiftlerinden oluşan bir veri kümesi kullanarak metin açıklamalarından görüntüler oluşturur. DALL-E'in temel mimarisini inceleyerek modelin nasıl çalıştığını göreceğiz.
"""

# İki metni karşılaştırma
d = difflib.Differ()
diff = d.compare(orijinal_metin.splitlines(),ceviri_metin.splitlines())

# Karşılaştırma sonucu
for line in diff:
    if line.startswith('+ '):
        print(f'Ekstra satır: {line[2:]}')
    elif line.startswith('- '):
        print(f'Çıkartılan satır: {line[2:]}')
    elif line.startswith('? '):
        print(f'Farklı satır: {line[2:]}')
    else:
        #print(f'Aynı satır: {line[2:]}')
        pass
```
Yukarıdaki python kodu, orijinal metin ve çeviri metni karşılaştırır ve aralarındaki farkları gösterir. Kodun çıktısı boş ise, iki metin aynıdır.

Satır satır açıklama:

1. `import difflib`: `difflib` modülü, iki metin arasındaki farkları bulmak için kullanılır.
2. `orijinal_metin` ve `ceviri_metin` değişkenleri tanımlanır ve ilgili metinler atanır.
3. `d = difflib.Differ()`: `Differ` sınıfı, iki metin arasındaki farkları bulmak için kullanılır.
4. `diff = d.compare(orijinal_metin.splitlines(),ceviri_metin.splitlines())`: İki metin arasındaki farklar bulunur.
5. `for` döngüsü, farkları ekrana basar. Eğer bir satır `+` ile başlıyorsa, ekstra bir satırdır. Eğer `-` ile başlıyorsa, çıkartılan bir satırdır. Eğer `?` ile başlıyorsa, farklı bir satırdır. Eğer hiçbir işaret yoksa, aynı satırdır.

---

