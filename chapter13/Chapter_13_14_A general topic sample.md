# Bu Alt Bölümde T5 Modeli Kullanarak Metin Özetleme

Bu alt bölümde, Project Gutenberg tarafından yayınlanan bir metni T5 modeli aracılığıyla çalıştıracağız. Özetleme fonksiyonumuzu test etmek için bu örneği kullanacağız. İsterseniz başka bir metni kopyalayıp yapıştırabilir veya kod ekleyerek bir metin yükleyebilirsiniz. Ayrıca, seçtiğiniz bir veri setini yükleyebilir ve özetleri bir döngü içinde çağırabilirsiniz. Bu bölümdeki programın amacı, T5'in nasıl çalıştığını görmek için birkaç örnek çalıştırmaktır.

## Giriş Metni
Giriş metni, Amerika Birleşik Devletleri'nin Bağımsızlık Bildirgesi'ni içeren Project Gutenberg e-kitabının başlangıcını içerir:
```python
text = """ We hold these truths to be self-evident, that all men are created equal, that they are endowed by their Creator with certain unalienable Rights, that among these are Life, Liberty, and the pursuit of Happiness. That to secure these rights, Governments are instituted among Men, deriving their just powers from the consent of the governed, That whenever any Form of Government becomes destructive of these ends, it is the Right of the People to alter or to abolish it, and to institute new Government, laying its foundation on such principles and organizing its powers in such form, as to them shall seem most likely to effect their Safety and Happiness.  Prudence, indeed, will dictate that Governments long established should not be changed for light and transient causes; and accordingly all experience hath shown, that mankind are more disposed to suffer, while evils are sufferable, than to right themselves by abolishing the forms to which they are accustomed.  But when a long train of abuses and usurpations, pursuing invariably the same Object evinces a design to reduce them under absolute Despotism, it is their right, it is their duty, to throw off such Government, and to provide new Guards for their future security. --Such has been the patient sufferance of these Colonies; and such is now the necessity which constrains them to alter their former Systems of Government. The history of the present King of Great Britain is a history of repeated injuries and usurpations, all having in direct object the establishment of an absolute Tyranny over these States.  To prove this, let Facts be submitted to a candid world. """
```

## Özetleme Fonksiyonunun Çağırılması
Daha sonra, özetleme fonksiyonumuzu çağırır ve özetlemek istediğimiz metni ve özetin maksimum uzunluğunu göndeririz:
```python
print("Number of characters:", len(text))
summary = summarize(text, 50)
```
Burada `len(text)` fonksiyonu, `text` değişkenindeki karakter sayısını hesaplar.

## Çıktının Biçimlendirilmesi
Çıktı sarılır:
```python
wrapped_summary = textwrap.fill(summary, width=70)
print("\nSummarized text: \n", wrapped_summary)
```
`textwrap.fill()` fonksiyonu, özet metni belirli bir genişlikte (bu örnekte 70 karakter) satırlara böler.

## Sonuç
Çıktı, 1632 karakterlik orijinal metni ve özeti gösterir:
```
Number of characters: 1632
Text to summarize: We hold these truths to be self-evident, that…
Summarized text:
 we hold these truths to be self-evident that all men are created
equal,that they are endowed by their Creator with certain unalienable
Rights. that whenever any Form of Government becomes destructive of
these ends,
```
Eksik cümleleri tespit etmek için bazı işlem sonrası işlemler gerekebilir. Maksimum uzunluğu artırmak ve sonra eksik cümleleri tespit etmek gerekebilir.

## T5 ile Daha Zor Özetleme
Şimdi T5'i daha zor bir özetleme için kullanalım.

---

