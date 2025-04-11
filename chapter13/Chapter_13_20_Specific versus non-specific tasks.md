# T5 Modeli ve ChatGPT Özeti

T5, bu bölümde gördüğümüz gibi, görev-specifik parametreler kullanarak metin-metne özel görevlere odaklanır: 
```json
"task_specific_params" : { 
  "summarization" : { 
    "early_stopping" : true, 
    "length_penalty" : 2.0 , 
    "max_length" : 200 , 
    "min_length" : 30 , 
    "no_repeat_ngram_size" : 3 , 
    "num_beams" : 4 , 
    "prefix" : "summarize: " 
  }
}
```
Bu JSON yapısı, T5 modelinin özetleme görevi için kullandığı özel parametreleri göstermektedir. Şimdi bu kod parçasını satır satır inceleyelim:

*   `"task_specific_params"` : Görev-specifik parametreler
*   `"summarization"` : Özetleme görevi için parametreler
    *   `"early_stopping" : true` : Erken durdurma özelliğini etkinleştirir. 
    *   `"length_penalty" : 2.0` : Üretilen metinlerin uzunluğuna göre uygulanan ceza katsayısı.
    *   `"max_length" : 200` : Üretilen özetin maksimum uzunluğu.
    *   `"min_length" : 30` : Üretilen özetin minimum uzunluğu.
    *   `"no_repeat_ngram_size" : 3` : Üretilen metinde n-boyutlu aynı kelime öbeğinin tekrar etmesini engellemek için kullanılan parametre.
    *   `"num_beams" : 4` : Işın arama algoritmasındaki ışın sayısını belirler.
    *   `"prefix" : "summarize: "` : Özetleme görevinin başlangıç etiketi.

ChatGPT ise birçok diğer spesifik görevde olduğu gibi özetleme için de spesifik görev parametrelerine ihtiyaç duymaz, ancak bu onun görev-specifik bir model olmadığı anlamına gelmez. Dil anlayışına, bağlama ve verilen talimata dayalı olarak bir diziyi devam ettiren bir tamamlama modeli olarak kalır. Aşağıdaki bölüm, OpenAI'ın API'si ile ChatGPT'nin özetlemesini uygular.

---

