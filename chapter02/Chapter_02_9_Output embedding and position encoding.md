# Çeviri

Decoder alt katmanlarının yapısı çoğunlukla encoder alt katmanları ile aynıdır. Çıktı embedding katmanı ve pozisyon kodlama işlevi, encoder yığınının aynısıdır. Transformer kullanımını araştırırken, Vaswani (2017) tarafından sunulan model ile çalışacağız. Çıktı, öğrenmemiz gereken bir çeviridir. Fransızca çevirisini kullanmayı seçtim: Çıktı=Le chat noir était assis sur le canapé et le chien marron dormait sur le tapis Bu çıktı, İngilizce girdi cümlesinin Fransızca çevirisidir: Girdi=The black cat sat on the couch and the  dog slept on the rug. (Not: orijinal metinde "black brown cat" olarak geçiyor, bu bir hata olabilir, normalde "black cat" veya "brown cat" olmalı). Çıktı kelimeleri, kelime embedding katmanından ve ardından encoder yığınının ilk katmanında olduğu gibi pozisyon kodlama işlevinden geçer. Decoder yığınının çoklu-baş dikkat katmanlarının özel özelliklerine bakalım.

# Python Kodları Yok

Bu metinde python kodları bulunmamaktadır. Eğer bir kod örneği ile birlikte verilseydi, satır satır açıklama yapılabilirdi. Ancak sadece bir ingilizce paragraf çevirisi istenmiştir. 

Eğer bir transformer modeli python kodu ile birlikte açıklanmak istenirse, örnek bir kod aşağıdaki gibi olabilir:

```python
import torch
import torch.nn as nn
import torch.optim as optim

# Encoder ve Decoder tanımları
class Encoder(nn.Module):
    def __init__(self):
        super(Encoder, self).__init__()
        # Encoder katmanları

    def forward(self, x):
        # Encoder ileri besleme
        return x

class Decoder(nn.Module):
    def __init__(self):
        super(Decoder, self).__init__()
        # Decoder katmanları

    def forward(self, x):
        # Decoder ileri besleme
        return x

# Transformer modeli
class Transformer(nn.Module):
    def __init__(self):
        super(Transformer, self).__init__()
        self.encoder = Encoder()
        self.decoder = Decoder()

    def forward(self, x):
        encoder_output = self.encoder(x)
        output = self.decoder(encoder_output)
        return output

# Model oluşturma
model = Transformer()

# Girdi ve çıktı tanımları
input_seq = "The black cat sat on the couch and the dog slept on the rug."
output_seq = "Le chat noir était assis sur le canapé et le chien marron dormait sur le tapis"

# Model eğitimi
# ...
```

Bu kod örneğinde, Encoder ve Decoder sınıfları tanımlanmıştır. Transformer modeli bu iki sınıftan oluşur. `forward` metodu, ileri besleme işlemini tanımlar. Model oluşturulduktan sonra, girdi ve çıktı dizileri tanımlanabilir ve model eğitilebilir. Bu kod örneği çok basit ve eksiktir, gerçek bir transformer modeli daha karmaşıktır ve birçok katmandan oluşur.

---

