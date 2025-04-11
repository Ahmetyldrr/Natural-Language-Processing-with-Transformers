# Bilgi Tabandan Veri Çekme ve Kullanıcı İsteklerini Ayrıştırma

Bilgi tabanınızdaki verilere bağlı anahtar kelimeleri içeren bilgileri girdiniz. Aşağıdaki örnek, bir uygulamanın iletişim sayfasında kullanıcının isteğini ayrıştırır: Anahtar kelimelerin listesini gözden geçirin. Her bir anahtar kelime, Bilgi Tabanındaki (KB) bir kaydın etiketi niteliğindedir. İhtiyaç duyduğunuz kadar anahtar kelime (metadata) ekleyebilirsiniz. Ayrıca, web sayfalarında olduğu gibi diğer metadata'ları da ekleyebilir ve arama motoru tekniklerini kullanarak onları da ayrıştırabilirsiniz. Bir anahtar kelime, KB kaydının etiketi, kullanıcının isteğiyle eşleştiğinde, KB kaydı alınır ve ChatGPT'ye gönderilen bilgilerin bir parçası olarak döndürülür. Uygulamanızı özelleştirmek için bu işlevi geliştirebilirsiniz. Bir sohbet botu uygulaması klasik arama işlevlerini içerebilir. Ayrıca, yeni Bing konuşma arayüzünü de keşfedebilirsiniz. Bu notebook'ta olduğu gibi anahtar kelimeleri çıkardığını ve ardından bilgi tabanındaki bağlantıları aradığını unutmayın. Son olarak, KB kaydı/kaydı kullanarak yapay zeka oluşturur. Kullanıcı isteğini ayrıştırmak veya istek-bilgi tabanı benzerliğini aramak için başka bir işlev tasarlamak için bir ayrıştırıcı oluşturmaya hazırsınız. Notebook'taki işlev, kullanıcı isteklerini ayrıştırmak için diğer yöntemler arasında bir yol gösterir.

## Kullanıcı İsteklerini Ayrıştırma Örneği

Bu örnekte, bir dizi kullanıcı isteğini çalıştıracağız:

```python
user_requests = []
user_requests.append({'role': 'user', 'content': 'At what time does Snap-LM Consulting open on Monday?'})
user_requests.append({'role': 'user', 'content': 'At what time does Snap-LM Consulting open on Saturday?'})
user_requests.append({'role': 'user', 'content': 'Can you create an AI-driven expert system?'})
user_requests.append({'role': 'user', 'content': 'What services does Snap-LM Consulting offer?'})
```

### İşlenecek İstek Sayısını Belirleme

İşleyeceğimiz parti için istek sayısını da belirliyoruz:
```python
n = len(user_requests)
```

### Ayrıştırma İşlevini Oluşturma

Ayrıştırma işlevini oluşturuyoruz:
```python
# Bu bir örnektir. Projeniz için istediğiniz gibi özelleştirebilirsiniz
def parse_user(uprompt, kbkw, kbt):
    i = 0
    j = 0
    for kw in kbkw:
        # print(i, kw)
        rq = str(uprompt)
        k = str(kw)
        fi = rq.find(k)
        if fi > -1:
            print(kw, rq, kbt[i])
            j = i
        i += 1
    return kbt[j]
```

## Kod Açıklaması

1. `user_requests` adlı boş bir liste oluşturulur ve `append` methodu kullanılarak bu listeye dört adet sözlük elemanı eklenir. Her bir sözlük, bir kullanıcı isteğini temsil eder ve `role` ve `content` anahtarlarına sahiptir.

2. `n = len(user_requests)` satırı, `user_requests` listesinde bulunan eleman sayısını `n` değişkenine atar.

3. `parse_user` adlı bir işlev tanımlanır. Bu işlev, üç parametre alır:
   - `uprompt`: Kullanıcının isteği
   - `kbkw`: Bilgi tabanındaki anahtar kelimeler
   - `kbt`: Bilgi tabanındaki kayıtlar

4. İşlev içinde, `kbkw` listesindeki her bir anahtar kelime için bir döngü çalıştırılır. Her bir anahtar kelime, kullanıcının isteğinde (`uprompt`) aranır.

5. `rq.find(k)` ifadesi, `k` anahtar kelimesinin `rq` (kullanıcının isteği) içinde olup olmadığını kontrol eder. Eğer anahtar kelime bulunursa (`fi > -1`), anahtar kelime, kullanıcının isteği ve bilgi tabanındaki ilgili kayıt (`kbt[i]`) yazdırılır.

6. İşlev, son bulunan bilgi tabanındaki kaydın indeksini (`j`) döndürür.

Bu kod, kullanıcı isteklerini bilgi tabanındaki anahtar kelimelere göre ayrıştırmak ve ilgili kayıtları döndürmek için kullanılır.

---

