# Transformer Modellerinin Duygu Analizi

Transformer modellerinin duyguları yoktur. Matris çarpımları ile stokastik matematiksel modeller kullanırlar ve kesinlikle hiçbir hissi yoktur. Yine de, karmaşık metinlerin klinik duygu analizini sağlayabilirler.

## İlk Adım: Modeli Tanımlama

İlk olarak modele ne beklediğimizi söylüyoruz:
```python
from vertexai.language_models import TextGenerationModel
vertexai.init(project="aiex-57523", location="us-central1")
parameters = {
    "temperature": 0.2,
    "max_output_tokens": 256,
    "top_p": 0.8,
    "top_k": 40
}
model = TextGenerationModel.from_pretrained("text-bison@001")
```
*   `vertexai.init`: Vertex AI projesini başlatır.
*   `project`: Proje ID'si.
*   `location`: Proje lokasyonu.
*   `parameters`: Modelin parametrelerini tanımlar.
    *   `temperature`: Modelin yaratıcılığını kontrol eder.
    *   `max_output_tokens`: Modelin üreteceği maksimum token sayısı.
    *   `top_p`: Modelin olasılık dağılımını kontrol eder.
    *   `top_k`: Modelin dikkate alacağı en yüksek olasılıklı token sayısı.
*   `TextGenerationModel.from_pretrained`: Önceden eğitilmiş bir model yükler.

## Duygu Analizi

Modeli kullanarak bir duygu analizi yapıyoruz:
```python
response = model.predict(
    """Is the sentiment positive or negative towards Louis van Gaal based on the article: 
    However, we provide a challenging text that contains negative phrases such as was struggling and hadn't any confidence : 
    Article: Louis van Gaal said he had no option but to substitute Paddy McNair in the first half against Southampton because the defender\'s \'confidence\' was shot - but believes that it will benefit the youngster in the long run. 
    The 19-year-old was hooked by Van Gaal after only 39 minutes at St Mary\'s Stadium on Monday night during Manchester United\'s 2-1 victory over the Saints. 
    McNair was struggling to contain Southampton strikers Shane Long and Graziano Pelle, forcing Van Gaal into replacing him prematurely. 
    Speaking to Sky Sports after the match, Van Gaal explained: \'He (McNair) hadn\'t any confidence. He had already given three big chances away. 
    \'I had to (substitute him), it\'s very disappointing for me and also for Paddy, but I had to because as a manager, I\'m responsible to win. 
    \'And I think, after the change, we played a little better.\' 
    But in spite of the fact United won the game, McNair was exposed time after time in defence and was substituted - even though Chris Smalling had already departed early with an injury. 
    Jonny Evans came on to replace Smalling, before McNair made way for midfielder Ander Herrera as Michael Carrick dropped back in to the centre of defence in Van Gaal\'s 3-5-2 system. 
    And, despite admitting it will be difficult for McNair to accept being replaced so early, Van Gaal insisted that it was a necessity which will serve the Northern Irishman well long term. 
    Van Gaal continued: \'Of course, it\'s tough (for McNair), but it\'s also in his best interests.\' 
    The victory moved United up to third in the Premier League - their highest position since they claimed the title in 2012-13 under Sir Alex Ferguson. """,
    **parameters
)
```
*   `model.predict`: Modeli kullanarak bir tahmin yapar.
*   `**parameters`: Modelin parametrelerini geçirir.

## Sonuç

Modelin sonucunu yazdırıyoruz:
```python
#print(f"Response from Model: {response.text}")
wrapped_text = textwrap.fill(response.text, width=40)
print(wrapped_text)
```
*   `textwrap.fill`: Metni belirli bir genişliğe göre sarar.

Modelin sonucu:
```
Positive
```
Model, Louis van Gaal'a karşı duyulan duygunun pozitif olduğunu belirledi.

## Açıklama

Modelin nasıl bu sonuca vardığını anlamak için, aynı metni kullanarak bir açıklama istiyoruz:
```python
response = model.predict(
    """Is the sentiment positive or negative towards Louis van Gaal based on the article and explain why in detail: 
    Article: Louis van...""",
    **parameters
)
```
Modelin açıklaması:
```
The sentiment towards Louis van Gaal is positive. 
The article is about Louis van Gaal's decision to substitute Paddy McNair in the first half of the match against Southampton. 
The article states that Van Gaal had to make the substitution because McNair was struggling and had given away three big chances. 
However, the article also says that Van Gaal believes that the substitution was the right thing to do and that it will benefit McNair in the long run. 
Overall, the article paints Van Gaal in a positive light. 
It shows him as a manager who is willing to make tough decisions in order to win games, and who is also looking out for the best interests of his players.
```
Model, Louis van Gaal'a karşı duyulan duygunun pozitif olduğunu çünkü makalenin Van Gaal'ı zor kararlar alan ve oyuncularının çıkarlarını düşünen bir yönetici olarak gösterdiğini açıkladı.

---

