# İngilizce Paragrafın Türkçe Çevirisi

Giriş verisi bu bölümdeki her bir örneği içerecektir. Ardından, istek oluşturduğumuz diyalog fonksiyonuna gönderilir, bu fonksiyon metin değişkeninde yanıtı döndürür. İstek ve yanıt görüntülenir: 
uinput = "Aşağıdaki cümle üzerinde Anlamsal Rol Etiketleme yapın: Bob gerçekten 50 kişiye sadece birkaç saat içinde yemek hazırlayabileceğini düşündü mü?"
text = dialog(uinput) 
# ChatGPT için mesajları hazırlama
print("Görüntüleyici isteği", uinput)
print("ChatGPT SRL:", text)

Kod metninde ChatGPT teriminin kullanıldığına dikkat edin. ChatGPT, OpenAI Üretken Yapay Zeka modellerini kapsayan bir marka haline geldi. Bu durumda uygulanan model GPT-4'dür. GPT-4 ile ChatGPT mantıklı bir yanıt sağlar ve açıklamalar içerir:

Görüntüleyici isteği
Aşağıdaki cümle üzerinde Anlamsal Rol Etiketleme yapın: Bob gerçekten 50 kişiye sadece birkaç saat içinde yemek hazırlayabileceğini düşündü mü?

ChatGPT SRL:
Verilen cümle için Anlamsal Rol Etiketleme aşağıda verilmiştir:
| Argüman       | Rol           | Açıklama                               |
|----------------|----------------|-------------------------------------------|
| Did            | O (Diğerleri)     | Yardımcı fiil, cümlenin ana yapısına dahil değil       |
| Bob            | A0 (Arg0)      | Eylemi gerçekleştiren (düşünmek)    |
| really         | AM-ADV (Değiştirici)| Fiili değiştirmek için kullanılan zarf (düşünmek)       |
| think          | V (Fiil)       | Cümlenin ana fiili (düşünmek)         |
| he             | A1 (Arg1)      | Gömülü cümlenin faili, eylemi gerçekleştiren 
                                    (hazırlamak)                      |
| could prepare  | A1-V (Eylem)  | Gömülü cümlede gerçekleştirilen eylem 
                                    (yemek hazırlamak)                 |
| a meal         | A1-Tema       | Gömülü cümlede hazırlanan nesne 
                                    (bir yemek)                         |
| for 50 people  | A1-Hedef        | Yemeğin hazırlanmasının hedef aldığı kişi sayısı 
                                    |
| in only a few hours| AM-TMP (Zaman)| Eylemin gerçekleştiği sınırlı zaman aralığı 
                                          |
"A1" argümanlarının gömülü cümleye özgü olduğuna dikkat edin (örneğin, "yemek hazırlamak"). Çıktının güvenilir olduğunu, ancak bu bölümün Temel örnek bölümünde GPT-4 ile ChatGPT ile elde edilen yanıttan oldukça farklı olduğunu görebilirsiniz. Güvenilir bir LLM çıktısının kelimesi kelimesine bir çıktı olmadığını görebiliriz. Aşağıdaki örnek genel amaçlı bir model için daha zordur.

## Python Kodlarının Açıklaması

1. `uinput = "Aşağıdaki cümle üzerinde Anlamsal Rol Etiketleme yapın: Bob gerçekten 50 kişiye sadece birkaç saat içinde yemek hazırlayabileceğini düşündü mü?"` 
   - Bu satır, `uinput` değişkenine bir değer atar. Bu değer, modele gönderilecek olan isteği temsil eder.

2. `text = dialog(uinput)`
   - Bu satır, `dialog` adlı bir fonksiyonu çağırır ve `uinput` değişkenini bu fonksiyona argüman olarak geçirir. `dialog` fonksiyonunun döndürdüğü değer `text` değişkenine atanır.

3. `print("Görüntüleyici isteği", uinput)`
   - Bu satır, `uinput` değişkeninin değerini "Görüntüleyici isteği" etiketiyle birlikte konsola yazdırır.

4. `print("ChatGPT SRL:", text)`
   - Bu satır, `text` değişkeninin değerini "ChatGPT SRL:" etiketiyle birlikte konsola yazdırır.

Not: `dialog` fonksiyonunun tanımı bu kod snippet'inde gösterilmemiştir. Bu fonksiyon, büyük olasılıkla bir dil modeli ile etkileşime girerek `uinput` değişkeninde geçirilen isteğe bir yanıt döndürür.

---

