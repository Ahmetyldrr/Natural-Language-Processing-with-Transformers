# OpenAI Örneği: Dilbilgisi Düzeltme Görevi

Bir dilbilgisi düzeltme görevi için OpenAI örneğini kopyalayıp yapıştırıyoruz:

```python
from openai import OpenAI
client = OpenAI()
response = client.chat.completions.create(
  model="gpt-4",
  messages=[
    {"role": "system", "content": "You will be provided with statements, and your task is to convert them to standard English."},
    {"role": "user", "content": "She no went to the market."}
  ],
  temperature=0,
  max_tokens=256,
  top_p=1,
  frequency_penalty=0,
  presence_penalty=0
)
```

Bu kodun yaptığı şey, OpenAI kütüphanesini kullanarak bir dilbilgisi düzeltme görevi gerçekleştirmektir.

## Kodun Adım Adım Açıklaması

1. `from openai import OpenAI`: OpenAI kütüphanesinden `OpenAI` sınıfını içe aktarıyoruz.
2. `client = OpenAI()`: `OpenAI` sınıfından bir nesne oluşturuyoruz.
3. `response = client.chat.completions.create(...)`: `client` nesnesinin `chat.completions.create` metodunu çağırarak bir dilbilgisi düzeltme görevi gerçekleştiriyoruz.

### `create` Metodunun Parametreleri

* `model="gpt-4"`: Kullanılacak modelin adı (`gpt-4`).
* `messages=[...]`: Görev için gerekli olan mesajları içeren bir liste.
	+ `{"role": "system", "content": "You will be provided with statements, and your task is to convert them to standard English."}`: Sistem mesajı.
	+ `{"role": "user", "content": "She no went to the market."}`: Kullanıcı mesajı (dilbilgisi hatası içeren cümle).
* `temperature=0`: Çıktının yaratıcılığını kontrol eden parametre (0 = en düşük yaratıcılık).
* `max_tokens=256`: Çıktının maksimum uzunluğu (token sayısı).
* `top_p=1`: Çıktının olasılık dağılımını kontrol eden parametre (1 = en yüksek olasılık).
* `frequency_penalty=0`: Çıktıda sık kullanılan tokenlere uygulanacak ceza (0 = ceza yok).
* `presence_penalty=0`: Çıktıda mevcut tokenlere uygulanacak ceza (0 = ceza yok).

## Yanıtın İşlenmesi

Görev sonucu elde edilen yanıt (`response`) bir sözlük nesnesidir. Bu nesne, görev hakkında ayrıntılı bilgi içerir.

Yanıtı işleyerek dilbilgisi doğru cümleyi elde edebiliriz:
```python
print(response.choices[0].message.content)
```

Bu kod, yanıtın `choices` listesindeki ilk öğenin `message` özelliğinin `content` değerini yazdırır.

## Çıktı

Dilbilgisi doğru cümle: "She didn't go to the market."

## Çıktının Kontrol Edilmesi

Çıktıyı çeşitli parametrelerle kontrol edebilirsiniz.

# Türkçe Çeviri
Dilbilgisi düzeltme görevi için OpenAI örneğini kopyalayıp yapıştırıyoruz: OpenAI kütüphanesinden OpenAI sınıfını içe aktarıyoruz.
İstemci = OpenAI() 
yanıt = istemci.chat.tamamlamalar.oluştur(
  model= "gpt-4" ,
  mesajlar=[
    { "rol" : "sistem" , "içerik" : "Size ifadeler verilecek ve göreviniz bunları standart İngilizceye çevirmektir." },
    { "rol" : "kullanıcı" , "içerik" : "Pazara gitmedi." } # Doğrusu "She didn't go to the market." olmalıydı, burada örnek olarak "She no went to the market." kullanılmış
  ],
  sıcaklık= 0 ,
  maksimum_jeton= 256 ,
  üst_p= 1 ,
  frekans_cezası= 0 ,
  varlık_cezası= 0 ) Görev, bu dilbilgisi hatasını düzeltmektir: Pazara gitmedi. Yanıtı ayrıştırarak istediğimiz gibi işleyebiliriz. OpenAI’ın yanıtı bir sözlük nesnesidir. OpenAI nesnesi, görev hakkında ayrıntılı bilgi içerir. Nesnenin görüntülenmesini isteyebiliriz: print (yanıt.seçenekler[ 0 ].mesaj.içerik) Sözlükteki “metin” çıktısı dilbilgisi açısından doğru cümledir: Pazara gitmedi. (İngilizce karşılığı) She didn't go to the market. Çıktıları çeşitli parametrelerle yönlendirebilirsiniz.

---

