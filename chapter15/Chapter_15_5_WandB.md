# WandB Gelişmiş Yapay Zeka Takip Kabiliyetleri

WandB'nin gelişmiş yapay zeka takip kabiliyetleri vardır. Geleceği hayal edin. Bir gün OpenAI GPT-4'ün WandB takip bilgilerini kendi aktivitesi üzerinde, örneğin Auto-Big-bench.ipynb not defterinde olduğu gibi, anlayabileceğini hayal edin. Yapay zeka bunu bir kez yapabilir hale geldiğinde, işlevsel AGI'nin kapısı geniş açıktır! Bu bölümün deposundan Open WandB_Prompts_Quickstart.ipynb not defterini açın. Not defteri kendi kendini açıklayıcıdır. 8. Bölüm, OpenAI GPT Modellerini Fine-Tuning  bölümünde gördüğümüz gibi, bir WandB anahtarına ve bir OpenAI anahtarına ihtiyacınız olacak. Not defterini çalıştırabilir ve WandB'nin OpenAI ve LangChain aktivitesini nasıl takip edebileceğini görmek için talimatları takip edebilirsiniz.

## Kodların İncelenmesi

Şimdi aşağıdaki hücreyi inceleyelim:
```python
tool_span.add_named_result({ "input" : "search: google founded in year" }, { "response" : "1998" })
chain_span.add_named_result({ "input" : "calculate: 2023 - 1998" }, { "response" : " 25" })
llm_span.add_named_result({ "input" : "calculate: 2023 - 1998" , "system" : "you are a helpful assistant" , },
                          { "response" : "25" , "tokens_used" : 218 })
parent_span.add_child_span(tool_span)
parent_span.add_child_span(chain_span)
parent_span.add_named_result({ "user" : " calculate: 2023 - 1998" },
                             { "response" : "25 years old" })
```
Bu kodlar, LangChain framework'unun bir parçası olarak kullanılan bazı nesnelerin (`tool_span`, `chain_span`, `llm_span`, `parent_span`) metodlarını çağırmaktadır.

- `add_named_result` metodu, ilgili nesneye bir isimli sonuç ekler. Bu metod, iki parametre alır: 
  - Birinci parametre, girdi bilgilerini içeren bir sözlüktür (`dict`).
  - İkinci parametre, çıktı bilgilerini içeren bir sözlüktür (`dict`).

Örneğin, `tool_span.add_named_result({ "input" : "search: google founded in year" }, { "response" : "1998" })` satırı, `tool_span` nesnesine bir girdi-çıktı çifti ekler. Girdi `"search: google founded in year"` iken, çıktı `"1998"`dir.

- `add_child_span` metodu, bir üst nesneye (`parent_span`) bir alt nesne (`tool_span` veya `chain_span`) ekler. Bu, bir hiyerarşi oluşturmak için kullanılır.

## LangChain ve WandB'nin Kullanımı

LangChain (https://www.langchain.com/), sezgisel bir framework olup, dil modelleri, araçlar ve kütüphaneler ile etkileşimde bulunmak için önceden yazılmış kodlar sağlar. Bu bölümde, LangChain'i NLP görevlerini gerçekleştirmek için kullanıyoruz. Hücreyi çalıştırdığımızda, görevin ayrıntılı sürecine Our Account (kendi hesabınızı kullanmalısınız) tıklayarak erişebilirsiniz. Çalışmayı https://wandb.ai/rothman/wandb_prompts_demo/runs/6r8aef4i adresinden görüntüleyebilirsiniz. Çağrının ayrıntılarını görselleştirebileceksiniz:

# Şekil 15.3: Weights & Biases çağrının ayrıntıları

## Sonuç

WandB'nin derin takip içgörüleri sağladığı açıktır. BIG-bench deneyi, yapay zekanın kendini analiz etme ve potansiyel olarak kendi hatalarını düzeltme, hiperparametrelerini değiştirme, eğitim verilerini optimize etme, kendi modelinin kopyaları üzerinde eğitim işleri çalıştırma (bir modelin deposunu kopyalamak kolaydır) ve daha fazlasını yapma potansiyeline sahip olduğunu göstermektedir. WandB, izleme potansiyelini gösterir ve bu potansiyel, takip araçlarından ne yapacağını öğrenebilecek yapay zeka algoritmalarıyla birleştirilebilir. Bir sonraki adımın, kendilerini kopyalayabilen yapay zeka ajanları olabileceği düşüncesi üzerinde düşünmeye zaman ayırın.

---

