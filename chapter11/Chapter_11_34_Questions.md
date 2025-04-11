# Prompt Tasarımı ve Doğru/Yanlış Soruları Çevirisi

Aşağıda verilen İngilizce paragrafın birebir Türkçe çevirisi yapılmıştır.

## Orijinal Paragraf
Prompt design is the same thing as prompt engineering. (True/False) 
OpenAI doesn’t have embedding models. (True/False) 
Ada is a chat model, not an embedding model. (True/False) 
An Ada embedding vector contains two dimensions. (True/False) 
GPT-3.5-turbo cannot answer questions. (True/False) 
GPT-4 has better reasoning abilities than GPT-3.5 turbo. (True/False) 
We don’t need to manage cost parameters. (True/False) 
GPT models don’t have a maximum input token limit. (True/False) 
A query must be embedded before being used with an embedded dataset. (True/False) 
Embeddings-based search can be an effective alternative to fine-tuning a model. (True/False)

## Çevirisi
Prompt tasarımı, prompt mühendisliği ile aynı şeydir. (Doğru/Yanlış) 
OpenAI'ın embedding modelleri yoktur. (Doğru/Yanlış) 
Ada, bir embedding modeli değil, bir sohbet modelidir. (Doğru/Yanlış) 
Bir Ada embedding vektörü iki boyut içerir. (Doğru/Yanlış) 
GPT-3.5-turbo soruları cevaplayamaz. (Doğru/Yanlış) 
GPT-4, GPT-3.5 turbo'dan daha iyi muhakeme yeteneğine sahiptir. (Doğru/Yanlış) 
Maliyet parametrelerini yönetmemize gerek yoktur. (Doğru/Yanlış) 
GPT modellerinin maksimum girdi token limiti yoktur. (Doğru/Yanlış) 
Bir sorgu, gömülü bir veri seti ile kullanılmadan önce gömülmelidir. (Doğru/Yanlış) 
Embedding tabanlı arama, bir modeli fine-tuning yapmaya etkili bir alternatif olabilir. (Doğru/Yanlış)

Bu çeviride herhangi bir Python kodu bulunmamaktadır. Çeviri işlemi basit bir dil çevirisi işlemidir. 

Eğer bir Python kodu ile bu doğru/yaniış sorularını cevaplamak isteseydik, aşağıdaki gibi bir kod yazabilirdik:

```python
# Doğru/Yanlış sorularını cevaplamak için bir sözlük oluşturma
sorular = {
    "Prompt design is the same thing as prompt engineering.": True,
    "OpenAI doesn’t have embedding models.": False,
    "Ada is a chat model, not an embedding model.": True,
    "An Ada embedding vector contains two dimensions.": False,
    "GPT-3.5-turbo cannot answer questions.": False,
    "GPT-4 has better reasoning abilities than GPT-3.5 turbo.": True,
    "We don’t need to manage cost parameters.": False,
    "GPT models don’t have a maximum input token limit.": False,
    "A query must be embedded before being used with an embedded dataset.": True,
    "Embeddings-based search can be an effective alternative to fine-tuning a model.": True
}

# Kullanıcıdan soruları cevaplamasını isteme
for soru, cevap in sorular.items():
    print(f"Soru: {soru} (Doğru/Yanlış)")
    kullanici_cevap = input("Cevabınız: ")
    if (kullanici_cevap.lower() == "doğru" and cevap) or (kullanici_cevap.lower() == "yanlış" and not cevap):
        print("Doğru!\n")
    else:
        print(f"Yanlış! Doğru cevap {'Doğru' if cevap else 'Yanlış'}.\n")
```

Bu kod, soruları kullanıcıya sorar ve kullanıcının cevaplarını doğrular. Her bir soru için doğru cevapları bir sözlükte saklar ve kullanıcının girdiği cevapları bu doğru cevaplarla karşılaştırır.

---

