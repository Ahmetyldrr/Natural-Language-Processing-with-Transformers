# Notebook'un Soruları Cevaplama İşlevi

Notebook'un `ask` işlevselliği, tüm gömülü tabanlı soru-cevap sürecini otomatize eder. `ask` işlevselliği, bir isteğin belirteç sayısını sayarak başlar. Amaç, mesajdaki belirteç sayısının belirteç bütçesini (model limiti, proje limiti) aşmadığından emin olmaktır:

```python
def num_tokens(text: str, model: str = GPT_MODEL) -> int:
    """Bir dizenin belirteç sayısını döndürür."""
    encoding = tiktoken.encoding_for_model(model)
    return len(encoding.encode(text))
```

Örneğin, bu durumda belirteç bütçesi 4.096 (toplam belirteç limiti) eksi 500 (isteğin belirteçleri) olarak sınırlandırılacaktır, çünkü GPT-3'in maksimum limiti 4.096 belirteçtir. Belirteç bütçelerini yönetirken hem isteği göndermemiz hem de yanıt için yer bırakmamız gerekir.

Sorgu mesajı işlevi, sorgu dizesini, pandas DataFrame'i, modeli ve belirteç bütçesini alır:

```python
def query_message(query: str, df: pd.DataFrame, model: str, token_budget: int) -> str:
```

Daha sonra `relatedness` işlevini kullanarak makaleleri bulacaktır:

```python
strings, relatednesses = strings_ranked_by_relatedness(query, df)
```

Daha sonra sorguyu yanıtlamak için talimatlar veren bir giriş mesajı hazırlayacaktır:

```python
introduction = 'Aşağıdaki 2022 Kış Olimpiyatları hakkındaki makaleleri kullanarak sonraki soruyu yanıtlayın. Cevap makalelerde bulunamazsa, "Cevap bulamadım" yazın.'
```

Girişi `message` değişkeninde saklayacak ve daha sonra makaleleri ekleyecektir:

```python
message = introduction
```

Daha sonra soruyu tanımlar:

```python
question = f»\n\nSoru: {query} »
```

Son olarak, işlev `token_budget` aşılana kadar makaleleri `next_article`'a ekler:

```python
for string in strings:
    next_article = f'\n\nWikipedia makale bölümü:\n"""\n {string} \n"""'
    if (
        num_tokens(message + next_article + question, model=model)
        > token_budget
    ):
        break
```

Ayrıca, belirteç bütçesi aşılana kadar makalelerin içeriği, zaten girişi içeren `message`'a eklenir:

```python
else:
    message += next_article
return message + question
```

GPT isteği etkin bir şekilde otomatize edilmiştir. Soru-cevap sistemini çalıştırabiliriz.

---

