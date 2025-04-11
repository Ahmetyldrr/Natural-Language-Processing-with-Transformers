# Amazon İnce Gıda İncelemeleri Veri Seti

Amazon Fine Food Reviews veri seti, Ekim 2012'ye kadar kullanıcılar tarafından yazılmış 568.454 gıda incelemesi içermektedir. Bu not defteri, en son 1.000 incelemeden oluşan bir alt kümeyi çıkaracaktır. İncelemeler oldukça olumlu veya olumsuz olarak sınıflandırılabilir. İnceleme kayıtları bir ürün kimliği, kullanıcı kimliği, puan, inceleme başlığı (özet) ve inceleme gövdesi (metin) içermektedir. İnceleme özeti ve inceleme tek bir birleşik metinde birleştirilecek ve tek bir vektöre gömülecektir.

## Veri Setinin İndirilmesi

İlk olarak veri setini https://www.kaggle.com/datasets/snap/amazon-fine-food-reviews adresinden Kaggle hesabımızla indireceğiz:
```python
!kaggle datasets download -d snap/amazon-fine-food-reviews
```
## Zip Dosyasının Çıkarılması

İncelemeleri Reviews.csv dosyasından çıkaracağız:
```python
import zipfile
```
*   Yukarıdaki kod, `zipfile` adlı Python kütüphanesini içe aktarır. Bu kütüphane, zip dosyalarıyla çalışmak için kullanılır.

```python
zip_file_path = '/content/amazon-fine-food-reviews.zip'
csv_file_name = 'Reviews.csv'
```
*   `zip_file_path` değişkeni, indirilen zip dosyasının yolunu belirtir.
*   `csv_file_name` değişkeni, zip dosyasından çıkarılacak dosyanın adını belirtir.

```python
with zipfile.ZipFile(zip_file_path, 'r') as zip_ref:
```
*   Yukarıdaki kod, `zip_file_path` değişkeninde belirtilen zip dosyasını açar. `'r'` parametresi, dosyanın okunmak üzere açıldığını belirtir.
*   `with` ifadesi, dosya işlemleri tamamlandıktan sonra otomatik olarak dosyayı kapatmayı sağlar.

```python
zip_ref.extract(csv_file_name)
```
*   Yukarıdaki kod, `csv_file_name` değişkeninde belirtilen dosyayı zip dosyasından çıkarır.

## Verilerin Hazırlanması

Şimdi verileri hazırlayacağız.

---

