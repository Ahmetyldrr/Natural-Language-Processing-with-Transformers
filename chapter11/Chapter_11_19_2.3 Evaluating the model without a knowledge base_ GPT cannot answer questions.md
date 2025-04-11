# İngilizce Paragrafın Türkçe Çevirisi

Modeli, bir soruyu cevaplamak için Wikipedia makalesini kullanması talimatını veriyoruz: 
```python
query = f"""Aşağıdaki 2022 Kış Olimpiyatları hakkındaki makaleyi sonraki soruyu cevaplamak için kullanın. Cevap bulunamazsa, "Bilmiyorum." yazın. Makale: \"\"\" {wikipedia_article_on_curling} \"\"\" Soru: 2022 Kış Olimpiyatları'nda curlingde altın madalyayı hangi atletler kazandı?"""
```
**OpenAI Kütüphanesinin Kullanılması**
```python
from openai import OpenAI
client = OpenAI()
```
**Modelin Çağrılması ve Cevap Alınması**
```python
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
Cevap doğru:
2022 Kış Olimpiyatları'nda curlingde altın madalyayı kazanan atletler aşağıdaki gibidir:
- Erkekler Curling: İsveç (Niklas Edin, Oskar Eriksson, Rasmus Wranå, Christoffer Sundgren, Daniel Magnusson)
- Kadınlar Curling: Büyük Britanya (Eve Muirhead, Vicky Wright, Jennifer Dodds, Hailey Duff, Mili Smith)
- Karma Çiftler Curling: İtalya (Stefania Constantini, Amos Mosaner)

# Bu Yaklaşımın Özeti

- Bir modelin bilgisi eğitim veri seti ile sınırlıdır. 
- Veri seti gerekli bilgileri içermiyorsa (kesim tarihi, bilgi eksikliği), model bir soruyu cevaplayamaz.
- Bilgiyi mesajın bir parçası olarak kopyalayabilir ve yapıştırabiliriz.
- Klasik veri sorgulama teknikleri ile bir veri tabanında veya dosya sisteminde bir bilgi tabanı oluşturabilir, verileri eşleyebilir ve gerektiğinde otomatik olarak alabiliriz.
- Otomatik bir sistemimiz olur.
- Bilgi tabanlı bir yöntem bir projenin gereksinimlerini karşılayabilir.
- Seçim her projenin gereksinimlerine bağlı olacaktır.
- Bazen özel bir sorgu-arama programı karmaşık heterojen verilerde beklentileri karşılamayabilir.
- Bu durumda, bir bilgi tabanına erişmek için klasik sorgu-arama teknikleri OpenAI'ın ikinci nesil embedding tabanlı arama modellerinin gücüne ulaşamaz.
- Klasik sorgularla oluşturulan bilgi tabanlı bir yaklaşımın sınırlamalarından biri arama fonksiyonunun boyut sayısı olacaktır.
- Klasik bir sorgu ile embedding tabanlı bir arama algoritmasının binlerce boyutunu eşleştiremeyiz!
- Artık embedding tabanlı aramaya dalmaya hazırız.

---

