# 2014 WMT Çevirisi

2014 WMT birkaç Avrupa dili veri seti içeriyordu. Bir veri seti Europarl korpusunun 7. sürümünden elde edilen verileri içeriyordu. Avrupa Parlamentosu Tutanakları Paralel Korpusu'ndan (1996–2011) Fransızca-İngilizce veri setini kullanacağız (https://www.statmt.org/europarl/v7/fr-en.tgz).

## Dosyaları İndirme ve Ayıklama

GitHub deposunun chapter dizininde bulunan WMT-translations.ipynb dosyasını açın. İlk adım, ihtiyacımız olan dosyaları indirmektir:
```python
# Dosya URL'sini tanımla
file_url = "https://www.statmt.org/europarl/v7/fr-en.tgz"
# Hedef dosya yolunu tanımla
destination_file = "/content/fr-en.tgz"
# Dosyayı indir
urllib.request.urlretrieve(file_url, destination_file)
```
Burada kullanılan Python kodları:
- `import urllib.request`: `urllib.request` modülünü içe aktarır. Bu modül, URL'leri açmak ve indirmek için kullanılır.
- `file_url = "https://www.statmt.org/europarl/v7/fr-en.tgz"`: İndirilecek dosyanın URL'sini tanımlar.
- `destination_file = "/content/fr-en.tgz"`: İndirilen dosyanın kaydedileceği yolu tanımlar.
- `urllib.request.urlretrieve(file_url, destination_file)`: Belirtilen URL'deki dosyayı belirtilen hedef yola indirir.

## Dosyaları Ayıklama

Şimdi, indirilen dosyaları ayıklayacağız:
```python
import tarfile
# tar dosyasını ayıkla
with tarfile.open(destination_file, 'r:gz') as tar_ref:
    tar_ref.extractall("/content/fr-en")
```
Burada kullanılan Python kodları:
- `import tarfile`: `tarfile` modülünü içe aktarır. Bu modül, tar dosyalarını işlemek için kullanılır.
- `with tarfile.open(destination_file, 'r:gz') as tar_ref`: İndirilen tar dosyasını gzip sıkıştırmasıyla açar.
- `tar_ref.extractall("/content/fr-en")`: Tar dosyasının içeriğini belirtilen dizine ayıklar.

## Dosya Yolları

Dosyaları indirdikten ve ayıkladıktan sonra, dosyalar aşağıdaki yollarda bulunacaktır:
- `/content/fr-en/europarl-v7.fr-en.en`
- `/content/fr-en/europarl-v7.fr-en.fr`

## Korpusun Ön İşlemesi

İki paralel dosyayı yükleyeceğiz, temizleyeceğiz ve boyutunu küçülteceğiz. İki paralel dosyanın ön işlemesine başlayalım.

---

