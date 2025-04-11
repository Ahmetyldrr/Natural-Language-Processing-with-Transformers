# Yapay Zeka Sanayileşme Çağına Girdi
Şimdi, Yapay Zeka'nın (YZ) sanayileşme çağına iyice girdik. Microsoft Azure, Google Cloud, Amazon Web Services (AWS) ve IBM gibi devler, hiçbir geliştiricinin veya geliştirici takımının umut edemeyeceği düzeyde YZ hizmetleri sunuyorlar. Teknoloji devleri, transformer modellerini ve genel olarak YZ modellerini eğitmek için milyonlarca dolarlık süper bilgisayarlara ve büyük veri setlerine sahip. Büyük teknoloji devlerinin halihazırda bulut hizmetlerini kullanan birçok kurumsal müşterisi var. Sonuç olarak, mevcut bir bulut mimarisine transformer API'si eklemek, diğer herhangi bir çözümden daha az çaba gerektiriyor. Küçük bir şirket veya hatta bir birey, pratik olarak hiçbir geliştirme yatırımı yapmadan, en güçlü transformer modellerine bir API aracılığıyla erişebilir. Bir stajyer, API'yi birkaç gün içinde uygulayabilir. Bu kadar basit bir uygulama için mühendis veya doktora derecesine sahip olmak gerekmez.

# OpenAI Platformu ve Transformer Modelleri
Örneğin, OpenAI platformu şimdi piyasadaki en etkili transformer modellerinden bazıları için Yazılım-Hizmet (SaaS) API'si sunuyor. OpenAI transformer modelleri o kadar etkili ve insan benzeri ki, mevcut politika, potansiyel kullanıcının bir istek formu doldurmasını gerektiriyor. İstek kabul edildikten sonra, kullanıcı doğal dil işleme evrenine erişebilir! OpenAI'ın API'sinin basitliği kullanıcıyı şaşırtıyor: Bir tıklamayla API anahtarı alın. Bir satırda OpenAI'ı bir not defterine aktarın. İstediğiniz herhangi bir Doğal Dil İşleme (NLP) görevini bir komut ile girin. Başka bir fonksiyon yazmanıza gerek kalmadan bir cevap alacaksınız. Örneğin, OpenAI'ın platformunda açıklandığı gibi, doğal dili bir SQL sorgusuna çevirebilirsiniz: https://platform.openai.com/examples/default-sql-translate :

## Şekil 1.5: OpenAI'de SQL sorgusu oluşturmak için komut
## Şekil 1.6: SQL komutundan gelen cevap

Ve hepsi bu kadar! Yapay Zeka API'lerinin dünyasına hoş geldiniz! Sadece kod odaklı çözümlere odaklanan geliştiriciler, YZ yardımcı pilotlarının gücünden yararlanan disiplinler arası zihinlere sahip bir nesil geliştirici haline gelecekler. YZ profesyonelleri, bir transformer modeline ne beklendiğini nasıl göstereceklerini tasarlamayı ve ona ne yapacağını söylememeyi öğrenmek zorunda kalacaklar. Kitabın sonunda, bu son teknoloji YZ modellerinin davranışını kontrol etmek için birkaç yöntem kazanmış olacaksınız.

# API'lerin Sınırları
API'ler birçok ihtiyacı karşılayabilir, ancak aynı zamanda sınırları da vardır. Örneğin, çok amaçlı bir API, tüm görevlerde makul derecede iyi olabilir, ancak belirli bir NLP görevi için yeterince iyi olmayabilir. Örneğin, transformerlarla çeviri yapmak kolay bir iş değildir. Bu durumda, bir YZ geliştiricisi, danışmanı veya proje yöneticisi, bir API'nin tek başına gerekli NLP görevini çözemeyeceğini kanıtlamak zorundadır. Bunu yaptıktan sonra, sağlam bir kütüphane, başka bir alternatif çözüm veya hatta kendi geliştirdikleri bir çözüm arayışına girmeleri gerekebilir.

Python kodları bulunmamaktadır, ancak OpenAI API'sini kullanmak için örnek bir python kodu aşağıdaki gibi olabilir:
```python
import openai

# API anahtarını alın
openai.api_key = "API_ANAHTARINIZ"

# NLP görevi için komut girin
prompt = "Doğal dili SQL sorgusuna çevir"

# OpenAI API'sini kullanarak cevabı alın
response = openai.Completion.create(
    engine="davinci",
    prompt=prompt,
    max_tokens=2048,
    temperature=0.7
)

# Cevabı yazdırın
print(response.choices[0].text)
```
Bu kod, OpenAI API'sini kullanarak bir NLP görevi için komut girer ve cevabı alır. 

1. `import openai`: OpenAI kütüphanesini içe aktarır.
2. `openai.api_key = "API_ANAHTARINIZ"`: OpenAI API anahtarını ayarlar.
3. `prompt = "Doğal dili SQL sorgusuna çevir"`: NLP görevi için komutu tanımlar.
4. `response = openai.Completion.create()`: OpenAI API'sini kullanarak cevabı alır.
5. `print(response.choices[0].text)`: Cevabı yazdırır.

---

