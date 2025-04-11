# OpenAI'de İnce Ayar Yapılabilir Modeller

OpenAI'de GPT-3.5-turbo ve GPT-4 dahil olmak üzere çeşitli modelleri ince ayar yapabilirsiniz. Ayrıca, Babbage-002 gibi GPT-3 mimarisine sahip bir modeli de ince ayar yapabilirsiniz: https://platform.openai.com/docs/guides/fine-tuning/what-models-can-be-fine-tuned . Örneğin, Babbage-002'yi ince ayar yapmak, GPT-4'ü ince ayar yapmaktan daha az maliyetlidir. Maliyet etkin bir modelle başlayın ve bunu temel modeliniz olarak kullanın. Ardından, daha iyi sonuçlar elde etmeniz gerekiyorsa, gerekirse daha pahalı olanları deneyin. Bir modeli ince ayar yapmadan önce veri hazırlama kısıtlamalarını ve veri kümesi formatlarını kontrol edin. Bu bölümde bir Babbage-002 modelini ince ayar yapacağız.

## İnce Ayar İşlemi

İnce ayar işlemi, OpenAI tarafından oluşturulan ve dosya kimliğini kullanarak oluşturduğumuz dosya ile çalışmaya hazırdır:
```python
from openai import OpenAI
client = OpenAI()
job_response = client.fine_tuning.jobs.create(
  training_file=file_id,
  model="babbage-002"
)
```
OpenAI birçok istek alır. Yaptığımız ince ayar isteği bir kuyruğa alınır. İşlem tamamlandığında genellikle bir e-posta alırsınız. İş kimliğini çıkarabilir ve görüntüleyebilirsiniz:
```python
job_id = job_response.id
print(job_id)
```
Çıktı, işi görüntüler: `ftjob-MUR57DYN3TxKeWvXO3M8IhCu`

OpenAI verilerinizi ve modellerinizi korur, böylece bu işe yalnızca siz erişebilirsiniz. İnce ayar işinizin durumunu kontrol etmek için önce işinizin ayrıntılarını almanız gerekir:
```python
# İnce ayar işinin durumunu kontrol edin
job_details = client.fine_tuning.jobs.retrieve(job_id)
print(job_details)
```
Ardından, işinizin durumunu görüntüleyebilirsiniz:
```python
# İki durum arasında bir zaman farkı olabilir:
# 1. İnce ayar işini çalıştırdığınız anda ve tamamlanma arasında
# 2. Tamamlanma ve sunucu güncellemesi arasında
# OpenAI bildirimlerini etkinleştirdiyseniz e-postanızı kontrol edin
status = job_details.status
print(f"İş durumu: {status}")
```
İş durumu: `validating_files`

Bu durumda, durum özelliği veri kümenizin doğrulandığını gösterir. İş durumu daha sonra `running` ve ardından `succeeded` olur. Gösterilen terimler değişebilir, ancak işlem aynı kalır: dosya doğrulama, ince ayar çalıştırma ve ince ayar başarılı (veya başarısız).

İnce ayar işlerinin listesini de kontrol edebilir ve işin durumunu görüntüleyebilirsiniz:
```python
# 10 ince ayar işini listeleyin
job_list = client.fine_tuning.jobs.list(limit=10)
```
Ardından, işleri ve durumlarını görüntüleyebilirsiniz:
```python
import json
from pprint import pprint

# SyncCursorPage nesnesinden ham JSON dizesini alın
json_string = job_list.json()

# JSON dizesini Python nesnesine dönüştürün
data = json.loads(json_string)

# Veri dizisini çıkarın
jobs = data.get('data', [])

# Verileri sözlük listesi olarak biçimlendirin
formatted_data = [
    {
        'id': job.get('id'),
        'created_at': job.get('created_at'),
        'status': job.get('status'),
        'training_file': job.get('training_file'),
        'model': job.get('model'),
        'model_name': job.get('fine_tuned_model')
    }
    for job in jobs
]

# Biçimlendirilmiş verileri yazdırın
pprint(formatted_data)
```
Mevcut iş için çıktı özeti, işlemin çalıştığını gösterir:
```python
[
    {
        'created_at': 1705083620,
        'id': 'ftjob-MUR57DYN3TxKeWvXO3M8IhCu',
        'model': 'babbage-002',
        'model_name': None,
        'status': 'running',
        ...
    }
]
```
Model ince ayarlandıktan sonra `model_name` görüntülenecektir. Hücreyi yeniden çalıştırdığınızda, mevcut iş için çıktı özeti, ince ayar işinin başarılı olduğunu ve model adının görüntülendiğini gösterir:
```python
[
    {
        'created_at': 1705083620,
        'id': 'ftjob-MUR57DYN3TxKeWvXO3M8IhCu',
        'model': 'babbage-002',
        'model_name': 'ft:babbage-002:personal::xxxxxx',
        'status': 'succeeded',
        ...
    }
]
```
Modeliniz ince ayarlandı ve artık modeli çalıştırma hazırsınız.

---

