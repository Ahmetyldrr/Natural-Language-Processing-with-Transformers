# Verimli Bir Bilgi Tabanı Oluşturma

Verimli bir bilgi tabanı, meta veri ve sağlam bir ayrıştırma işlevi oluşturmak için çok iş var. Ayrıştırma işlevi, bu bölümde gösterildiği gibi klasik olabilir. Ayrıca, 11. Bölüm'de uyguladığımız gibi, gelişmiş arama özelliği ile embedding'leri de kullanabiliriz: [LLM Embedding'lerini İnce Ayarlama Alternatifi Olarak Kullanma](link).

# İddialara Anahtar Kelimeler Eklemek

İddialara anahtar kelimeler ekleyelim:
```python
assertkw1 = "open"
assertkw2 = "expert"
assertkw3 = "services"
assertkwn = "prompt"
```
Burada, `assertkw1`, `assertkw2`, `assertkw3` ve `assertkwn` değişkenlerine anahtar kelimeler atanmaktadır.

# Anahtar Kelimeleri Pandas DataFrame'de Görüntüleme

Anahtar kelimeleri bir liste olarak bilgi tabanına ekleyelim:
```python
# Bilgi tabanı anahtar kelimelerini liste olarak oluşturma
kbkw = [assertkw1, assertkw2, assertkw3, assertkwn]
```
Ardından, bu anahtar kelimeleri bir pandas DataFrame'de görüntüleyelim:
```python
# Bilgi tabanını DataFrame olarak görüntüleme
dfk = pd.DataFrame(kbkw)
dfk
```
Bu kod, `kbkw` listesindeki anahtar kelimeleri bir pandas DataFrame'e dönüştürür ve görüntüler.

# Çıktı

Çıktı, kalite kontrolü için hazırdır:
### Şekil 15.5: Bilgi Tabanı İndeksi

Şimdi, bilgi tabanımızı kullanıcının girişlerini ayrıştırmak için kullanacağız.

---

