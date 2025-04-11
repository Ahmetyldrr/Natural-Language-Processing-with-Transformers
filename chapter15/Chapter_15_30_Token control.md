# Verilen İngilizce Paragrafın Türkçe Çevirisi

Toplam token sayısı, bütçe izleme için pandas DataFrame'de de görüntülenir. OpenAI bize 1K token'lık gruplar için ücretlendirme yapacaktır. Bir token yaklaşık bir kelimenin %75'i kadardır. Böylece bir maliyet-izleme fonksiyonu oluşturabilirsiniz. Token kontrolü, bir LLM kullanmanın risklerini sınırlayabilir: 
- Token kullanım limiti yoluyla kullanıcıların aşırı güvenini sınırlama
- Dialog fonksiyonunda max_tokens parametresini tanıtarak modelin sapmasını önlemek ve halüsinasyonları sınırlama
- Genel bütçe izleme ve kontrolü

## Python Kodları Yok, Sadece Çeviri Yapıldı

Eğer python kodları olsaydı, satır satır açıklama yapılacaktı. Ancak verilen metinde python kodları bulunmamaktadır. Sadece bir ingilizce paragrafın türkçeye çevirisi yapılmıştır. 

Eğer çeviri yapılacak metinde python kodları olsaydı, örneğin:
```python
# örnek python kodu
def maliyet_hesapla(token_sayisi):
    # token başına maliyet
    maliyet = 0.01
    return token_sayisi * maliyet
```
Yukarıdaki python kodu için satır satır açıklama aşağıdaki gibi olacaktı:

1. `def maliyet_hesapla(token_sayisi):` 
   - `maliyet_hesapla` isimli bir fonksiyon tanımlanıyor. Bu fonksiyon `token_sayisi` parametresini alıyor.

2. `# token başına maliyet`
   - Bu satır bir yorum satırıdır ve token başına maliyetin ne anlama geldiğini açıklıyor.

3. `maliyet = 0.01`
   - Token başına maliyet 0.01 olarak belirleniyor.

4. `return token_sayisi * maliyet`
   - Fonksiyon, verilen `token_sayisi` ile `maliyet`i çarparak toplam maliyeti hesaplıyor ve döndürüyor.

---

