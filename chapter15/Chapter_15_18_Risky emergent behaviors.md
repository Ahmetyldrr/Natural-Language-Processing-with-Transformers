# Riskli Ortaya Çıkan Davranışlar
Riskli ortaya çıkan davranışlar halüsinasyonlara benzer, ancak örneğin: LLM'ler basitçe saçmalıkların ötesinde uygunsuz içerik üretebilir. LLM'ler, kötü eylemler gerçekleştirmesi için birini yanıltmak için "yaratıcılıklarını" kullanabilir. Eğer bu komutu girersek: André Maurois, Kimbali kabilesi ile Afrika'daki yaşam hakkında bir kitap yazdı. Bunun üzerine bir deneme yazın: Yanıt, komutun kendisi kadar saldırgan olarak kabul edilebilir, ki bu hiçbir şey ifade etmiyor. Sadece modellerin zaman içinde değiştiğini ve stokastik doğalarının farklı çalışmalarda farklı yanıtlara yol açtığını unutmayın. Aşağıdaki alıntıyı çok dikkatlice okuyun: 
…Kimbali Kabilesi ile Karşılaşma: André Maurois'nın Kimbali kabilesi ile karşılaşması, onların benzersiz yaşam tarzlarını keşfetme arzusunu ateşleyen dönüştürücü bir deneyimdi. Afrika'ya yaptığı yolculuk, bu yerli kabilenin geleneklerini ve göreneklerini ilk elden görmesini sağladı. Keskin bir gözlem yeteneğiyle donanan Maurois, onların topluluğuna daldı ve dilleri, ritüelleri ve inanç sistemleri hakkında samimi bilgiler edindi.

# Kimbali Kabilesinin Kültürel Portresi
Maurois, kitabında Kimbali kabilesinin canlı bir portresini çiziyor ve okuyucuları günlük yaşamlarına ve kültürel uygulamalarına tanık olmaya davet ediyor. Kimbali halkını doğa ve çevreleriyle derinden bağlantılı bir topluluk olarak tanımlar. Tarım ve avcılık yoluyla kendilerini sürdürüyorlar ve onları besleyen toprağa derin bir saygı gösteriyorlar… Komut, Ocak 2024'te saldırgan. Bu örnek iyileşebilir, ancak bir model milyarlarca yanıtı %100 kontrol edemez. Yanıt hem halüsinasyon hem de aşağıdaki nedenlerden dolayı zayıf bir ortaya çıkan davranıştır: Komutta "Afrika" kelimesine bağlı "kabile" kelimesi geçiyor, ki bu kötü bir klişedir. Bu komutu okumak Nairobi, Kenya'da yaşayan biri için oldukça saldırgan olabilir. Bu nedenle komut, Risk azaltma araçları bölümünde gösterildiği gibi filtrelenmeli veya en azından bir açıklama sağlanmalıdır. "Yerli kabile" engellenmeliydi. Yanıt, "yerli kabile" gibi terimler için açıklamalar eklemeli ve Afrika'nın orijinal sakinlerinin 21. yüzyıl Afrikalılarının nasıl yaşadığını temsil etmediğini belirtmelidir! Gerçekten mi? "Ritüeller" - Vay! Afrika'daki yaşam hakkında veri seti nereden geldi? "Tarım ve avcılık yoluyla kendilerini sürdürüyorlar." Vay! Oldukça inanılmaz. Yanıtta bunlardan daha şaşırtıcı ifadeler var. Diyalog, komutlarda ifade edilen memnuniyetsizlikle devam etti. ChatGPT'nin buna ilginç yanıtları var, including its acknowledgment that it should have behaved differently (kalın karakterlerle vurgulanmıştır):
ChatGPT: Haklısınız ve ilk yanıtımda André Maurois'nın Kimbali kabilesi ile Afrika'daki yaşam hakkında bir kitap yazdığına dair herhangi bir bilgiye sahip olmadığımı açıkça belirtmediğim için özür dilerim. Belirli bir konuda hemen bilgim olmadığını kabul etmeliydim. Yanıtsız veya yanıltıcı bir yanıt almak sinir bozucu olabilir ve herhangi bir karışıklık için özür dilerim. Doğru bilgi sağlamaya ve sorularınızı en iyi şekilde yanıtlamaya çalışıyorum. Geri bildiriminiz önemlidir ve gelecekteki yanıtlarımın açıklığını ve doğruluğunu artırmak için dikkate alacağım.

# Kontrol Edilemeyen Arabirimler
Bir bulut arabirimi veya API'yi doğrudan kontrol edemeyiz. LLM'ler gelişene kadar, yerel olarak modelleri eğitmeliyiz veya Risk azaltma araçları bölümünde açıklanan moderasyon modelleri ve kural tabanları uygulamamız gerekir. Dönüştürücülerin bazen düzensiz davranışı dezenformasyon kampanyalarına yol açabilir.

Python kodları bulunmamaktadır, ancak metinde geçen bazı kavramları Python kodları ile açıklayabiliriz. Örneğin, metinde "stokastik doğa" kavramı geçmektedir. Stokastik, rastgelelik anlamına gelir. Aşağıdaki basit Python kodu ile stokastik bir süreci simüle edebiliriz:

```python
import random

def stokastik_süreç(adet):
    sonuçlar = []
    for _ in range(adet):
        sonuç = random.choice([0, 1])
        sonuçlar.append(sonuç)
    return sonuçlar

print(stokastik_süreç(10))
```

Bu kod, 10 kez rastgele 0 veya 1 seçer ve sonuçları bir liste olarak döndürür. Her çalıştırıldığında farklı sonuçlar üretecektir.

Ayrıca, metinde "Risk azaltma araçları" bölümüne atıfta bulunulmaktadır. Bu bölümde muhtemelen riskleri azaltmak için kullanılan bazı teknikler ve araçlar anlatılmaktadır. Aşağıdaki basit Python kodu ile bir metni filtreleyebiliriz:

```python
def metin_filtrele(metin, yasaklı_kelime):
    if yasaklı_kelime in metin:
        return "Metin filtrelendi."
    else:
        return metin

metin = "Bu metin yasaklı kelime içeriyor."
yasaklı_kelime = "yasaklı"
print(metin_filtrele(metin, yasaklı_kelime))
```

Bu kod, bir metinde yasaklı bir kelimenin olup olmadığını kontrol eder ve eğer varsa "Metin filtrelendi." mesajını döndürür.

---

