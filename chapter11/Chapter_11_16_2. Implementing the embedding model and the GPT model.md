# Model Seçimi
Bir model seçmek, gelişmiş bir NLP görevi için programınızın ve projenizin yolunu belirleyecektir. Yanlış olanı seçerseniz, çıktıların doğruluğu düşük olacaktır. Doğruluk için doğru olanı seçerseniz, projeniz için çok maliyetli olabilir. Doğruluk ve maliyet arasında bir denge bulmanız gerekecektir. Bu not defterinde embeddingler için `text-embedding-ada-002` ve soru-cevap görevi için `gpt-3.5-turbo` seçilmiştir: 
```python
# modeller
EMBEDDING_MODEL = "text-embedding-ada-002"
GPT_MODEL = "gpt-3.5-turbo"
```
`text-embedding-ada-002`, OpenAI'ın ikinci nesil embedding modelidir. Maksimum 8.191 token girdisini kabul edecek ve 1.536 boyutlu çıktı vektörleri üretecektir. 
Bu bilgilerin sindirilmesi için birkaç saniye ayırın: Örneğin, Gensim'in vektör uzayındaki her kelime için 300 boyut yerine her token için 1.536 boyut.

`GPT-3.5-turbo` ve `GPT-4` hem doğal dili anlayabilir hem de üretebilir. `GPT-4`, `GPT-3.5-turbo`'yu geliştirir. Ancak, her görev için `GPT-4`'e ihtiyacımız var mı? Her şey için en güçlü modele ihtiyacımız var mı? Hayır, yok. Ancak, bir modelin diğerine göre seçilmesi dikkatli bir değerlendirme gerektirir. 
Bir model ile diğeri arasında seçim yaparken maliyet hala kritiktir. Bir model uygularken OpenAI'ın fiyatlandırma sayfasını kontrol ettiğinizden emin olun: https://openai.com/pricing#language-models . 
Şimdi modeli değerlendireceğiz.

Python kodları:

1. `# models` : Bu bir yorum satırıdır ve kodun çalışmasını etkilemez. Sadece kodun okunmasını kolaylaştırmak için kullanılır.
2. `EMBEDDING_MODEL = "text-embedding-ada-002"` : `EMBEDDING_MODEL` adlı bir değişken tanımlanıyor ve `"text-embedding-ada-002"` string değeri atanıyor. Bu değişken embedding modeli için kullanılacak.
3. `GPT_MODEL = "gpt-3.5-turbo"` : `GPT_MODEL` adlı bir değişken tanımlanıyor ve `"gpt-3.5-turbo"` string değeri atanıyor. Bu değişken GPT modeli için kullanılacak.

Bu python kodları, daha sonra kullanılmak üzere iki model adını değişkenlere atamaktadır.

---

