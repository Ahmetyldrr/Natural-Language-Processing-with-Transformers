# İnce Ayar Yapılmış Modelleri Yönetme

Bu kitabın yazıldığı sırada, ince ayar yapılmış modelleri kuruluşunuzun dışıyla paylaşamazsınız. Bunları projeleriniz için dağıtabilirsiniz. Ayrıca modeller hakkında bilgi edinebilir, işleri iptal edebilir ve ince ayar yapılmış modelleri silebilirsiniz. Bunu yapmak için bakım işlevlerini dikkatlice etkinleştirin: 
```python
from openai import OpenAI
client = OpenAI() 
# Birkaç iş veya model işlevinden (bilgi, iptal, silme) birini etkinleştirmek istiyorsanız bakımı True olarak ayarlayın
maintenance = False
```
## Bakım İşlevlerini Etkinleştirme

Eğer `maintenance` `True` ise, ince ayar işlerini listeleyebilir, bir işin durumunu alabilir, bir işi iptal edebilir, ince ayar süreciyle ilgili iş olaylarını listeleyebilir ve model silme işlemini gerçekleştirebilirsiniz:
```python
if maintenance is True:
    # 10 ince ayar işini listele
    client.fine_tuning.jobs.list(limit=10)
    
    # Bir ince ayarın durumunu al
    client.fine_tuning.jobs.retrieve("ftjob-your job")
    
    # Bir işi iptal et
    client.fine_tuning.jobs.cancel("ftjob-your job")
    
    # Bir ince ayar işinden 10'a kadar olayları listele
    client.fine_tuning.jobs.list_events(fine_tuning_job_id="ftjob-your job", limit=10)
    
    # İnce ayar yapılmış bir modeli sil (modelin oluşturulduğu kuruluşun sahibi olmalısınız)
    # client.models.delete("your model")
```
Keşfedebileceğiniz birçok başka OpenAI hizmeti vardır: https://platform.openai.com/docs/guides/fine-tuning/. Daha ileriye gitmek için, her aşamayı ayrı not defterlerinde de izole edebilirsiniz:

* JSON verileri, bir bilgi veri kümesi oluşturmak için ayrı bir not defterinde veya hatta ayrı bir projede hazırlanabilir.
* Sınıflandırma, veri keşfi ve projeniz için ihtiyaç duyduğunuz her görev gibi diğer birçok NLP görevi için istemler ve tamamlamalar oluşturabilirsiniz.
* Dosyayı OpenAI'nin ince ayar araçları için gerektiğinde kaydedebilir ve yükleyebilirsiniz.
* Verileri JSONL'ye dönüştürmek, OpenAI'nin ince ayarı veya herhangi bir proje için bir bilgi veri kümesi olarak veri kümenizi görselleştirmek için mükemmel bir yol olabilir.
* Dosyayı kaydedebilir ve OpenAI modelini gerektiğinde ince ayar yapabilirsiniz.
* OpenAI modelini ince ayarlamak ayrı bir program olabilir. Hazırlanan veri kümesini istediğinizde yükleyebilirsiniz.
* İnce ayar yapılmış GPT modelini çalıştırmak ayrı bir not defterinde veya uygulamasında yapılabilir.
* Bu bölümdeki yönetim işlevlerini başka bir not defterinde veya uygulamasında da çalıştırabilirsiniz.
* İnce ayar sürecinin esnekliği, her aşamanın dikkatli bir şekilde hazırlanmasını ve kaynakları gerektirmesini hafifletecektir.

---

