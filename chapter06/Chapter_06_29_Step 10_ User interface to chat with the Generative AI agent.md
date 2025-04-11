# ipywidgets Kurulumu ve Modelin Hazırlanması
ipywidgets'i arayüzü oluşturmak için kurduktan ve model ile tokenizer'ın başlatıldığından emin olduktan sonra, içerik oluşturmak için bir fonksiyon tanımlayarak prototipi değerlendirebiliriz:

```python
!pip install ipywidgets
import ipywidgets as widgets
from IPython.display import display, clear_output
from transformers import RobertaTokenizer, RobertaForCausalLM
```

# Yanıt Oluşturma Fonksiyonunun Tanımlanması
Yanıt oluşturma fonksiyonunu tanımlayalım:
```python
def generate_response(prompt):
    # Her istek için model ve tokenizer'ı yeniden yükle
    tokenizer = RobertaTokenizer.from_pretrained('roberta-base')
    model = RobertaForCausalLM.from_pretrained(model_path)
    inputs = tokenizer(prompt, return_tensors="pt", max_length=50, truncation=True)
    output = model.generate(**inputs, max_length=100, temperature=0.9, num_return_sequences=1)
    generated_text = tokenizer.decode(output[0], skip_special_tokens=True)
    return generated_text
```
Bu fonksiyon:
1. `RobertaTokenizer` ve `RobertaForCausalLM` modellerini `roberta-base` ve `model_path` üzerinden yükler.
2. Giriş metnini (`prompt`) `tokenizer` ile işler ve tensor olarak döndürür. `max_length=50` ve `truncation=True` parametreleri ile giriş metnini 50 token'a kadar kırpar.
3. İşlenmiş girişi (`inputs`) `model.generate` metoduna geçirerek çıktı üretir. `max_length=100` parametresi ile maksimum çıktı uzunluğunu 100 token olarak belirler. `temperature=0.9` parametresi ile çıktıların çeşitliliğini ayarlar. `num_return_sequences=1` parametresi ile yalnızca bir çıktı dizisi döndürür.
4. Üretilen çıktıyı (`output`) `tokenizer.decode` ile metne çevirir ve özel tokenları atlar (`skip_special_tokens=True`).

# Arayüz Oluşturma
Arayüzü oluşturmak için widget'ları tanımlayalım:
```python
text_input = widgets.Textarea(
    description='Prompt:',
    placeholder='Enter your prompt here...'
)

button = widgets.Button(
    description='Generate',
    button_style='success'
)

output_text = widgets.Output(layout={'border': '1px solid black', 'height': '100px'})
```
Bu widget'lar:
1. `text_input`: Kullanıcının giriş yapması için bir metin alanı.
2. `button`: "Generate" butonu.
3. `output_text`: Çıktının gösterileceği alan.

# Buton Tıklama Olayı İşleyicisi
Buton tıklama olayını işleyelim:
```python
def on_button_clicked(b):
    with output_text:
        clear_output()
        response = generate_response(text_input.value)
        print(response)

button.on_click(on_button_clicked)
```
Bu fonksiyon:
1. `output_text` alanını temizler (`clear_output()`).
2. `text_input` değerini `generate_response` fonksiyonuna geçirerek yanıtı üretir.
3. Üretilen yanıtı `output_text` alanında yazdırır (`print(response)`).

# Arayüzü Gösterme
Arayüzü gösterelim:
```python
display(text_input, button, output_text)
```
Artık bir giriş metni girebilir ve "Generate" butonuna tıklayarak Generative AI çıktısını görüntüleyebiliriz.

# Deneme ve Sonuçlar
Şekil 6.5'te gösterildiği gibi bir giriş metni girebiliriz:
Şekil 6.5: Kullanıcı Arayüzü

"Generate" butonuna tıkladığımızda Generative AI çıktısı görüntülenir:
Şekil 6.6: Giriş metni ve üretilen yanıt

Bu durumda, çıktı deneysel ve ilginçtir. Son kısım bilinen kelimelerin bir sözlüğü ile filtrelenebilir. Ancak, Generative AI stokastiktir ve hatalar üretebilir. İlk olarak, eğitilen örneklemelere yakın girişler denemek gerekir, örneğin noktalama işaretleri olmadan: "I would like to assist you", "I need help to find the battery of", "I would like to know why they moved us". Daha ileri gitmek için daha fazla eğitim gerekebilir.

---

