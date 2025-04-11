# Prompt Tasarımı ve Prompt Mühendisliği

Prompt tasarımı ve prompt mühendisliği benzer görünen ancak sizi bir sonraki seviyeye götürecek iki terimdir. Prompt tasarımı basitçe son kullanıcının bir soru veya talimat yazmasını ve bir sohbet modeline göndermesini gerektirir. Prompt mühendisliği, sohbet modelini yönlendirmek için karmaşık mesajlar oluşturmayı içerir. Örneğin, bazen ChatGPT bir soruyu cevaplayamaz çünkü eğitim verileri gerekli bilgileri içermez. Belki de veri kümesi bir olaydan önce oluşturulmuştur, örneğin. Veya bilgiler başlangıçtan itibaren veri kümesinde değildir. Bu durumda, prompt tasarımından prompt mühendisliğine geçmeliyiz, ki bu bölümde RAG'ı içerir. Bu bölümde, basit bir son kullanıcı promptundan tamamen mühendislik yapılmış embedding tabanlı bir prompta nasıl geçileceğini keşfedeceksiniz. Metin embeddinginin temellerini gözden geçirerek başlayacağız.

İlgili python kodları bulunmamaktadır, eğer ek olarak bir kod verilseydi, satır satır açıklama yapabilirdim. 

Örnek bir python kodu ve açıklaması şöyle olabilir:

```python
# Metin embedding işlemi için gerekli kütüphane
import numpy as np

# Örnek bir metin dizisi
text = "Bu bir örnek metindir."

# Embedding işlemi için basit bir fonksiyon
def text_embedding(text):
    # Bu fonksiyon basitçe metni embeddinge çevirir
    # Gerçek uygulamalarda bu işlem daha karmaşıktır
    embedding = np.random.rand(1, 128)  # 128 boyutlu embedding vektörü oluştur
    return embedding

# Metni embeddinge çevir
embedded_text = text_embedding(text)
print(embedded_text)
```

1. `import numpy as np`: Numpy kütüphanesini `np` takma adı ile içe aktarır. Numpy, sayısal işlemler için kullanılan bir kütüphanedir.
2. `text = "Bu bir örnek metindir."`: Örnek bir metin dizisi tanımlar.
3. `def text_embedding(text):`: `text_embedding` adında bir fonksiyon tanımlar. Bu fonksiyon metni embeddinge çevirir.
4. `embedding = np.random.rand(1, 128)`: 128 boyutlu bir embedding vektörü oluşturur. Gerçek uygulamalarda bu işlem daha karmaşıktır ve genellikle önceden eğitilmiş modellere dayanır.
5. `return embedding`: Oluşturulan embedding vektörünü döndürür.
6. `embedded_text = text_embedding(text)`: Tanımlanan `text_embedding` fonksiyonunu kullanarak metni embeddinge çevirir.
7. `print(embedded_text)`: Elde edilen embedding vektörünü yazdırır.

---

