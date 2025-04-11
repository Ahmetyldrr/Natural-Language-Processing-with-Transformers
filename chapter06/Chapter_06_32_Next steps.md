# Sıfırdan İki Transformatör Eğitimi

Sıfırdan iki transformatör eğittiniz. Kişisel veya kurumsal ortamınızda neler yapabileceğinizi hayal etmek için biraz zaman ayırın. Belirli bir görev için bir veri kümesi oluşturabilir ve sıfırdan eğitebilirsiniz. BERT ailesi, GPT modelleri, T5 ve daha fazlasında eğitim için birçok başka Hugging Face modeli mevcuttur! İlgi alanlarınızı veya şirket projelerinizi transformatör yapılandırma kitlerinin büyüleyici dünyasıyla denemek için kullanın!

## Modeli Paylaşma

Beğendiğiniz bir modeli oluşturduktan sonra, onu Hugging Face topluluğuyla paylaşabilirsiniz. Modeliniz Hugging Face modelleri sayfasında görünecektir: https://huggingface.co/models . Modelinizi bu sayfada açıklanan talimatları kullanarak birkaç adımda yükleyebilirsiniz: https://huggingface.co/transformers/model_sharing.html . Ayrıca, Hugging Face topluluğunun kişisel ve profesyonel projeleriniz için yeni fikirler edinmek üzere paylaştığı modelleri indirebilirsiniz.

İngilizce paragrafın birebir Türkçe çevirisi yukarıdaki gibidir.

Python kodları bulunmamaktadır, eğer çeviri için kullanılan bir kod olsaydı bu şekilde açıklanabilirdi:

Örneğin, eğer bir python kodu olsaydı:
```python
# İngilizce metni çevirmek için gerekli kütüphaneleri içe aktarma
import translators as ts

# İngilizce metni tanımlama
english_text = """You have trained two transformers from scratch. Take some time to imagine what you could do in your personal or corporate environment. You could create a dataset for a specific task and train it from scratch. Many other Hugging Face models are available for training in the BERT family, GPT models, T5, and more! Use your areas of interest or company projects to experiment with the fascinating world of transformer construction kits! Once you have made a model you like, you can share it with the Hugging Face community. Your model will appear on the Hugging Face models page: https://huggingface.co/models . You can upload your model in a few steps using the instructions described on this page: https://huggingface.co/transformers/model_sharing.html . You can also download models the Hugging Face community has shared to get new ideas for your personal and professional projects."""

# İngilizce metni Türkçe'ye çevirme
turkish_text = ts.google(english_text, from_language='en', to_language='tr')

# Çevirilen metni yazdırma
print(turkish_text)
```
Bu kod, `translators` kütüphanesini kullanarak İngilizce metni Türkçe'ye çevirir. 

1. `import translators as ts`: Gerekli kütüphaneyi içe aktarır.
2. `english_text = """..."""`: İngilizce metni tanımlar.
3. `turkish_text = ts.google(english_text, from_language='en', to_language='tr')`: İngilizce metni Türkçe'ye çevirir.
4. `print(turkish_text)`: Çevirilen metni yazdırır.

---

