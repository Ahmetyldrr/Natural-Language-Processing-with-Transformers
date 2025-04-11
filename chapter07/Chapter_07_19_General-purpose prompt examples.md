# OpenAI Platformundan Örneklerin İncelenmesi

https://platform.openai.com/examples adresine gidin. Bu sayfa, Şekil 7.8'de gösterildiği gibi inceleyebileceğimiz birçok örnek göstermektedir:
Şekil 7.8: OpenAI tarafından sağlanan prompt örneklerinden birkaç tanesi

OpenAI GPT modellerinin bu görevleri yerine getirmek için önceden eğitilmediğini unutmayın. Sistemin sihirli tarafı, GPT'nin bu görevler için eğitilmemiş olmasıdır. 
Grammar correction (Dilbilgisi düzeltme) üzerine tıkladığımızda, Python'da bir örneğe erişebiliriz:
```python
# Gerekli kütüphanelerin import edilmesi
import os 
import openai

# OpenAI API anahtarının ortam değişkeninden alınması
openai.api_key = os.getenv("OPENAI_API_KEY")

# ChatCompletion.create metodunun çağrılması
response = openai.ChatCompletion.create(
  # Kullanılacak modelin belirlenmesi
  model="gpt-3.5-turbo",
  # Mesajların boş bir list olarak ayarlanması
  messages=[],
  # Sıcaklık parametresinin 0 olarak ayarlanması
  temperature=0,
  # Maksimum token sayısının 256 olarak ayarlanması
  max_tokens=256
)
```
Ayrıca, Soru-Cevap gibi bir örneği çalıştırmak, sorular sormak ve parametreleri değiştirmek için OpenAI Playground'a gidebiliriz: https://platform.openai.com/playground/. Birçok NLP görevi çalıştırabilir, parametreleri değiştirebilir ve kodu görüntüleyebilirsiniz.

# Microsoft Office 365 Copilot için ChatGPT

ChatGPT for Microsoft Office 365 Copilot, üretken transformer teknolojisinin kapılarını milyonlarca son kullanıcıya, dahil olmak üzere bize açar.

---

