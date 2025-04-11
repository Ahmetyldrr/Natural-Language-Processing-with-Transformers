# ChatGPT'nin Başarısının Sırrı: Transformer Modelinin İç Yapısı

ChatGPT, 2022 sonu ve 2023 başlarında aniden popüler olduğunda dünyayı şaşkına çevirdi. Bir yapay zeka, pratik olarak her konuda insana benzer metinler üretebiliyordu. Bu inanılmaz Üretken Yapay Zeka (Generative AI) transformer'ına binlerce görev gönderildi. GPT-4 ile birlikte gelen ChatGPT Plus, son kullanıcıların aklına gelebilecek her görevi yerine getirebiliyor gibi görünüyordu. Ancak OpenAI, önceden tahmin edilemeyen binlerce görev üzerinde ChatGPT'yi önceden eğitmiş olamazdı. Ne de OpenAI, son kullanıcının aklına gelebilecek her şey için GPT modellerini ince ayar yapmış olabilirdi. Elbette, bir transformer modeli, özetleme gibi belirli görevler ve aşağı akış görevleri için eğitilebilir. Ancak ChatGPT gibi modeller, eğitilmedikleri aşağı akış görevlerini yerine getirebilirler. Bu bölüm, bir transformer modelinin iç yapısını inceleyerek, 2. Bölüm'de anlatılan mimarinin aşağı akış görevlerine nasıl uygulandığını gösterir.

## Transformer Modelinin Mimarisi

2. Bölüm'de, Orijinal Transformer'ın mimarisini inceledik. Özellikle, alt katman 1: Çoklu baş dikkat (Multi-head attention) bölümünden başlayarak dikkat başlarını inceledik: Gösterilen skorlar, Q * K matris çarpımının sonucudur. Bu ham skorlar daha sonra anahtar vektörlerinin boyutunun kareköküne bölünerek ölçeklendirilir. Ardından, ham skorlara softmax fonksiyonu uygulanarak 1'e kadar toplanır. Gerekirse, 2. Bölüm'e tekrar göz atmak için zaman ayırın. Bu matematiksel fonksiyonlar, örneğin ChatGPT ile diyalog kurduğumuzda elde ettiğimiz inanılmaz çıktılara nasıl dönüşür? Bu görünür mucizenin nasıl gerçekleştiğini anlamak için transformerların görünmeyen derinliklerine dalmalıyız.

Python kodları bulunmamaktadır, ancak transformer modelinin iç yapısını anlamak için kullanılan bazı matematiksel işlemleri Python koduyla gösterebiliriz.

Örneğin, Q * K matris çarpımı:
```python
import numpy as np

Q = np.array([[1, 2], [3, 4]])
K = np.array([[5, 6], [7, 8]])

scores = np.matmul(Q, K.T)
print(scores)
```
Bu kod, Q ve K matrislerinin çarpımını hesaplar.

Softmax fonksiyonu:
```python
import numpy as np

def softmax(x):
    e_x = np.exp(x - np.max(x))
    return e_x / e_x.sum()

scores = np.array([1, 2, 3, 4, 5])
softmax_scores = softmax(scores)
print(softmax_scores)
```
Bu kod, softmax fonksiyonunu uygular.

Bu kodlar, transformer modelinin iç yapısını anlamak için kullanılan bazı temel matematiksel işlemleri gösterir.

---

