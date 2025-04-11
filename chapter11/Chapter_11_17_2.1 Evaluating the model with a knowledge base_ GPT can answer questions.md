# Bellek açısından modelin değerlendirilmesi

Bu bölüm, modeli eğitim verilerine bağlı olan bellek açısından değerlendirecektir. Örneğin, Ocak 2024'te GPT-3.5-turbo ve GPT-4, Nisan 2023'ün ötesindeki soruları cevaplayamaz. Veri kümelerinin kesinti tarihleri vardır ve eğitim için muazzam makine ve insan kaynakları gerektirir. Çok küçük bir modeli kolayca eğitebiliriz, ancak GPT-4'ün soruları anlama yeteneğine sahip olacak mı? Bu, her projenin gereksinimlerine bağlıdır. Her durumda, GPT-3.5-turbo'nun bir bellek sorunu vardır. Bir veri kümesiyle ince ayar yapmayı deneyebilirsiniz. Ancak, ertesi gün, örneğin son spor etkinlikleri hakkında bir soruyu cevaplayamayacaktır. Modeli sürekli olarak ince ayar yapmak maliyetli olabilir. GPT-3.5-turbo'nun uzun vadeli belleği çalışır, ancak kısa vadeli belleği yoktur çünkü veri kümesinde bu bilgi yoktur.

Örneğin, not defterinin aşağıdaki hücresinde, 2022 Olimpiyatları hakkında bir soruyu cevaplayamaz:

```python
# 2022 Olimpiyatları hakkında bir örnek soru
query = '2022 Kış Olimpiyatları\'nda curlingde altın madalyayı hangi atletler kazandı?'
response = client.chat.completions.create(
    messages=[
        {'role': 'system', 'content': '2022 Kış Olimpiyatları hakkında soruları cevaplarsınız.'},
        {'role': 'user', 'content': query},
    ],
    model=GPT_MODEL,
    temperature=0,
)
print(response.choices[0].message.content)
```

Yanıt aşağıdaki gibi olacaktır:
"Bir AI dil modeli olarak, gerçek zamanlı verilere sahip değilim. Ancak, genel bilgiler sağlayabilirim. 2022 Kış Olimpiyatları'nda curlingde altın madalya kazananlar etkinlik sırasında belirlenecektir. Kazananlar, erkekler ve kadınlar curling yarışmalarında ilk sırada yer alan takımlar olacaktır. Belirli kazananları öğrenmek için Uluslararası Olimpiyat Komitesi'nin resmi web sitesini veya güvenilir spor haber kaynaklarını kontrol edebilirsiniz."

Model, soruyu cevaplayamaz çünkü gerekli bilgiye sahip değildir. OpenAI kesinlikle yeni bir model üretecektir. Ancak, başka bir kesinti tarihi olacaktır. Yeni modeli denerseniz, eğitim veri kümesinde olmayan soruları yine de cevaplayamayacaktır. Modelimize yaptığımız isteğe bir bilgi tabanı eklemeyi deneyelim.

### Python Kodunun Açıklaması

1. `query = '2022 Kış Olimpiyatları\'nda curlingde altın madalyayı hangi atletler kazandı?'` 
   - Bu satır, modele sorulacak soruyu tanımlar.

2. `response = client.chat.completions.create(...)`
   - Bu satır, OpenAI'ın GPT modelini kullanarak soruyu cevaplamak için bir istek gönderir.

3. `messages=[{'role': 'system', 'content': '2022 Kış Olimpiyatları hakkında soruları cevaplarsınız.'}, {'role': 'user', 'content': query}]`
   - Bu bölüm, modele gönderilen mesajları tanımlar. 
   - İlk mesaj, modelin rolünü tanımlar (bu durumda, 2022 Kış Olimpiyatları hakkında soruları cevaplamak).
   - İkinci mesaj, kullanıcının sorusunu içerir.

4. `model=GPT_MODEL`
   - Bu satır, kullanılacak GPT modelini belirtir.

5. `temperature=0`
   - Bu satır, modelin cevaplarını ne kadar yaratıcı veya deterministik olacağını kontrol eder. 
   - Sıfır değeri, modelin daha deterministik ve daha az yaratıcı cevaplar vermesini sağlar.

6. `print(response.choices[0].message.content)`
   - Bu satır, modelin cevabını yazdırır. 
   - `response.choices[0].message.content`, modelin ürettiği cevabı içerir.

---

