# Bölüm 20: Otomatik Üretken Fikir Üretme Çerçevesi

Şekil 20.1, bu bölümde uygulanan çerçeveeyi göstermektedir:
# Şekil 20.1: Üretken Yapay Zeka Fikir Üretme Çerçevesi

Bu bölümde, otomatik üretken fikir üretmenin dört adımlı geliştirme sürecini ele alacağız:
## Adım 1: İstem Yok
Python kodu gibi otomatik özellikler, artık klasik olan Üretken Yapay Zeka (Generative AI) Retrieval Augmented Generation (RAG) sürecinde belge almayı, ayrıştırmayı ve aramayı otomatikleştirecektir. 
```python
# Burada python kodları olabilir, ancak metinde yok.
```
Eski, klasik kural tabanlı ayrıştırma ve sorgu programlama, kullanıcı eylemlerini tıklama ve çalıştırma özellikleriyle sınırlamak için kolaylaştıracaktır. Klasik web tasarım prototipleri, uygulama geliştirme için temel sağlayacaktır.

## Adım 2: Üretken Yapay Zeka: İstem Oluşturma
Bir istem, üretken içerik tetiklemeyecek, ancak zincirleme üretken modeller için istemler üretecektir. İnsan tasarımı istemlerinden Üretken Yapay Zeka istemlerine geçiş, zaman alıcı ve deneme-yanılma yaklaşımları gerektiren istemleri hayal etmekten kaçınmak isteyen kullanıcılara yardımcı olacaktır. Bu, başka bir RAG'dir; burada otomatik bir sistem, belgeleri alacak (Yukarıdaki Adım 1) ve başka bir Üretken Yapay Zeka modelinin girdisi olacak istemleri oluşturmak için ayrıştıracaktır. 
```python
# Llama ve GPT-4 modellerinin kullanımı ile ilgili python kodu örneği:
# import torch 
# from transformers import AutoModelForCausalLM, AutoTokenizer

# model = AutoModelForCausalLM.from_pretrained("Llama")
# tokenizer = AutoTokenizer.from_pretrained("Llama")

# input_ids = tokenizer.encode("İstem oluşturma metni", return_tensors="pt")
# output = model.generate(input_ids, max_length=100)
# print(tokenizer.decode(output[0], skip_special_tokens=True))
```
Llama ve GPT-4, insan tasarım sürecinin yerini alacaktır. Bu süreç, bir geliştirme yatırımı gerektirir, ancak insan kaynakları ve bütçeler kıt olduğunda, doğru istemi bulma yükünden son kullanıcıları kurtaracaktır.

Large Language Model Meta AI (LLaMA), Meta tarafından bir model olarak kullanıldığında genellikle Llama olarak yazılır: https://llama.meta.com/ 
Hem LLaMA (daha akademik) hem de Llama, bu bölümde kullanılacaktır.

## Adım 3: Üretken Yapay Zeka: Görüntü Oluşturma
Bu bölüm, bilgisayar vizyonuna odaklanmaktadır. Ekosistemin amacı, Midjourney, Microsoft Designer (DALL-E ve GPT modelleri) ve Stable Diffusion için Üretken Yapay Zeka metin çıktılarını metin-görüntü girdilerine zincirlemektir.

## Adım 4: Yanıt Üretme
Çıktılar, görüntü çıktıları ve metin-görüntü eserleri olacaktır. Ekosistemi oluşturmak geliştirme gerektirir, ancak son uygulama, son kullanıcı için tıklama ve çalıştırma ile sınırlı olmalıdır.

---

