# BertViz ile Transformatör Model Görünümü Elde Etme

Bir transformatörün model görünümünü BertViz ile elde etmek sadece bir satır kod gerektirir: `model_view(attention, tokens, sentence_b_start)`. BertViz, Şekil 9.5'teki görünüm alıntısında gösterildiği gibi, tüm katmanları ve dikkat başlıklarını tek bir görünümde gösterir:

# BertViz Model Görünümü

BertViz'in model görünüm modu, tüm katmanları ve dikkat başlıklarını içerir. Bir dikkat başlığına tıkladığınızda, kelime-kelime ve cümle-cümle seçenekleri içeren bir dikkat başlığı görünümü elde edersiniz. Daha sonra, transformatör modelinin katmanlar boyunca ilerledikçe daha iyi temsiller nasıl oluşturduğunu görmek için dikkat başlıklarını inceleyebilirsiniz. Örneğin, Şekil 9.6, ilk katmanlardaki bir dikkat başlığının aktivitesini gösterir:

# Alt Katmanlardaki Bir Dikkat Başlığının Aktivitesi

Bu interaktif arayüz, dikkat başlıklarının aktivitesi hakkında içgörüler sunar. Şimdi, bu dikkat başlıklarının analizine daha derinlemesine dalacağız.

Python kodu bulunmamaktadır, sadece bir ingilizce paragraf çevirisi yapılmıştır. 

Eğer python kodu olsaydı, örneğin:
```python
model_view(attention, tokens, sentence_b_start)
```
gibi bir kod için açıklama şu şekilde olurdu:

*   `model_view`: BertViz kütüphanesinden bir fonksiyondur ve transformatör modelinin görünümünü elde etmek için kullanılır.
*   `attention`: Dikkat mekanizması ile ilgili değerleri içerir.
*   `tokens`: İşlenmiş kelimeleri veya tokenleri temsil eder.
*   `sentence_b_start`: İkinci cümlenin başlangıç indeksini belirtir.

Bu fonksiyon, belirtilen parametrelerle model görünümünü oluşturur ve görselleştirir.

---

