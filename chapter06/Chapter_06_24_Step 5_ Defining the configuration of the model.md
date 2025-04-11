# Yapılandırma Hücresinin Ana Hattı

Yapılandırma hücresinin ana hattı şu şekildedir: 
```python
from transformers import RobertaConfig, RobertaForCausalLM
```
`RobertaForCausalLM`, model ön eğitimi yapmak isteyenler için değerli bir varlık olan Üretken Yapay Zeka (Generative AI) için kullanılabilir.

## Model Yapılandırması

Dikkat edilmesi gereken bir diğer özellik de modelin yapılandırılmasıdır:
```python
config = RobertaConfig(
    vocab_size=52_000,
    max_position_embeddings=514,
    num_attention_heads=12,
    num_hidden_layers=6,
    type_vocab_size=1,
    is_decoder=True,  # Modeli potansiyel seq2seq kullanımı için ayarlayarak otoregresif çıktılara izin verir
)
```
`is_decoder=True` parametresi, RoBERTa modeline otoregresif işlevsellik ekler, genellikle maskelerle uygulanır. Bir maske, bir kelime dizisinde herhangi bir yerde olabilir. Otoregresif bir model, son tokendan itibaren bir diziyi devam ettirir.

## Üretken Yapay Zeka Modelinin Tanımlanması

Artık Üretken Yapay Zeka modelimizi tanımlayabiliriz:
```python
# Belirtilen yapılandırmayla RobertaForCausalLM modelini oluşturun
model = RobertaForCausalLM(config=config)
print(model)
```
## Tokenizer Kullanımı

Hugging Face'in RoBERTa tokenizörünü kullanacağız:
```python
tokenizer = RobertaTokenizer.from_pretrained('roberta-base')
```
Tokenizör, özel tokenler içerir, ancak örneğin maskeye ihtiyacımız olmayacak.

---

