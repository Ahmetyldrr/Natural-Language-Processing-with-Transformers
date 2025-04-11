# BertViz ile BERT Modelinin İç Mekanizmalarını Anlamak

BertViz, BERT, GPT, RoBERTa ve diğer modelleri destekler. Daha fazla bilgi için GitHub'daki BertViz'e başvurabilirsiniz: https://github.com/jessevig/BertViz . 5. Bölüm'de, BERT aracılığıyla İnce Ayar'a daldık ve bir bert-base-uncased modelini ince ayarladık. Bu bölümde, aynı zamanda bir bert-base-uncased modeli ve önceden eğitilmiş bir tokenleştirici çalıştırarak iç mekanizmalarına olan anlayışımızı derinleştireceğiz:

## Modeli Yükleme ve Dikkat Alma
```python
model_version = 'bert-base-uncased'
do_lower_case = True
model = BertModel.from_pretrained(model_version, output_attentions=True)
tokenizer = BertTokenizer.from_pretrained(model_version, do_lower_case=do_lower_case)
```
*   `model_version` değişkeni, kullanılacak BERT modelinin versiyonunu belirler. Burada 'bert-base-uncased' kullanılmaktadır.
*   `do_lower_case` değişkeni, tokenleştirme sırasında metnin küçük harfe çevrilip çevrilmeyeceğini belirler. Burada `True` olarak ayarlanmıştır.
*   `BertModel.from_pretrained()` fonksiyonu, önceden eğitilmiş BERT modelini yükler. `output_attentions=True` parametresi, modelin dikkat ağırlıklarını döndürmesini sağlar.
*   `BertTokenizer.from_pretrained()` fonksiyonu, önceden eğitilmiş tokenleştiriciyi yükler.

## Giriş Cümlelerini Belirleme
```python
sentence_a = "A lot of people like animals so they adopt cats"
sentence_b = "A lot of people like animals so they adopt dogs"
inputs = tokenizer.encode_plus(sentence_a, sentence_b, return_tensors='pt', add_special_tokens=True)
```
*   `sentence_a` ve `sentence_b` değişkenleri, modele girilecek iki cümleyi tanımlar.
*   `tokenizer.encode_plus()` fonksiyonu, cümleleri tokenleştirir ve modele girdi olarak uygun bir formatta döndürür. `return_tensors='pt'` parametresi, çıktıların PyTorch tensörleri olarak döndürülmesini sağlar. `add_special_tokens=True` parametresi, özel tokenlerin (örneğin, `[CLS]` ve `[SEP]`) eklenmesini sağlar.

## Girdi Kimliklerini ve Dikkat Ağırlıklarını Alma
```python
token_type_ids = inputs['token_type_ids']
input_ids = inputs['input_ids']
attention = model(input_ids, token_type_ids=token_type_ids)[-1]
```
*   `token_type_ids` değişkeni, her bir tokenin hangi cümleye ait olduğunu belirtir.
*   `input_ids` değişkeni, tokenleştirilmiş cümlelerin kimliklerini içerir.
*   `model()` fonksiyonu, girdi kimliklerini ve token tür kimliklerini alır ve modelin çıktısını döndürür. `[-1]` indeksi, dikkat ağırlıklarını döndürür.

## Cümle B Başlangıcını ve Tokenleri Alma
```python
sentence_b_start = token_type_ids[0].tolist().index(1)
input_id_list = input_ids[0].tolist() 
tokens = tokenizer.convert_ids_to_tokens(input_id_list)
```
*   `sentence_b_start` değişkeni, ikinci cümlenin başlangıç indeksini belirler.
*   `input_id_list` değişkeni, girdi kimliklerini bir liste olarak döndürür.
*   `tokenizer.convert_ids_to_tokens()` fonksiyonu, kimlikleri tokenlere çevirir.

Artık görselleştirme arayüzü ile etkileşime geçmeye hazırız.

---

