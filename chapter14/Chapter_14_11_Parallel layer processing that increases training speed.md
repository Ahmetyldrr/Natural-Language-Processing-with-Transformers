# Transformer Bloğu Nedir?
Bir transformer bloğu, 2. Bölümde, Transformer Modelinin Mimarisine Başlarken'de açıklanan bir hesaplama birimidir. Transformer bloğu esas olarak bir dikkat katmanı, bir ileri beslemeli sinir ağı (MLP) ve bir katman normalizasyon katmanıyla oluşturulur.

# Klasik Transformer Bloğu Denklemi
Klasik transformer bloğunu şu denklemle temsil edebiliriz: 
```python
y = x + MLP(LayerNorm(x + Attention(LayerNorm(x))))
```
Bu formülasyonda, girdi olarak gömülü verileri temsil eden `x`in, dikkat katmanına eklendiğini görebiliriz. Bu, başlangıç gömme değerlerini kaybetmememiz için bir artık bağlantı sağlar. Ayrıca, MLP'nin, 2. Bölüm'de gördüğümüz gibi, kendisinden önce gelen tüm süreci kapsadığını görebiliriz. Son olarak, başka bir artık bağlantı (`x + MLP`) görüyoruz, bu da başlangıç gömme değerleri için herhangi bir bilgiyi kaybetmediğimizden emin olmamızı sağlar. Genel fikir, MLP'nin önceki alt katmanları ve normalizasyonları kapsadığı yönündedir. Dikkat alt katmanı, gömme girdi alt katmanını takip eder ve MLP tüm bunları kapsar.

# Google AI Araştırma Takımının Yapılandırma Değişikliği
2. Bölüm'ü dikkatlice okursanız, "Yani ne olmuş?" diye düşünmüş olabilirsiniz. Şimdi, Google AI araştırma takımının ne yaptığına bakalım! Onlar, dikkat alt katmanını ve MLP'yi paralel olarak çalıştırdılar:
```python
y = x + MLP(LayerNorm(x)) + Attention(LayerNorm(x))
```
Evet, denklem doğru! MLP, dikkat alt katmanından sonra gelmez. Paralel olarak çalışır! Sistemin kazandığı hızı hayal edebilirsiniz.

Python kodu olarak bu denklemleri aşağıdaki şekilde gösterebiliriz:
```python
import torch
import torch.nn as nn

# Klasik Transformer Bloğu
class ClassicTransformerBlock(nn.Module):
    def __init__(self, attention, mlp, layer_norm):
        super(ClassicTransformerBlock, self).__init__()
        self.attention = attention
        self.mlp = mlp
        self.layer_norm = layer_norm

    def forward(self, x):
        # x = girdi olarak gömülü veriler
        attention_output = self.attention(self.layer_norm(x))
        x = x + attention_output
        x = self.layer_norm(x)
        mlp_output = self.mlp(x)
        y = x + mlp_output
        return y

# Google AI Transformer Bloğu
class GoogleAITransformerBlock(nn.Module):
    def __init__(self, attention, mlp, layer_norm):
        super(GoogleAITransformerBlock, self).__init__()
        self.attention = attention
        self.mlp = mlp
        self.layer_norm = layer_norm

    def forward(self, x):
        # x = girdi olarak gömülü veriler
        layer_norm_x = self.layer_norm(x)
        attention_output = self.attention(layer_norm_x)
        mlp_output = self.mlp(layer_norm_x)
        y = x + attention_output + mlp_output
        return y
```
Bu python kodlarında `ClassicTransformerBlock` klasik transformer bloğunu, `GoogleAITransformerBlock` ise Google AI araştırma takımının yapılandırma değişikliğini temsil etmektedir. 

- `forward` methodu, her iki blok için de girdi `x`i işler ve çıktı `y`i döndürür.
- `ClassicTransformerBlock`da önce dikkat katmanı uygulanır, sonra `x` ile toplanır, daha sonra layer norm uygulanır ve MLP ye verilir. 
- `GoogleAITransformerBlock`da ise dikkat katmanı ve MLP paralel olarak çalışır, layer norm uygulanmış `x` her iki katmana da verilir ve çıktıları `x` ile toplanır.

---

