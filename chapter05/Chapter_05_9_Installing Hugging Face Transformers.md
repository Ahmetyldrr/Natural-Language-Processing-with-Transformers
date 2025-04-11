# Hugging Face Önceden Eğitilmiş BERT Modeli Sağlar

Hugging Face önceden eğitilmiş bir BERT modeli sağlar. Hugging Face, `PreTrainedModel` adında bir temel sınıf geliştirmiştir. Bu sınıfı kurarak önceden eğitilmiş bir yapılandırmadan bir model yükleyebiliriz. Hugging Face, TensorFlow ve PyTorch'ta modüller sağlar. Bir geliştiricinin her iki ortamda da rahat olması önerilir. Yapay zeka araştırma takımları bu ortamların birini veya her ikisini de kullanabilir. Bu bölümde, gerekli modülleri aşağıdaki şekilde kuracağız:

```python
try:
    import transformers
except:
    print("transformers kuruluyor")
    # !pip -q install transformers 
    # Bu satır bir Jupyter Notebook hücresinde çalıştırılacak bir komuttur.
    # -q seçeneği ile kurulum ayrıntılarını sınırlar ve sadece uyarı veya hata mesajları gösterir.
```

## Kurulum ve İçe Aktarma

Kurulum, `-q` seçeneği ile çalışacak ve ayrıntıları sınırlayarak sadece uyarı veya hata mesajları gösterecektir. Şimdi program için gerekli modülleri içe aktarabiliriz.

### Kod Açıklaması

1. `try: import transformers` 
   - Bu satır, `transformers` kütüphanesini içe aktarmayı dener.

2. `except: print("Installing transformers")`
   - Eğer `transformers` kütüphanesi içe aktarılamazsa (yani kurulu değilse), bu satır "transformers kuruluyor" mesajını yazdırır.

3. `!pip -q install transformers`
   - Bu satır, Jupyter Notebook içinde çalıştırıldığında `transformers` kütüphanesini `-q` (quiet) modunda kurar. 
   - `-q` seçeneği, kurulum sırasında ayrıntılı çıktıları bastırır ve sadece uyarıları veya hataları gösterir.

4. `import transformers`
   - Kurulumdan sonra, `transformers` kütüphanesini içe aktarmak için kullanılır.

Bu şekilde, gerekli kütüphane kontrol edilir, eğer kurulu değilse kurulur ve programın devam etmesi için içe aktarılır.

---

