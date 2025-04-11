# İngilizce Paragrafın Türkçe Çevirisi

Giriş, bazı kafa karıştırıcı tuzaklar içermektedir: 
input= "Aşağıdaki cümle üzerinde Anlamsal Rol Etiketleme yapın:Alice, kocası her Pazar koşuya giden, bu sırada dans sınıfına gitmekten hoşlanırdı." 
text=dialog(uinput) #ChatGPT için mesajları hazırlama 
print ( "İzleyici isteği" ,uinput) 
print ( "ChatGPT SRL:" ,text) 

Yine, GPT-4, ajanın ilgili ana fiillerinin yeterli olduğuna karar verir ve diğerlerini argüman olarak kabul eder:
İzleyici isteği 
Aşağıdaki cümle üzerinde Anlamsal Rol Etiketleme yapın:Alice, kocası her Pazar koşuya giden, bu sırada dans sınıfına gitmekten hoşlanırdı. 

ChatGPT SRL: 
Anlamsal Rol Etiketleme: 
Fiil: "went" (gidiyordu)
+----+--------------+----------------------------+
|ARG | Argüman      | Metin                      |
+----+--------------+----------------------------+
|A0  | Ajan         | Alice'in kocası            |
|AM-MNR | Yol      | koşuya                     |
|AM-TMP | Zaman    | her Pazar                  |
+----+--------------+----------------------------+
Fiil: "liked" (hoşlanırdı)
+----+--------------+--------------------------------------------+
|ARG | Argüman      | Metin                                      |
+----+--------------+--------------------------------------------+
|A0  | Deneyimleyen | Alice                                      |
|V   | Fiil         | hoşlanırdı                                 |
|A1  | Tema         | bu sırada dans sınıfına gitmek     |
+----+--------------+--------------------------------------------+
Fiil: "go" (gitmek)
+----+--------------+------------------------------------------------+
|ARG | Argüman      | Metin                                          |
+----+--------------+------------------------------------------------+
|A0  | Ajan         | Alice                                          |
|V   | Fiil         | gitmek                                        |
|A2  | Hedef        | dans sınıfına                                |
|AM-TMP | Zaman    | bu sırada                                      |
+----+--------------+------------------------------------------------+ 
Yanıtın her çalıştırdıktan sonra değişebileceğini unutmayın. Prompt'u değiştirseniz bile değişebilir. Şimdi, aşağıdaki örnek belirsiz bir kelime içermektedir.

## Python Kodlarının Açıklaması

1. `text=dialog(uinput)`: Bu satır, `uinput` değişkenini `dialog` fonksiyonuna geçirerek `text` değişkenine atar. Bu, ChatGPT için bir mesaj hazırlama işlemidir.

2. `print ( "İzleyici isteği" ,uinput)`: Bu satır, "İzleyici isteği" başlığı altında `uinput` değişkeninin içeriğini yazdırır.

3. `print ( "ChatGPT SRL:" ,text)`: Bu satır, "ChatGPT SRL:" başlığı altında `text` değişkeninin içeriğini yazdırır.

Bu kodlar, bir kullanıcı girişi (`uinput`) alıp bunu bir `dialog` fonksiyonuna geçirerek bir yanıt (`text`) oluşturur ve hem kullanıcı girişini hem de oluşturulan yanıtı yazdırır. 

### Kodların Adım Adım Çalışması

1. Kullanıcı girişi (`uinput`) alınır.
2. `dialog` fonksiyonu kullanılarak `uinput` işlenir ve `text` oluşturulur.
3. Kullanıcı girişi ve ChatGPT'nin yanıtı yazdırılır.

Not: `dialog` fonksiyonunun nasıl çalıştığı bu örnekten anlaşılmamaktadır. Bu fonksiyonun gerçeklenmesi burada gösterilmemiştir.

---

