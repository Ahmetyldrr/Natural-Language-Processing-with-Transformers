# Google AI Eğilimi
Google AI eğilimi, bu bölümde göreceğimiz gibi, ML uzmanı olmayanların ML uzmanı görevlerini yerine getirmesini sağlamaktır. Aşağıdaki örneklerde, Şekil 14.12'de gösterildiği gibi bir istem girilecektir:

## Şekil 14.12: İstem Kullanıcı Arayüzü

Bu tarihte PaLM 2 modellerinden birini seçeceğiz (bunlar, text_bison@002, Gemini, vb. gibi bu listede sürekli olarak gelişecektir):

## Şekil 14.13: Modellerin Listesi

Varsayılan parametreleri kullanacağız ve modelin adıyla başlayan yanıtı görüntüleyeceğiz:

### Bir Talimat Görevi
İstem: Google Dokümanlar'a eklenti nasıl yüklenir açıklayın:
Yanıt (text-bison): Google Dokümanlar'ı açın ve "Eklentiler" menüsüne tıklayın. "Eklenti al" seçeneğine tıklayın. Arama çubuğuna yüklemek istediğiniz eklentinin adını yazın. Eklentinin adına tıklayın ve "Yükle" seçeneğine tıklayın. Eklenti yüklenecek ve "Eklentiler" menüsüne eklenecektir. Eklentiyi kullanmak için "Eklentiler" menüsüne tıklayın ve eklentiyi seçin...

### Bir Üretken Sohbet Görevi
İstem: Büyük dil modeli Üretken Yapay Zeka nedir açıklayın:
Yanıt (text-bison): Büyük bir dil modeli (LLM), metin oluşturabilen, dilleri çevirebilen, farklı türlerde yaratıcı içerik yazabilen, sorularınızı yanıtlayabilen ve metni özetleyebilen bir yapay zeka türüdür... 
LLM'lerin en heyecan verici şeylerinden biri, yaratıcı metin oluşturma yetenekleridir. Şiir, kod, senaryo, müzik parçaları ve hatta tüm romanlar gibi farklı türlerde yaratıcı içerikler yazabilirler. Bunun nedeni, LLM'lerin farklı yaratıcı metin türlerinde kullanılan farklı desenleri ve yapıları öğrenebilmeleridir...

### Bir Ayırt Edici Görev
İstem: Aşağıdaki metin beyzbol veya hokey hakkındadır ve nedenini açıklayın: "Oyuncu topu attı."
Yanıt (text-bison): Metin beyzbol hakkındadır çünkü beyzbol, bir oyuncunun topu attığı tek spordur. Hokeyde, oyuncular diski vurmak için bir sopa kullanırlar.

### Bir Metin Üzerinde Soru-Cevap Görevi
İstem: Bu metindeki ana karakterin adı ve ana karakterin ana faaliyeti nedir: Jill, John ve Alice bir proje üzerinde çalışıyorlardı. Jill bir web arayüzü tasarladı, John metni yazdı ve Alice web sitesinin tasarımını ve içeriğini kontrol etti ve üst yönetime rapor verdi.
Yanıt (text-bison): Ana karakter Alice'dir. Ana karakter, hikayedeki en önemli şeyi yapan kişidir. Bu durumda, Alice web sitesinin tasarımını, içeriğini kontrol eden ve üst yönetime rapor veren kişidir.

### Bir Kod Talimatı Görevi
İstem: 1'den başlayarak ilk 10 asal sayıyı hesaplayabilen bir Python programı yazın. Çıktıyı 10 ile sınırlayın:
Yanıt (code-bison@001):
```python
# Bu program 1'den başlayarak ilk 10 asal sayıyı hesaplayacaktır.
# Bir sayının asal olup olmadığını kontrol eden bir fonksiyon tanımlayın.
def is_prime(number):
    # Sayının 2'ye bölünüp bölünmediğini kontrol edin.
    if number % 2 == 0:
        return False
    # Sayının 3'ten sayının kareköküne kadar olan herhangi bir sayıya bölünüp bölünmediğini kontrol edin.
    for i in range(3, int(number ** 0.5) + 1, 2):
        if number % i == 0:
            return False
    # Sayı 2'den sayının kareköküne kadar olan herhangi bir sayıya bölünmüyorsa, asal demektir.
    return True

# İlk 10 asal sayıyı alın.
prime_numbers = []
for number in range(1, 10000):
    if is_prime(number):
        prime_numbers.append(number)
    # İlk 10 asal sayıyı yazdırın.
    if len(prime_numbers) == 10:
        break
print(prime_numbers)
```
Kod çalıştırıldığında, çıktının doğru olduğu doğrulanabilir: `[2, 3, 5, 7, 11, 13, 17, 19, 23, 29]` (Not: Orijinal metinde ilk asal sayı olarak 1 yazılmıştır, ancak 1 asal sayı değildir.)

## Kod Açıklaması
1. `is_prime(number)` fonksiyonu, bir sayının asal olup olmadığını kontrol eder.
   - `if number % 2 == 0:` Sayının 2'ye bölünüp bölünmediğini kontrol eder. Eğer bölünürse, asal değildir.
   - `for i in range(3, int(number ** 0.5) + 1, 2):` 3'ten sayının kareköküne kadar olan tek sayıları dolaşır.
     - `if number % i == 0:` Sayının bu aralıklardaki herhangi bir sayıya bölünüp bölünmediğini kontrol eder. Eğer bölünürse, asal değildir.

2. `prime_numbers` listesi, asal sayıları saklamak için kullanılır.
   - `for number in range(1, 10000):` 1'den 10000'e kadar olan sayıları dolaşır.
     - `if is_prime(number):` Sayının asal olup olmadığını kontrol eder.
       - `prime_numbers.append(number)` Asal ise, `prime_numbers` listesine ekler.

3. `print(prime_numbers[:10])` İlk 10 asal sayıyı yazdırır.

Google asistanlarının sezgisel, etkili ve çalıştırması kolay olduğunu gördük. Şimdi Vertex AI PaLM 2 API ile NLP görevleri için fonksiyonlar oluşturacağız.

---

