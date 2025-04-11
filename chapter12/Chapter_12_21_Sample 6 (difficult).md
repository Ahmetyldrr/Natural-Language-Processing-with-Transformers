# Çeviri
Giriş, bu bölümün Zor örnek kısmındaki ile aynıdır: 
uinput= "Aşağıdaki cümle üzerinde Anlamsal Rol Etiketleme yapın: Şimdi, diski buzlayın adamlar!" 
text=dialog(uinput) # ChatGPT için mesajları hazırlama 
print ( "İzleyici isteği" ,uinput) 
print ( "ChatGPT SRL:" ,text) 

Bu çalışmada, GPT-4, hokey jargonında "ice" fiilini tespit eder:
İzleyici isteği 
Aşağıdaki cümle üzerinde Anlamsal Rol Etiketleme yapın: Şimdi, diski buzlayın adamlar!
ChatGPT SRL: 
 Sağladığınız cümle gayet kolokyual bir ifade veya argo terim gibi görünüyor. 
Anlamsal Rol Etiketleme standart olmayan dil ile daha az doğru olabilir. 
Ancak, bir deneme yapacağım: 
Cümle: Şimdi, diski buzlayın adamlar!
Roller:
1. Zamansal Değiştirici: Şimdi
2. Yüklem: buzla (yenmek veya geçmek)
3. Nesne: disk
4. Hedef: adamlar

|  Bileşen       | Cümledeki Rol  | 
|----------------|-------------------|
|  Şimdi         | Zamansal Değiştirici | 
|  buzla         | Yüklem         | 
|  disk          | Nesne            | 
|  adamlar       | Hedef            | 

GPT-4'ün algoritmasının rastgele doğası nedeniyle başka bir çalışmada doğru cevabı vermeyebileceğini unutmayın. 
Bu, bir SRL görevinin kapsamını sınırlayabilir. 
Şimdi SRL'in kapsamını ve sınırlarını keşfetmemizi sonlandıralım.

# Kod Açıklaması

Python kodları aşağıdaki gibidir:
```python
uinput = "Perform Semantic Role Labeling on the following sentence:Now, ice pucks guys!"
text = dialog(uinput)  # ChatGPT için mesajları hazırlama
print("Viewer request", uinput)
print("ChatGPT SRL:", text)
```
1. `uinput = "Perform Semantic Role Labeling on the following sentence:Now, ice pucks guys!"` 
   - Bu satır, `uinput` değişkenine bir string atar. Bu string, bir cümle üzerinde Anlamsal Rol Etiketleme (SRL) yapma isteğini temsil eder.

2. `text = dialog(uinput)` 
   - Bu satır, `dialog` adlı bir fonksiyonu `uinput` parametresi ile çağırır ve sonucu `text` değişkenine atar. 
   - `dialog` fonksiyonunun ne yaptığını bilmiyoruz çünkü tanımı verilmedi, ancak ChatGPT ile etkileşim kurduğu anlaşılıyor.

3. `print("Viewer request", uinput)` 
   - Bu satır, "İzleyici isteği" ve `uinput` değişkeninin değerini konsola yazdırır.

4. `print("ChatGPT SRL:", text)` 
   - Bu satır, "ChatGPT SRL:" ve `text` değişkeninin değerini konsola yazdırır. `text`, muhtemelen ChatGPT'nin SRL sonucunu içerir.

---

