# PaLM 2'nin Değerlendirilmesi ve Karşılaştırılması

PaLM 2'nin bazı alanlarda diğer modellerle eşleşebildiğini ve belki de onları aşabileceğini gördük. Google AI asistanları, bulut araçları ve API'ler genel amaçlı işlevler sağlar. Bunlar Microsoft Azure ve OpenAI tekliflerine benzer. Ancak, PaLM 2'ye yol açan mimari ile gördüğümüz gibi, teknoloji oldukça farklıdır. Ayrıca, birçok faktör kararı etkileyecektir ve çıktılar bir görevden diğerine değişebilir. Bir seçim yapmadan önce, Microsoft Azure, Google Cloud ve IBM Cloud dahil olmak üzere, doğru sorularla kapsamlı değerlendirmeler yapılmalıdır.

# Yeni Transformer Modellerinin İncelenmesi

Bölüm, yeni transformer modellerini keşfettiğimizde muhtemelen karşılaşacağımız dört bölümden oluşuyordu: mimari iyileştirmeleri, büyük dil üretken ana akım asistanları, API uygulaması ve özelleştirme (ince ayar veya diğer yöntemler). 
- LLM Generative AI modellerinin mimarisindeki birçok iyileştirmeyi gözden geçirerek bölüme başladık. 
- Pathways, donanım kaynaklarının ve verimliliğin artırılmış optimizasyonuna kapı açar. 
- PaLM ve PaLM 2, dikkat katmanlarıyla paralel olarak beslemeli ağı çalıştırma gibi cesur fikirler sunarak transformerların yazılım mimarisini geliştirdi. 
- Diğer bir cesur fikir ise girdi ve çıktı gömmeleri için aynı matris temsilini kullanmaktı.

# Google Asistanları ve Vertex AI PaLM 2 API

Daha sonra Gemini, Google Workspace, Google Colab Copilot ve Vertex AI PaLM 2 çevrimiçi asistanı ile Google'ın birçok asistanından bazılarını keşfettik. 
- Vertex AI PaLM 2 API'si ile soru-cevap, özetleme ve diğer görevler için olan yolculuğumuza devam ettik. 
- Saatlerce yeni görevler yaratabilir ve tatmin edici sonuçlar elde edebilirdik!

# Vertex AI'nın İnce Ayar İşlemi

Son olarak, dikkatli veri seti hazırlığı gerektiren Vertex AI'nın ince ayar sürecini inceledik.

# Sonuç

LLM Generative transformer modellerinin gücü büyük fırsatlar sunar, ancak zorlu risklerle de gelir. Bir sonraki bölümde, "Devleri Korumak: Büyük Dil Modellerinde Riskleri Azaltma" konusuna geçerek, riskleri azaltırken bu fırsatları nasıl değerlendirebileceğimizi görmek için bir yol haritası çıkarmak zamanıdır.

Bu çeviride Python kodları bulunmamaktadır. Eğer bir kod örneği veya açıklaması istenseydi, ilgili Python kod bloğu ve satır satır açıklaması sağlanacaktı. Örneğin, eğer bir kod örneği aşağıdaki gibi olsaydı:

```python
# Örnek bir Python kodu
def selamla(isim):
    print(f"Merhaba, {isim}!")

selamla("Dünya")
```

Açıklaması şu şekilde olurdu:

1. `def selamla(isim):` satırı `selamla` adında bir fonksiyon tanımlar. Bu fonksiyon bir `isim` parametresi alır.
2. `print(f"Merhaba, {isim}!")` satırı, `isim` değişkenini kullanarak bir selamlama mesajı yazdırır. `f-string` kullanımı, değişkeni string içinde kullanmayı sağlar.
3. `selamla("Dünya")` satırı, tanımlanan `selamla` fonksiyonunu "Dünya" argümanı ile çağırır.

---

