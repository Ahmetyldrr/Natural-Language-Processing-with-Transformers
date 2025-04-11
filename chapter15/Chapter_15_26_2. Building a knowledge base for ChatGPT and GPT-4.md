# Bilgi Tabanı (KB) Oluşturma

Bilgi Tabanı (KB) oluşturmanın amacı, bir kuruluşun bir modele gönderilen bilgi akışını kontrol ederek doğru yönde ilerlemesini sağlamaktır. KB'yi istediğiniz formatta oluşturabilirsiniz: SQL Server, diğer veritabanları, JSON dosyaları, CSV vb. Bu not defterinde, örnek bir KB için Snap-ML Consulting'i kullanacağım. Projeniz için topladığınız bilgileri kullanarak kurumsal veya kişisel bir KB oluşturabilirsiniz. Bu adım, veri oluşturmanın klasik bir yöntemidir. Örneğin, web siteleri oluştururken, görünürlüğümüzü artırmak ve arama motorlarına yardımcı olmak için meta veriler ve anahtar kelimeler gireriz. Aynı şey, dönüştürücü sohbet modellerimiz için de geçerlidir.

Not: KB'nizde istediğiniz kadar iddia oluşturabilirsiniz. Tek maliyet, verilerinizin kapladığı alan ve veri kümenizin bakımı olacaktır.

Aşağıdaki KB, asistanın rolünü açıklamak için iddialarla etkinleştirilmiştir:

```python
assert1 = {'role': 'assistant', 'content': 'Snap-LM Consulting çalışma saatleri: Pazartesi - Cuma 9:00 - 17:00. Hizmetler: uzman sistemler, kural tabanlı sistemler, makine öğrenimi, derin öğrenme, dönüştürücü modeller.'}
assert2 = {'role': 'assistant', 'content': 'Hizmetler: uzman sistemler, kural tabanlı sistemler, makine öğrenimi, derin öğrenme, dönüştürücü modeller.'}
assert3 = {'role': 'assistant', 'content': 'Hizmetler: OpenAI GPT-3 modellerinin ince ayarlanması, veri kümelerinin tasarlanması, bilgi tabanlarının tasarlanması.'}
assertn = {'role': 'assistant', 'content': 'Hizmetler: Bilgi tabanı ve SEO anahtar kelime yöntemlerini kullanarak gelişmiş istem mühendisliği.'}
```

# Bilgi Tabanını Veri Kümesi Olarak Kullanma

```python
kbt = []  # Boş bir liste oluştur
kbt.append(assert1)  # assert1'i listeye ekle
kbt.append(assert2)  # assert2'i listeye ekle
kbt.append(assert3)  # assert3'ü listeye ekle
kbt.append(assertn)  # assertn'i listeye ekle
```

# Bilgi Tabanını Pandas DataFrame'de Görüntüleme

```python
import pandas as pd  # pandas kütüphanesini içe aktar
df = pd.DataFrame(kbt)  # kbt listesini DataFrame'e dönüştür
df  # DataFrame'i görüntüle
```

Çıktı, kalite kontrolü için KB'yi görüntüler:

# Şekil 15.4: Kalite Kontrolü için KB

Şimdi, kullanıcı isteklerini ayrıştırmak için anahtar kelimeler ekleyeceğiz.

---

