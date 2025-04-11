# Sadhika Malladi, Tianyu Gao, Eshaan Nichani, Alex Damian, Jason D. Lee, Danqi Chen, ve Sanjeev Arora , 2023, Yalnızca İleri Yönde Geçişlerle Dil Modellerini Fine-Tuning Yapmak : https://arxiv.org/abs/2305.17333

Bu metin bir makale referansını ve topluluk davetini içermektedir. Şimdi, bu metni birebir Türkçeye çevirelim:

Sadhika Malladi, Tianyu Gao, Eshaan Nichani, Alex Damian, Jason D. Lee, Danqi Chen, ve Sanjeev Arora , 2023, Yalnızca İleri Yönde Geçişlerle Dil Modellerini İnce Ayar Yapmak : https://arxiv.org/abs/2305.17333 

Discord'da Topluluğumuza Katılın 
Yazarlar ve diğer okuyucularla tartışmalar için topluluğumuzun Discord alanına katılın: https://www.packt.link/Transformers

Bu çeviride herhangi bir Python kodu bulunmamaktadır. 

Eğer verdiğiniz metinde gizli bir python kodu varsa lütfen belirtin ki size satır satır açıklayabileyim. 

Ancak eğer isterseniz verdiğiniz ingilizce metni python kodu içinde işleyen basit bir örnek yapabilirim.

```python
# İngilizce metni çevirmek için basit bir fonksiyon
def translate_text(text):
    # Burada çeviri işlemini yapacak kodlar yer alacak
    # Basit bir örnek olması için sadece print ediyoruz
    print("Çeviri işlemi yapılacak metin: ", text)

# Verilen metni çeviri fonksiyonuna gönder
text = "Sadhika Malladi, Tianyu Gao, Eshaan Nichani, Alex Damian, Jason D. Lee, Danqi Chen, and Sanjeev Arora , 2023, Fine-Tuning Language Models with Just Forward Passes : https://arxiv.org/abs/2305.17333 Join our community on Discord Join our community’s Discord space for discussions with the authors and other readers: https://www.packt.link/Transformers"
translate_text(text)
```

Bu kod, ingilizce metni `translate_text` fonksiyonuna gönderir ve fonksiyon da bu metni print eder. Gerçek bir çeviri işlemi için bu fonksiyon içine bir çeviri API'si entegre edilebilir. 

Örneğin Google Translate API kullanabilirsiniz.

```python
from googletrans import Translator

def translate_text(text):
    translator = Translator()
    translation = translator.translate(text, dest='tr')
    return translation.text

text = "Sadhika Malladi, Tianyu Gao, Eshaan Nichani, Alex Damian, Jason D. Lee, Danqi Chen, and Sanjeev Arora , 2023, Fine-Tuning Language Models with Just Forward Passes : https://arxiv.org/abs/2305.17333 Join our community on Discord Join our community’s Discord space for discussions with the authors and other readers: https://www.packt.link/Transformers"
print(translate_text(text))
```

Bu kod, ingilizce metni Türkçeye çevirir.

---

