# Giriş: Bir PyTorch modeli 
# Çıkış: Modeldeki eğitilebilir toplam parametre sayısı

Aşağıdaki Python kodunu kullanarak bir PyTorch modelinin eğitilebilir toplam parametre sayısını hesaplayabilirsiniz.

```python
# Modeldeki eğitilebilir parametre sayısını hesaplamak için gerekli kütüphaneleri içe aktarın
import torch
import torch.nn as nn

# Eğitilebilir parametre sayısını hesaplamak için bir fonksiyon tanımlayın
def count_trainable_parameters(model):
    # Modeldeki eğitilebilir parametre sayısını sayın
    return sum(p.numel() for p in model.parameters() if p.requires_grad)

# Örnek kullanım
class ExampleModel(nn.Module):
    def __init__(self):
        super(ExampleModel, self).__init__()
        self.fc1 = nn.Linear(5, 10)  # Giriş katmanı (5) -> Gizli katman (10)
        self.fc2 = nn.Linear(10, 5)  # Gizli katman (10) -> Çıkış katmanı (5)

    def forward(self, x):
        x = torch.relu(self.fc1(x))  # İleri besleme
        x = self.fc2(x)
        return x

# Modeli oluşturun
model = ExampleModel()

# Eğitilebilir parametre sayısını hesaplayın ve yazdırın
print("Toplam eğitilebilir parametre sayısı:", count_trainable_parameters(model))
```

## Kod Açıklaması

1. `import torch` ve `import torch.nn as nn`: PyTorch kütüphanesini ve PyTorch'un sinir ağları modülünü içe aktarır.
2. `def count_trainable_parameters(model)`: Modeldeki eğitilebilir parametre sayısını hesaplamak için bir fonksiyon tanımlar.
3. `return sum(p.numel() for p in model.parameters() if p.requires_grad)`: 
   - `model.parameters()`: Modelin tüm parametrelerini döndürür.
   - `if p.requires_grad`: Sadece eğitilebilir ( yani `requires_grad` özelliği `True` olan) parametreleri dikkate alır.
   - `p.numel()`: Her bir parametrenin eleman sayısını döndürür (örneğin, bir ağırlık matrisi için bu, matrisin eleman sayısıdır).
   - `sum(...)`: Tüm bu eleman sayılarını toplar ve toplam eğitilebilir parametre sayısını verir.
4. `class ExampleModel(nn.Module)`: PyTorch'un `nn.Module` sınıfından miras alan bir örnek model sınıfı tanımlar.
5. `self.fc1 = nn.Linear(5, 10)` ve `self.fc2 = nn.Linear(10, 5)`: Sırasıyla 5 giriş ve 10 çıkış nöronuna sahip bir doğrusal katman ve 10 giriş, 5 çıkış nöronuna sahip başka bir doğrusal katman tanımlar.
6. `def forward(self, x)`: Modelin ileri besleme işlemini tanımlar.
7. `model = ExampleModel()`: Örnek modeli oluşturur.
8. `print("Toplam eğitilebilir parametre sayısı:", count_trainable_parameters(model))`: Modeldeki eğitilebilir parametre sayısını hesaplar ve yazdırır.

---

