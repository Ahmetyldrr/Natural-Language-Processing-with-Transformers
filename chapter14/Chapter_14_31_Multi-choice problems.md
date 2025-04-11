# Çoktan Seçmeli Problem
Çoktan seçmeli bir problem, bir metni tam olarak anlamayı gerektirir. Bu örnekte, önce bir konu listesi sunuyoruz: 
```python
from vertexai.language_models import TextGenerationModel
vertexai.init(project="aiex-57523", location="us-central1")
parameters = {"temperature": 0.2, "max_output_tokens": 256, "top_p": 0.8, "top_k": 40}
model = TextGenerationModel.from_pretrained("text-bison@001")
```
Bu kod, Vertex AI'nın dil modellerini kullanarak metin oluşturma modelini içe aktarır ve `vertexai` kütüphanesini projeye göre başlatır. `parameters` sözlüğü, modelin metin oluşturma davranışını kontrol eden hiperparametreleri tanımlar.

- `temperature`: Oluşturulan metnin yaratıcılığını kontrol eder. Düşük değerler daha tahmin edilebilir metinlere yol açar.
- `max_output_tokens`: Oluşturulacak maksimum token sayısını belirler.
- `top_p`: Çekirdek örnekleme için olasılık eşiğini tanımlar.
- `top_k`: Her adımda dikkate alınacak maksimum token sayısını belirler.

Model, `"text-bison@001"` önceden eğitilmiş modelinden oluşturulur.

```python
response = model.predict("""Multi-choice problem: What is the topic of this text? - entertainment - technology - politics - sports - business - health - fun - culture - science
We then continue the prompt with the text: 
Text: Samba is a name or prefix used for several rhythmic variants, such as samba urbano carioca (urban Carioca samba), samba de roda (sometimes also called rural samba), recognized as part of the Intangible Cultural Heritage of Humanity by UNESCO, amongst many other forms of Samba, mostly originated in the Rio de Janeiro and Bahia States. 
Samba is a broad term for many of the rhythms that compose the better known Brazilian music genres that originated in the Afro-Brazilian communities of Bahia in the late 19th century and early 20th century, having continued its development on the communities of Rio de Janeiro in the early 20th century. 
Having its roots in the Afro-Brazilian Candomblé, as well as other Afro-Brazilian and Indigenous folk traditions, such as the traditional Samba de Caboclo, it is considered one of the most important cultural phenomena in Brazil and one of the country's symbols. 
Present in the Portuguese language at least since the 19th century, the word "samba" was originally used to designate a "popular dance". 
Over time, its meaning has been extended to a "batuque-like circle dance", a dance style, and also to a "music genre". 
This process of establishing itself as a musical genre began in the 1910s and it had its inaugural landmark in the song "Pelo Telefone", launched in 1917. 
Despite being identified by its creators, the public, and the Brazilian music industry as "samba", this pioneering style was much more connected from the rhythmic and instrumental point of view to maxixe than to samba itself. 
Samba was modernly structured as a musical genre only in the late 1920s from the neighborhood of Estácio and soon extended to Oswaldo Cruz and other parts of Rio through its commuter rail. 
Today synonymous with the rhythm of samba, this new samba brought innovations in rhythm, melody and also in thematic aspects. 
Its rhythmic change based on a new percussive instrumental pattern resulted in a more "batucado" and syncopated style – as opposed to the inaugural "samba-maxixe" – notably characterized by a faster tempo, longer notes and a characterized cadence far beyond the simple ones palms used so far. 
Also the "Estácio paradigm" innovated in the formatting of samba as a song, with its musical organization in first and second parts in both melody and lyrics. 
In this way, the sambistas of Estácio created, structured and redefined the urban Carioca samba as a genre in a modern and finished way. 
In this process of establishment as an urban and modern musical expression, the Carioca samba had the decisive role of samba schools, responsible for defining and legitimizing definitively the aesthetic bases of rhythm, and radio broadcasting, which greatly contributed to the diffusion and popularization of the genre and its song singers. 
Thus, samba has achieved major projection throughout Brazil and has become one of the main symbols of Brazilian national identity. 
Once criminalized and rejected for its Afro-Brazilian origins, and definitely working-class music in its mythic origins, the genre has also received support from members of the upper classes and the country's cultural elite.""" , **parameters)
```
Bu kısım, modele bir metin tamamlama görevi verir. Metin, "Samba" hakkında ayrıntılı bilgi içermektedir ve modelden bu metnin konusunu çoktan seçmeli olarak belirlemesi istenir.

```python
#print(f"Response from Model: {response.text}")
wrapped_text = textwrap.fill(response.text, width=40)
print(wrapped_text)
```
Modelin cevabı `response.text` içinde saklanır. `textwrap.fill` fonksiyonu, bu cevabı belirli bir genişliğe göre satır sonlarına ekleyerek daha okunabilir hale getirir.

# Sonuç
Cevap kabul edilebilir: culture

Görüldüğü gibi, PaLM 2 çeşitli görevleri yerine getirebilmektedir. API'si aracılığıyla kod üretebilir mi? Hadi öğrenelim.

---

