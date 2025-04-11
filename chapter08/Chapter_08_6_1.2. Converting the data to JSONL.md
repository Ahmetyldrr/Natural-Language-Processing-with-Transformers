# JSON Dosyasının Hazırlanması ve OpenAI Modelinin İncelenmesi

Eğer JSON dosyasının hazırlanması sorunsuz bir şekilde gerçekleştiyse, OpenAI'ın veri hazırlama aracı yeni oluşturduğumuz `kant_prompts_and_completions.json` dosyasıyla sorunsuz çalışmalıdır. Şimdi `fine_tunes` aracını çalıştıracağız: 
```bash
!openai tools fine_tunes.prepare_data -f "kant_prompts_and_completions.json"
```
Çıktı, veri setinde hata olmadığını gösteriyor:
```
Analyzing...
- Your JSON file appears to be in a JSONL format. Your file will be converted to JSONL format
- Your file contains 6127 prompt-completion pairs
- All prompts end with suffix ` ->`
- All completions end with suffix `\n`
```
Analiz sonuçlarına göre aşağıdaki işlemler gerçekleştirilecek:
```
- [Necessary] Your format `JSON` will be converted to `JSONL`
```
Eğer veri setiniz hatalar içeriyorsa, hazırlama aracı verileri düzeltmeye çalışacaktır. Bu süreçte bazı verileri kaybedebilirsiniz. Bu durumda her şey yolunda. JSON dosyasını JSONL formatına dönüştürmeniz istenecek: 
```
Your data will be written to a new JSONL file. Proceed [Y/n]: Y
Wrote modified file to `kant_prompts_and_completions_prepared.jsonl`
```
Dosyayı inceleyebilirsiniz! Birkaç satır sonra OpenAI, bir promptu nasıl çalıştıracağınıza dair bilgi sağlıyor:
```
After you've fine-tuned a model, remember that your prompt has to end with the indicator string ` ->` for the model to start generating completions, rather than continuing with the prompt. Make sure to include `stop=["\n"]` so that the generated texts ends at the expected place.
```
Modelinizin eğitimi başladığında, `curie` modelinin eğitimi yaklaşık 1.44 saat sürecek, `ada` ve `babbage` için daha az sürecek. Sıra yaklaşık olarak sizden önce gelen her iş için yarım saat sürecek. OpenAI, dönüştürülen dosyayı `kantgpt_prepared.jsonl` olarak kaydeder.

## JSONL Dosyasının İncelenmesi

Şimdi önerildiği gibi JSONL dosyasını inceleyeceğiz:
```python
import json

# Dosyayı aç ve satırları oku
with open('kant_prompts_and_completions_prepared.jsonl', 'r') as f:
    lines = f.readlines()

# İlk birkaç satırı ayrıştır ve yazdır
for line in lines[:5]:
    data = json.loads(line)
    print(json.dumps(data, indent=4))
```
Çıktının bir bölümü her şeyin yolunda gittiğini gösteriyor:
```
{
    "prompt": "The Project Gutenberg Etext of The Critique of Pure Reason, by Immanuel Kant Copyright laws are changing all over the world. ->",
    "completion": " Be sure to check the copyright laws for your country before distributing this or any other Project Gutenberg file.\n"
}
```
## OpenAI'a Dosyanın Yüklenmesi

Son hazırlık adımımız OpenAI'de dosya oluşturmaktan ibaret:
```python
from openai import OpenAI

client = OpenAI()
file_response = client.files.create(
  file=open("/content/kant_prompts_and_completions_prepared.jsonl", "rb"),
  purpose='fine-tune'
)

# Bakım için yazdırma seçeneği
# print(file_response)
```
Şimdi dosya ID'sini değişken olarak kullanmak için kişisel dosya ID'mizi çıkaracağız:
```python
# Eğitim dosya ID'sini çıkar
file_id = file_response.id
print(file_id)
```
Çıktı, dosya ID'sini doğru bir şekilde çıkardığımızı gösteriyor:
```
file-vMtRO7to3c26hVc4TRrzBmst
```
OpenAI modelini fine-tune etmeye hazırız.

---

