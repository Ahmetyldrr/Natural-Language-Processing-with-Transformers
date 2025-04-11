# Transformers ve Yapay Zeka Evrimi
Transformatörler yapay zekayı derin evrimlere zorladı. Temel Modeller, üretken yapay zeka yetenekleri de dahil olmak üzere, her şeyi her şeye bağlayan ve her yerde temel süreçlere sahip olan dijital devrim üzerine inşa edilmiştir. Otomatik süreçler, NLP dahil olmak üzere kritik alanlardaki insan kararlarının yerini alıyor. RNN'ler hızlı hareket eden bir dünyada gerekli olan otomatik NLP görevlerinin ilerlemesini yavaşlattı. Transformatörler bu boşluğu doldurdu. Bir şirket, artan gelen bilgi hacminin zorluklarıyla başa çıkmak için özetleme, çeviri ve geniş bir NLP araç yelpazesine ihtiyaç duyar. Transformatörler böylece bir yapay zeka endüstriyel çağı başlattı.

## Transformatörlerin Temel Modelleri Olarak Kullanılması
İlk olarak transformatörlerin nasıl geniş bir görev yelpazesi gerçekleştiren Temel Modeller haline geldiğini gördük. Transformatör dikkat katmanlarının nasıl yinelemeli ağ katmanlarını geride bıraktığını kısaca gördük. Transformatör modellerinin tek jeton esnekliğinin nasıl günlük hayatımızın her alanına nüfuz etmeye başladığını gördük! Hugging Face, Google Cloud, OpenAI ve Microsoft Azure gibi platformlar, NLP görevlerini kurulum gerektirmeden ve özelleştirilmiş programlarda transformatör modeli uygulamak için kaynaklar sağlar. Örneğin, OpenAI, güçlü GPT-4 jenerasyon modellerinden birini çalıştırmak için yalnızca birkaç kod satırı gerektiren bir API sağlar. Google Trax uçtan uca bir kütüphane sağlar, Google Vertex AI kolayca uygulanabilir araçlara sahiptir ve Hugging Face çeşitli transformatör modelleri ve uygulamaları sunar. Bu ekosistemleri bu kitap boyunca keşfedeceğiz.

## Transformatör Mimarisi ve Otomasyon
Daha sonra transformatör mimarisinin, eski yapay zekadan kökten farklı olan otomasyona nasıl yol açtığını gördük. Sonuç olarak, bir yapay zeka profesyoneli için daha geniş beceri setleri gereklidir. Örneğin, bir proje yöneticisi, bir web tasarımcısından Google Cloud AI veya OpenAI API'leri için bir arayüz oluşturmasını istemek suretiyle transformatörleri uygulayabilir. Veya gerektiğinde, bir proje yöneticisi bir yapay zeka uzmanından Google Trax veya Hugging Face kaynaklarını indirerek özelleştirilmiş bir transformatör modeli ile tam teşekküllü bir proje geliştirmesini isteyebilir. Transformatör, rolleri genişleyecek ve programlamadan daha fazla tasarım gerektirecek olan geliştiriciler için bir oyun değiştiricisidir. Ayrıca, gömülü transformatörler, yardımcı kod geliştirme ve kullanımı sağlayacaktır. Bu yeni beceri setleri bir zorluk ama aynı zamanda yeni heyecan verici ufuklar açıyor.

## Gelecek Adımlar
# 2. Bölümde, Transformatör Modelinin Mimarisine Başlarken, orijinal transformatör mimarisi ile başlayacağız.

Python kodları bulunmamaktadır, ancak OpenAI API'sini kullanmak için örnek bir kod bloğu aşağıda verilmiştir:
```python
import openai

# OpenAI API anahtarınızı girin
openai.api_key = "API-ANAHTARINIZ"

# GPT-4 modelini kullanarak metin oluşturun
response = openai.Completion.create(
  model="gpt-4",
  prompt="Merhaba, dünya!",
  max_tokens=1024
)

# Oluşturulan metni yazdırın
print(response.choices[0].text)
```
Bu kod, OpenAI API'sini kullanarak GPT-4 modelini çalıştırır ve "Merhaba, dünya!" promptuna karşılık olarak metin oluşturur. `max_tokens` parametresi, oluşturulacak metnin maksimum uzunluğunu belirler.

---

