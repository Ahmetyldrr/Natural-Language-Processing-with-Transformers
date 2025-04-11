# Doğru/Yanlış Soruları Çevirisi

Aşağıdaki İngilizce paragrafın birebir Türkçe çevirisi yapılmıştır.

İngilizce Paragraf:
"It’s impossible to force ChatGPT to harass somebody. (True/False) Hallucinations are only for humans. (True/False) Privacy is taken seriously on the leading cloud platforms. (True/False) APIs pose no risk. (True/False) Harmful content can be filtered. (True/False) A moderation model is 100% reliable. (True/False) A rule base is useless when using LLMs. (True/False) A knowledge base will make the transformer ecosystem more reliable. (True/False) We cannot add information to a prompt. (True/False) Prompt engineering requires more effort than prompt design. (True/False)"

Türkçe Çevirisi:
"ChatGPT'yi birine saldırmaya zorlamak imkansızdır. (Doğru/Yanlış) Halüsinasyonlar sadece insanlara özgüdür. (Doğru/Yanlış) Lider bulut platformlarında gizlilik ciddiye alınır. (Doğru/Yanlış) API'ler hiçbir risk oluşturmaz. (Doğru/Yanlış) Zararlı içerik filtrelenebilir. (Doğru/Yanlış) Bir moderasyon modeli %100 güvenilirdir. (Doğru/Yanlış) Bir kural tabanı, LLMs kullanırken işe yaramaz. (Doğru/Yanlış) Bir bilgi tabanı, transformer ekosistemini daha güvenilir kılacaktır. (Doğru/Yanlış) Bir isteme bilgi ekleyemeyiz. (Doğru/Yanlış) İstem mühendisliği, istem tasarımından daha fazla çaba gerektirir. (Doğru/Yanlış)"

Bu çeviride Python kodları bulunmamaktadır. Sadece basit bir metin çevirisi yapılmıştır.

Eğer bir Python kodu ile çeviri yapmak isteseydik, aşağıdaki gibi bir kod kullanabilirdik:

```python
import googletrans

# Çeviri yapılacak metin
metin = """It’s impossible to force ChatGPT to harass somebody. (True/False) Hallucinations are only for humans. (True/False) Privacy is taken seriously on the leading cloud platforms. (True/False) APIs pose no risk. (True/False) Harmful content can be filtered. (True/False) A moderation model is 100% reliable. (True/False) A rule base is useless when using LLMs. (True/False) A knowledge base will make the transformer ecosystem more reliable. (True/False) We cannot add information to a prompt. (True/False) Prompt engineering requires more effort than prompt design. (True/False)"""

# Çevirici nesnesini oluştur
cevirici = googletrans.Translator()

# Metni çevir
sonuc = cevirici.translate(metin, dest='tr')

# Çeviri sonucunu yazdır
print(sonuc.text)
```

Bu kod, `googletrans` kütüphanesini kullanarak verilen İngilizce metni Türkçe'ye çevirir.

1. `import googletrans`: Googletrans kütüphanesini içe aktarır. Bu kütüphane, Google Translate API'sini kullanarak metin çevirisi yapar.
2. `metin = "..."`: Çeviri yapılacak metni bir değişkene atar.
3. `cevirici = googletrans.Translator()`: Çevirici nesnesini oluşturur.
4. `sonuc = cevirici.translate(metin, dest='tr')`: Metni Türkçe'ye çevirir. `dest='tr'` parametresi, çeviri dilini Türkçe olarak belirler.
5. `print(sonuc.text)`: Çeviri sonucunu yazdırır.

---

