# Kaggle Müşteri Destek Verisetini Kullanarak Model Eğitimi

Modeli, Twitter'daki en büyük markalardan (Apple, American Airlines, Amazon ve diğer birçok üst düzey şirket) gelen 2.800.000+ müşteri destek tweet'ini içeren Kaggle'ın Twitter'daki Müşteri Desteği veri seti üzerinde eğiteceğiz. Bu veri seti hakkında daha fazla bilgi için lütfen https://www.kaggle.com/datasets/thoughtvector/customer-support-on-twitter adresini ziyaret edin. 

Bu veri setini kullanmak için bir Kaggle hesabına ve API anahtarına ihtiyacınız olacak ve kimlik doğrulamasını etkinleştirmeniz gerekecektir. Veri seti daha sonra tek satır kod ile indirilebilir: 
```python
!kaggle datasets download -d thoughtvector/customer-support-on-twitter
```
Dosya indirildikten sonra, zip dosyasından çıkarılır:
```python
import zipfile 
with zipfile.ZipFile('/content/customer-support-on-twitter.zip', 'r') as zip_ref:
    # '/content/' dizinine zip dosyasının içeriğini çıkarır
    zip_ref.extractall('/content/')
    # Dosya başarıyla çıkarıldı mesajı yazdırır
    print("File Unzipped!")
```
### Kod Açıklaması

1. `!kaggle datasets download -d thoughtvector/customer-support-on-twitter`
   - Bu komut, Kaggle'dan "customer-support-on-twitter" veri setini indirir.

2. `import zipfile`
   - Python'ın zipfile modülünü içe aktarır. Bu modül, zip dosyalarıyla çalışmak için kullanılır.

3. `with zipfile.ZipFile('/content/customer-support-on-twitter.zip', 'r') as zip_ref:`
   - `/content/customer-support-on-twitter.zip` yolundaki zip dosyasını okuma (`'r'`) modunda açar.
   - `with` ifadesi, dosya işlemleri için bir bağlam yöneticisi sağlar. Bu, işlem sonunda dosyanın otomatik olarak kapatılmasını sağlar.

4. `zip_ref.extractall('/content/')`
   - Zip dosyasının içeriğini `/content/` dizinine çıkarır.

5. `print("File Unzipped!")`
   - Dosya başarıyla çıkarıldığında ekrana "File Unzipped!" mesajını yazdırır.

---

