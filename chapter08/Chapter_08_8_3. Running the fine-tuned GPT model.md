# Model Eğitimi ve Tamamlama Görevi

Model eğitildi ve bir tamamlama görevi için hazır. Bildirimleri etkinleştirdiyseniz, ince ayar işi tamamlandığında bir e-posta alacaksınız. Aşağıdaki gibi bir mesaj alacaksınız: İnce ayar işiniz ftjob-xxxxxxxxxxxx başarıyla tamamlandı ve kullanımınız için yeni bir model ft:babbage-002:personal::xxxxxxxx oluşturuldu.

# Eğitilen Modeli Deneme

OpenAI Playground'da deneyin, ince ayar UI'de eğitim sonuçlarını görüntüleyin veya Sohbet Tamamlama veya Eski Tamamlama API'sini kullanarak uygulamanıza entegre edin. Playground'da tamamlamaları etkinleştirebilir, ince ayarlı modelinizi seçebilir ve test edebilirsiniz: 
Şekil 8.3: Playground'da ince ayarlı model test ediliyor 

İstemin "Zaman ve uzay açıklamasını yaz:" olduğu bir kişisel ince ayarlı model ile düşük sıcaklıkta (daha kesin): 
Şekil 8.4: Düşük sıcaklıkta seçilen ince ayarlı model 

Model, ilginç bir şekilde spekülatif sorularla cevap verdi. Diyalogunuzu kaydedebilir veya kaynak kodunu görüntüleyebilirsiniz, ardından programınıza kopyalayıp yapıştırabilirsiniz: 
Şekil 8.5: Diyalogu kaydetme veya kodu görüntüleme 

# Eğitilen Modeli Uygulama

Şimdi ince ayarlı modeli orijinal model gibi uygulayacağız. Modeli doğrudan çalıştırabilir veya bazı düzenlemeler yapabilirsiniz. Bu bölümde modelin bir tamamlama görevi için çalıştırılacaktır. 

İlk olarak, ince ayarlı modelin tamamlamasını istediğimiz bir metin içeriği tanımlıyoruz:
```python
# Tamamlanacak metin
text_content = "Uzay ve zaman, insan muhakemesinin temel faktörleridir. İnsan zihni uzay ve zaman algıları olmadan düşünemez."
#print(text_content)
```
Gerekirse bakım için her adımı yazdırabilirsiniz.

Ardından, metin içeriğimizi ekleyerek istemi talimatlarla sağlıyoruz:
```python
prompt = "Aşağıdaki metni bir bilim adamı ve filozofmuş gibi devam ettir" + text_content
#print(prompt)
```
Şimdi, eğitilen model ile herhangi bir tamamlama modeli gibi görevi çalıştırıyoruz:
```python
response = client.completions.create(
    model="[EĞİTİLEN MODELİNİZ]",
    prompt=prompt,
    max_tokens=1000,
    temperature=0.8
)
#print(response)
```
Tamamlamayı çıkarabilir ve görüntüleyebiliriz:
```python
# Yanıtta herhangi bir seçim olup olmadığını kontrol edin
if response.choices:
    # İlk seçimi alın (index 0)
    first_choice = response.choices[0]
    # İlk seçimin metnini yazdırın
    print("Modelin Tamamlama:", first_choice.text)
else:
    print("Yanıtta seçim döndürülmedi")
```
Aşağıdaki alıntı, ince ayarın çalıştığını gösteriyor. Ancak çıktı, daha büyük bir veri kümesi ve daha fazla eğitim gerekebileceğini gösteriyor:
Modelin Tamamlama:  Eğer kendimiz hakkında düşünemezsek, başkaları hakkında da düşünemeyiz.
Uzay nedir? Uzay, bir şeyin bilincinde olduğum, ancak kendimi algılayamadığım bilinçli alandır.
Zaman nedir? Zaman, içsel bilinçteki bir dizi olayın bilinçli deneyimidir, böylece onları geçmişte veya belirli bir zamanda düşünürüm.
Bu nedenle, uzay ve zaman tüm düşüncenin temel koşullarıdır,…

# Yanıt Bilgilerini Görüntüleme

Yanıt hakkındaki bazı bilgileri de görüntüleyebilirsiniz:
```python
# Seçimleri biçimlendirme
for i, choice in enumerate(response.choices):
    print(f"Seçim {i}:")
    print("  Bitiş Nedeni:", choice.finish_reason)
    print("  İndeks:", choice.index)
    print("  Log olasılıkları:", choice.logprobs)
    print("  Metin:", choice.text)

# Kullanımı biçimlendirme
print("Kullanım:")
print("  Tamamlama Tokenları:", response.usage.completion_tokens)
print("  İstemin Tokenları:", response.usage.prompt_tokens)
print("  Toplam Token:", response.usage.total_tokens)
```
Çıktı, yanıttaki bazı temel özelliklerin biçimlendirilmiş bir açıklamasıdır:
Tamamlama Kimliği: cmpl-8gHgWGl0QuWIqi8swO80pEp9Lwdbs
Oluşturuldu: 1705088448
Model: ft:babbage-002:personal::xxxxxxx
Nesne Türü: text_completion
Seçim 0:
  Bitiş Nedeni: length
  İndeks: 0
  Log olasılıkları: None
  Metin:  Eğer kendimiz hakkında düşünemezsek, başkaları hakkında da düşünemeyiz…(alıntı)

# Yönetim Fonksiyonlarını Ekleme

Şimdi bazı yönetim fonksiyonları ekleyeceğiz.

---

