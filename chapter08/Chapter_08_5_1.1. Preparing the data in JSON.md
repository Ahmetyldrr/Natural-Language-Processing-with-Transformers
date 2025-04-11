# OpenAI Veri Hazırlama: Gutenberg'den JSON'a

OpenAI, istemler ve tamamlamalar içeren biçimlendirilmiş bir dosya gerektirir. JSON önerilen dosya biçimlerinden biridir. İlk olarak gerekli kütüphaneleri içe aktarmamız gerekiyor. Aşağıdakilere ihtiyacımız olacak:

*   Natural Language Toolkit ile birlikte gelen `punkt`, 10. Bölüm'de daha ayrıntılı olarak ele aldığımız önceden eğitilmiş bir tokenleştirici.
*   `sent_tokenize`, `punkt` ile birlikte çalışacak
*   HTTP isteği için `requests`
*   Web sayfasını kazımak için `BeautifulSoup`
*   JSON dosyası oluşturmak için `json`
*   Metni düzenli ifadelerle ayrıştırmak için `re`

Bu araçlarla, Gutenberg'den JSON'a istediğimiz kitabı dönüştürebiliriz:

```python
# Gutenberg'den JSON'a
import nltk
nltk.download('punkt')
from nltk.tokenize import sent_tokenize
import requests
from bs4 import BeautifulSoup
import json
import re
```

İlk olarak kitabı Project Gutenberg'den aşağıdaki kodu uncomment ederek alıyoruz:

```python
# İlk olarak kitabı Project Gutenberg'den al
# url = 'http://www.gutenberg.org/cache/epub/4280/pg4280.html'
# response = requests.get(url)
soup = BeautifulSoup(response.content, 'html.parser')
```

Ya da kitabı GitHub deposundan indirip, okuyup, BeautifulSoup ile ayrıştırabiliriz:

```python
# Seçenek 2: GitHub deposundan
# Üretim aşamasına geçerken silinecek geliştirme erişimi
!curl -L https://raw.githubusercontent.com/Denis2054/Transformers_3rd_Edition/master/Chapter08/gutenberg.org_cache_epub_4280_pg4280.html --output "gutenberg.org_cache_epub_4280_pg4280.html"

# İndirilen HTML dosyasını aç ve oku
with open("gutenberg.org_cache_epub_4280_pg4280.html", 'r', encoding='utf-8') as file:
    file_contents = file.read()
soup = BeautifulSoup(file_contents, 'html.parser')
```

Daha sonra metni temizleyip cümlelere ayırıyoruz:

```python
# Kitabın metnini al ve biraz temizle
text = soup.get_text()
text = re.sub('\s+', ' ', text).strip()

# Metni cümlelere ayır
sentences = sent_tokenize(text)
```

Şimdi zor bir kısma geldik. OpenAI, eğitmek istediğimiz her satır için bir istem ve bir tamamlanma bekliyor. Ancak ayırıcılar dikkatlice seçilmelidir:

```python
# Ayırıcıları ve bitiş işaretlerini tanımla
prompt_separator = " ->"
completion_ending = "\n"
```

Bu iyi tanımlanmış ayırıcılarla, istemleri ve tamamlamaları oluşturabiliriz:

```python
# Şimdi istemleri ve tamamlamaları oluştur
data = []
for i in range(len(sentences) - 1):
    data.append({"prompt": sentences[i] + prompt_separator, "completion": " " + sentences[i + 1] + completion_ending})
```

Son olarak, istemleri ve tamamlamaları bir JSON dosyasına kaydediyoruz:

```python
# İstemleri ve tamamlamaları bir dosyaya yaz
with open('kant_prompts_and_completions.json', 'w') as f:
    for line in data:
        f.write(json.dumps(line) + '\n')
```

Bu işlem, veri kümesinin OpenAI'ın hazırlık modülü tarafından kısmen veya tamamen reddedilmesini önlemek için dikkatlice hazırlanmalıdır. Şimdi veri kümesini veri hazırlama modülüne göndermeden önce kontrol ediyoruz:

```python
import pandas as pd

# Veriyi yükle
df = pd.read_json('kant_prompts_and_completions.json', lines=True)
df
```

Çıktı, iyi bir iş çıkardığımızı gösteriyor. Her satır için bir istem ve bir tamamlanma var:

# Veri Kümesinin Kontrolü

Artık OpenAI'ın veri hazırlama modülünü çalıştırabiliriz.

---

