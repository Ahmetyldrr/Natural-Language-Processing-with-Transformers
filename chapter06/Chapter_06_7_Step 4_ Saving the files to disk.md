# Tokenizer Eğitim Sonrası Dosyaların Oluşturulması

Tokenizer eğitildiğinde iki dosya oluşturacaktır: 
- merges.txt, birleştirilmiş tokenleştirilmiş alt dizeleri içerir 
- vocab.json, tokenleştirilmiş alt dizelerin indekslerini içerir

Program önce KantaiBERT dizinini oluşturur ve ardından iki dosyayı kaydeder:

```python
import os
token_dir = '/content/KantaiBERT'
if not os.path.exists(token_dir):
  os.makedirs(token_dir)
tokenizer.save_model('KantaiBERT')
```

Program çıktısı, iki dosyanın kaydedildiğini gösterir:
`['KantaiBERT/vocab.json', 'KantaiBERT/merges.txt']`

İki dosya da dosya yöneticisi panelinde görünmelidir:

## Şekil 6.2: Colab Dosya Yöneticisi

Bu örnekteki dosyalar küçüktür. İçeriklerini görüntülemek için çift tıklayabilirsiniz. 
- merges.txt, planlandığı gibi tokenleştirilmiş alt dizeleri içerir:
```
#version: 0.2 - Trained by 'huggingface/tokenizers'
Ġ t
h e
Ġ a
o n
i n
Ġ o
Ġt he
r e
i t
Ġo f
```
- vocab.json, indeksleri içerir:
```
[…,"Ġthink":955,"preme":956,"ĠE":957,"Ġout":958,"Ġdut":959,"aly":960,"Ġexp":961,…]
```

Eğitilen tokenleştirilmiş veri kümesi dosyaları işlenmeye hazırdır.

### Kod Açıklaması

1. `import os`: Bu satır, Python'un işletim sistemi modülünü içe aktarır. Bu modül, dosya ve dizin işlemleri için kullanılır.

2. `token_dir = '/content/KantaiBERT'`: Bu satır, `token_dir` değişkenine KantaiBERT dizininin yolunu atar.

3. `if not os.path.exists(token_dir):`: Bu satır, `token_dir` değişkeninde belirtilen dizin varsa `True`, yoksa `False` döner. Eğer dizin yoksa (`False`), aşağıdaki kod bloğu çalışır.

4. `os.makedirs(token_dir)`: Bu satır, `token_dir` değişkeninde belirtilen dizini oluşturur.

5. `tokenizer.save_model('KantaiBERT')`: Bu satır, eğitilen tokenleştirici modeli 'KantaiBERT' dizinine kaydeder. Bu işlem, `merges.txt` ve `vocab.json` dosyalarını oluşturur.

Bu kod, KantaiBERT dizini yoksa oluşturur ve eğitilen tokenleştirici modeli bu dizine kaydeder.

---

