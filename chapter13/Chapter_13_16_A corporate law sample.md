# Montana Corporate Law Çevirisi

Şirket hukuku birçok yasal inceliği içerir, bu da özetleme görevlerini oldukça zorlaştırır. Bu örneğin girdisi, Montana eyaletindeki şirket yasasının bir alıntısıdır, ABD: 

## Metin
```python
text = """The law regarding corporations prescribes that a corporation can be incorporated in the state of Montana to serve any lawful purpose. In the state of Montana, a corporation has all the powers of a natural person for carrying out its business activities. The corporation can sue and be sued in its corporate name. It has perpetual succession. The corporation can buy, sell or otherwise acquire an interest in a real or personal property. It can conduct business, carry on operations, and have offices and exercise the powers in a state, territory or district in possession of the US, or in a foreign country. It can appoint officers and agents of the corporation for various duties and fix their compensation. The name of a corporation must contain the word "corporation" or its abbreviation "corp."  The name of a corporation should not be deceptively similar to the name of another corporation incorporated in the same state. It should not be deceptively identical to the fictitious name adopted by a foreign corporation having business transactions in the state. The corporation is formed by one or more natural persons by executing and filing articles of incorporation to the secretary of state of filing. The qualifications for directors are fixed either by articles of incorporation or bylaws. The names and addresses of the initial directors and purpose of incorporation should be set forth in the articles of incorporation. The articles of incorporation should contain the corporate name, the number of shares authorized to issue, a brief statement of the character of business carried out by the corporation, the names and addresses of the directors until successors are elected, and name and addresses of incorporators. The shareholders have the power to change the size of board of directors."""
```

## Çeviri
Şirketlerle ilgili yasa, bir şirketin Montana eyaletinde herhangi bir yasal amaç için kurulabileceğini öngörür. Montana eyaletinde, bir şirket, ticari faaliyetlerini yürütmek için bir doğal kişinin tüm yetkilerine sahiptir. Şirket, tüzel ismiyle dava açabilir ve dava açılabilir. Sürekli halefiyeti vardır. Şirket, bir gayrimenkul veya menkul mülkiyette bir menfaat satın alabilir, satabilir veya başka bir şekilde edinebilir. İş yapabilir, operasyonlar yürütebilir ve ABD'nin sahip olduğu bir eyalet, bölge veya ilde veya yabancı bir ülkede ofisler kurabilir ve yetkilerini kullanabilir. Çeşitli görevler için şirketin görevlilerini ve acentelerini atayabilir ve ücretlerini belirleyebilir. Bir şirketin adı "corporation" kelimesini veya kısaltması "corp."içermelidir.  Bir şirketin adı, aynı eyalette kurulmuş başka bir şirketin adıyla aldatıcı bir şekilde benzer olmamalıdır. Eyalette ticari işlemleri olan yabancı bir şirket tarafından kabul edilen kurgusal isimle aldatıcı bir şekilde aynı olmamalıdır. Şirket, bir veya daha fazla doğal kişi tarafından tescil sekreterine kuruluş sözleşmesini imzalayarak ve dosyayarak kurulur. Yönetim kurulu üyeleri için nitelikler, kuruluş sözleşmesi veya tüzük tarafından belirlenir. İlk yönetim kurulu üyelerinin adları ve adresleri ve kuruluş amacı, kuruluş sözleşmesinde belirtilmelidir. Kuruluş sözleşmesi, şirketin adını, ihraç etmeye yetkili olduğu hisselerin sayısını, şirket tarafından yürütülen işin karakterinin kısa bir açıklamasını, halefleri seçilene kadar yönetim kurulu üyelerinin adlarını ve adreslerini ve kurucuların adlarını ve adreslerini içermelidir. Hisedarlar, yönetim kurulu büyüklüğünü değiştirme yetkisine sahiptir.

## Kod Açıklaması
```python
print("Number of characters:", len(text))
```
Bu satır, `text` değişkeninin karakter sayısını yazdırır.

```python
summary = summarize(text, 50)
```
Bu satır, `text` değişkenini özetler ve `summary` değişkenine atar. `summarize` fonksiyonu, metni özetlemek için kullanılır ve ikinci parametre olarak özetin maksimum uzunluğunu alır.

```python
wrapped_summary = textwrap.fill(summary, width=70)
```
Bu satır, `summary` değişkenini 70 karakter genişliğinde bir metin olarak biçimlendirir.

```python
print("\nSummarized text:\n", wrapped_summary)
```
Bu satır, özetlenen metni yazdırır.

## Hugging Face Model Kullanımı
```python
from transformers import T5Tokenizer, T5ForConditionalGeneration
tokenizer = T5Tokenizer.from_pretrained("google/flan-t5-xl")
model = T5ForConditionalGeneration.from_pretrained("google/flan-t5-xl", device_map="auto")
```
Bu satırlar, Hugging Face kütüphanesini kullanarak FLAN-T5 XL modelini yükler.

```python
input_text = "translate English to German: How old are you?"
input_ids = tokenizer(input_text, return_tensors="pt").input_ids.to("cuda")
outputs = model.generate(input_ids)
print(tokenizer.decode(outputs[0]))
```
Bu satırlar, İngilizce'den Almanca'ya çeviri yapmak için FLAN-T5 XL modelini kullanır.

## Çıktı
```
Number of characters: 1816
Preprocessed and prepared text:
summarize: The law regarding the corporation prescribes that a corporation...
Summarized text:
 a corporation can be incorporated in the state of Montana to serve any
lawful purpose. it can sue and be sued in its corporate name, and it
has perpetual succession. the name of the corporation must contain the
word "corp
```
Bu çıktı, orijinal metnin özetlenmiş halini gösterir.

Wie alt sind Sie? (İngilizce'den Almanca'ya çeviri çıktısı)

---

