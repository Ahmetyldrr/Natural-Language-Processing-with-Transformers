# Parametreler ve Hiperparametreler

"Parametreler" terimi genellikle ağırlıklar ve biaslar gibi eğitilmiş parametreleri ifade eder. "Hiperparametreler" terimi, modeli (katmanlar, boyutlar) veya bir istek işlerken davranışını yapılandırabilen parametreleri ifade eder. Bir istek, bir istem ile başlar ve model veya motor tarafından tamamlanır. "Tamamlama", modelin Generative AI yetenekleri ile bir istemi tamamlama görevini ifade eder. Model, bir yanıt tokenini token token tahmin eder.

# Tamamlama Görevini Değiştirme

Aşağıdaki parametrelerle tamamlama görevinin davranışını değiştirebilirsiniz:
```python
model="gpt-4"  # Kullanılacak OpenAI GPT-3 modelinin seçimi ve muhtemelen gelecekteki diğer modeller.
temperature=0  # Daha yüksek bir değer, örneğin 0.9, modelin daha fazla risk almasını sağlar. Sıcaklık ve top_p'yi aynı anda değiştirmeyin.
max_tokens=256  # Yanıtın maksimum token sayısı.
top_p=1.0  # Top-P veya nucleus sampling, olasılıkların toplamı top_p=1.0 değerine ulaşana kadar üst olasılıkları seçer. Ardından, bu setteki olasılıklardan biri rastgele seçilir.
frequency_penalty=0.0  # 0 ile 1 arasında bir değer, belirli bir yanıttaki tokenlerin sıklığını sınırlar.
presence_penalty=0.0  # 0 ile 1 arasında bir değer, sistemin yeni tokenler kullanmasını ve yeni fikirler üretmesini sağlar.
```
Her platformdaki her model için her pipeline'ın örnekleme sürecini etkileyen ve çıktıları kontrol eden kendi hiperparametreleri vardır. Sıcaklık Top-P hiperparametrelerini içeren örnekleme süreci hakkında daha fazla bilgi için, Bölüm 14'teki Vertex AI PaLM 2 arayüzü bölümüne bakın.

# İstem Rolü

Bu durumda, istemin iki ana bölümü vardır: sistem ve kullanıcı rolleri.

### Sistem Rolü

Rollerin önüne "role": gelir. Sistem rolü şu şekilde tanımlanır:
```json
"role": "system"
```
Ardından, rolün içeriği "content": terimi ile tanımlanır, bu da model için talimatları içerir:
```json
"content": "İfadeler sağlanacak ve sizin göreviniz bunları standart İngilizceye çevirmektir."
```
### Kullanıcı Rolü

Kullanıcı rolü şu şekilde tanımlanır:
```json
"role": "user"
```
Ardından, kullanıcı rolünün içeriği "content": terimi ile tanımlanır, bu da kullanıcı isteğini içerir:
```json
"content": "She no went to the market."
```
Daha birçok seçenek mümkündür. OpenAI belgeleri sürekli olarak gelişiyor ve yeni işlevler sunuyor: https://platform.openai.com/docs/overview. Hayal gücünüz sınırdır! Artık diğer görevler için not defterine devam edebilirsiniz.

Python kodları bulunmamaktadır, ancak JSON formatındaki kod parçacıkları açıklanmıştır.

---

