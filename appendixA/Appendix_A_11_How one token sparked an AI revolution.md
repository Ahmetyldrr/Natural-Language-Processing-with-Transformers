# Bir Tokenin Gücü: Yapay Zeka Devrimi

Bir token, bir Yapay Zeka (YZ) devrimi üretti ve her alanda ve uygulamada YZ'nin kapısını açtı. ChatGPT ile GPT-4, PaLM 2 ve diğer Büyük Dil Modelleri (LLM), metin üretmenin benzersiz bir yoluna sahiptir. LLM'lerde, bir token minimal bir kelime parçasıdır. Token, bir LLM'nin başladığı ve bittiği yerdir. Örneğin, "including" kelimesi "includ" + "ing" haline gelebilir, bu da iki tokeni temsil eder. GPT modelleri, eğitim veri setindeki yüz milyarlarca tokene dayanarak tokenleri tahmin eder.

# Şekil A.7: Python ile NetworkX Kullanarak Oluşturulan GPT Çıkarım Grafiği

Şekil A.7'de OpenAI GPT modelinin bir token üretmek için yaptığı çıkarımı gösteren bir grafik verilmiştir. Bu şekilde, model tarafından kontrol edilen tek kısımların "Model" ve "Çıktı Üretimi" olduğu görülmektedir. Geri kalan her şey işlem hattındadır. İşlem hattını anlamak için, önce bu adımların bir açıklamasını yapacağız:

## Tokenleştirme
İşlem hattı, girdi dizisini (örneğin, "Güneş güneş sisteminde mi?"), bir tokenleştirici kullanarak tokenlere dönüştürür. Tokenleştiricilerin transformer modellerindeki kritik rolü, Bölüm 10'da incelenmiştir.

## Model Girdisi
İşlem hattı, tokenleştirilmiş diziyi eğitilmiş GPT modeline geçirir.

## Model
Model, girdiyi çeşitli katmanlardan geçirerek işler, girdi katmanından başlayarak birden fazla transformer katmanından geçerek çıktı katmanına ulaşır. Bölüm 2, Transformer Modelinin Mimarisini detaylı olarak açıklamaktadır.

## Çıktı Üretimi
Model, girdi dizisine göre ham çıktı lojitsleri üretir.

## Örnekleyici
Örnekleyici, lojitsleri olasılıklara dönüştürür. Bölüm 7, modelin çıktısını etkileyen hiperparametreleri uygulamıştır. Örnekleme sürecine ilişkin daha fazla bilgi için, Bölüm 14'teki Vertex AI PaLM 2 Arayüzü bölümüne bakınız.

## Sonraki Token Seçimi (Sonraki TS)
Sonraki token, örnekleyicinin olasılıklarına göre seçilir.

## Sonraki Token Ekleme
Seçilen sonraki token, girdi dizisine (token biçiminde) eklenir ve maksimum token sınırına ulaşılana kadar işlem 3. adımdan itibaren tekrarlanır.

## Token Üretimi Tamamlanması (Metin Üretimi)
Metin üretimi, maksimum token sınırına ulaşıldığında veya bir dizi sonu tokeni tespit edildiğinde sona erer.

## Metin Yeniden Yapılandırma
Tokenleştirici, son token dizisini tekrar bir metin dizisine dönüştürür. Bu adım, alt kelime tokenlerini tekrar birleştirerek tam kelimeler oluşturmayı içerir.

Bu işlem, girdi dizisini alır ve bir token üretir. Bu token, diziye eklenir ve model, başka bir token üretmek için yeniden başlar. Bu sürecin adımlarını özetleyebiliriz:
- Girdi = tokenlerde ifade edilen bir girdi dizisi.
- Model, girdiyi işler.
- Çıktı = sonraki token, maksimum token sayısına ulaşılana kadar girdinin sonuna eklenir.

Bu işlem, Şekil A.8'de gösterildiği gibi, bir token çıktı devrimidir.

## Bir İleri Doğru Geçiş için Gösterim
t = bir token
f = sonraki tokeni tahmin eden model ve çıktı kontrolörü
n = ilk token dizisi + her yeni token eklenene kadar maksimum token sayısına ulaşılana veya bir dizi sonu tokeni tespit edilene kadar

Bu süreci f(n) olarak özetledik. f(n)'in altında, tahmin edilen tokenlerin birer birer eklenmesi süreci yatmaktadır. f(n)'i şu şekilde düşünebilirsiniz: 
t_i = f(t_1, t_2, ..., t_{i-1})

Bunu düşünün. Bir token! Yine de bu token, her alanda toplumu değiştirdi: çeviriler, özetleme, soru-cevap, görüntü, video ve liste her gün büyüyor. Bu kitabın sonuna gelirken, YZ'deki her yeni gelişmenin dünyamızı nasıl daha da şekillendireceğini hayal edin!

## Discord Topluluğumuza Katılın
Yazarlar ve diğer okuyucularla tartışmak için topluluğumuzun Discord alanına katılın: https://www.packt.link/Transformers

Python kodları ile ilgili açıklama istenen kısım bulunmamaktadır. Ancak, metinde NetworkX kütüphanesinin kullanıldığı bir Python kodundan bahsedilmektedir. NetworkX, Python'da çizge (graph) oluşturmak ve analiz etmek için kullanılan bir kütüphanedir. Şekil A.7'nin oluşturulmasında kullanıldığı belirtilen bu kütüphane ile ilgili basit bir örnek aşağıda verilmiştir:

```python
import networkx as nx
import matplotlib.pyplot as plt

# Boş bir çizge oluştur
G = nx.Graph()

# Düğümler ekle
G.add_node("Model")
G.add_node("Çıktı Üretimi")
G.add_node("Tokenleştirme")
G.add_node("Model Girdisi")

# Kenarlar ekle
G.add_edge("Tokenleştirme", "Model Girdisi")
G.add_edge("Model Girdisi", "Model")
G.add_edge("Model", "Çıktı Üretimi")

# Çizgeyi çiz
nx.draw(G, with_labels=True)
plt.show()
```

Bu kod, basit bir çizge oluşturur ve "Model", "Çıktı Üretimi", "Tokenleştirme" ve "Model Girdisi" adlı düğümleri ekler. Daha sonra bu düğümler arasında kenarlar ekler ve çizgeyi çizer. Şekil A.7'nin nasıl oluşturulduğu ile ilgili detaylar verilmemiştir, ancak benzer bir şekilde NetworkX kullanılarak oluşturulduğu anlaşılmaktadır.

---

