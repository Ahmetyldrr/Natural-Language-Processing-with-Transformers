# Büyük Dil Modeli Gömmelerini Kullanma

Büyük bir dil dönüştürücü modelini ince ayar yapma alternatifi olarak gömmeleri göz ardı etmeyin. İnce ayar yapmak güvenilir bir veri seti, doğru model konfigürasyonu ve donanım kaynakları gerektirir. Yüksek kaliteli veri setleri oluşturmak zaman ve kaynak gerektirir. OpenAI'ın Ada'sı gibi bir Büyük Dil Modeli'nin (LLM) gömme yeteneklerinden yararlanmak, modelinizi azaltılmış maliyet ve çaba ile özelleştirmenizi sağlar. Modeliniz gerçek zamanlı olarak güncellenmiş verilere erişebilecektir. Gömülü metinler aracılığıyla Retrieval Augmented Generation (RAG) uygulayacaksınız. 7. Bölüm'de, ChatGPT ile Üretken Yapay Zeka Devrimi'nde RAG için web sayfaları ve özelleştirilmiş metin kullandık. Bu kez, daha da ileri giderek gömmeleri kullanacağız. Bu bölüm, gömmelerle arama yapmanın neden bazen ince ayara çok etkili bir alternatif olabileceğini açıklayarak başlar. Bu yaklaşımın avantajlarını ve sınırlarını inceleyeceğiz. Ardından, metin gömmelerinin temellerini inceleyeceğiz. Gensim ve Word2Vec ile bir dosyayı okuyan, tokenleştiren ve gömen bir program oluşturacağız. Program, model açıklamasını analiz etmeyi ve bir kelimenin vektörüne erişmeyi gösterecektir. Genism'in vektör uzayını keşfedeceğiz ve kelimeler arasındaki kosinüs benzerliğini görüntüleyeceğiz. Son olarak, vektör uzayını Google'ın TensorFlow Projector'ında görüntüleyeceğiz. Bu temel bilgilerle, veri setinin kesim tarihinden sonra meydana gelen spor etkinlikleri hakkında bir soru-cevap programı uygulayacağız. Örneğin, bir model önceden eğitilmiş ve bir yıl önce ince ayar yapılmışsa, bir yıl sonraki olaylar hakkında soruları nasıl cevaplayacaktır? Bu soruna gömme tabanlı arama işlevselliği ile adres ediyoruz. Son olarak, Amazon Fine Food Reviews'i gömmek için OpenAI Ada'yı uygulayacağız. Verileri hazırlayacağız ve Ada gömme işlemini çalıştıracağız. Program, k-means kümeleme ile kümeleri bulacaktır. Kümeleri t-SNE ile görüntüleyeceğiz. Sistem, her bir inceleme kümesinin temasını bulmak ve açıklamak için OpenAI davinci'ye soru sormaya hazır olacaktır. Bölümün sonunda, bir sistemi istem tasarımından ileri istem mühendisliğine kadar gömmeleri kullanarak RAG için nasıl alacağınızı öğreneceksiniz.

## Bu Bölümde İşlenecek Konular:
- Punkt ile metin tokenleştirme
- Gensim ve Word2Vec ile metin gömme
- Bir kelimenin vektörüne erişme
- Gömülü vektör uzayını keşfetme
- Kosinüs benzerliği
- Vektör uzayını TensorFlow Projector ile görüntüleme
- Soru-cevap
- Arama verilerini hazırlama
- Gömme ile arama yapma
- Transfer öğrenme
- Ada gömmelerini çalıştırma ve RAG kullanma
- Öğrenilen gömmelerle veri kümeleme

Bu alandaki tüm yeniliklere ve kütüphane güncellemelerine rağmen, paketler ve modeller düzenli olarak değişmektedir. Lütfen en son kurulum ve kod örnekleri için GitHub deposuna gidin: https://github.com/Denis2054/Transformers-for-NLP-and-Computer-Vision-3rd-Edition/tree/main/Chapter11 . Ayrıca, bu veya herhangi bir bölümdeki kodu çalıştırırken herhangi bir sorunuz varsa Discord topluluğumuza bir mesaj gönderin ( https://www.packt.link/Transformers ). LLM gömmelerinin neden ince ayara bir alternatif olabileceğini inceleyelim.

Python kodları bulunmamaktadır, ancak ilerleyen kısımlarda Gensim ve Word2Vec ile ilgili kod örnekleri verilecektir. 

Örneğin, aşağıdaki gibi bir kod bloğu olabilir:
```python
# Gensim ve Word2Vec ile metin gömme
from gensim.models import Word2Vec

# Veri setini oku
with open('data.txt', 'r') as f:
    data = f.read()

# Tokenleştirme
tokenized_data = [sentence.split() for sentence in data.split('.')]

# Word2Vec modelini oluştur
model = Word2Vec(tokenized_data, vector_size=100, window=5, min_count=1)

# Bir kelimenin vektörüne erişme
vector = model.wv['kelime']

print(vector)
```
Bu kod bloğunda:
1. `gensim.models`ten `Word2Vec` modülü içe aktarılır.
2. `data.txt` dosyası okunur.
3. Veri tokenleştirilir.
4. `Word2Vec` modeli oluşturulur.
5. `model.wv` kullanarak bir kelimenin vektörüne erişilir.

Bu şekilde, her bir kod satırının açıklaması verilebilir.

---

