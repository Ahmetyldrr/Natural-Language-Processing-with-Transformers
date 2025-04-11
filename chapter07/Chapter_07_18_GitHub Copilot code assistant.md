# OpenAI'ın Üretken Fonksiyonelliğini Kullanma

OpenAI'ın son teknoloji modellerinin üretken işlevselliğini geliştirme ortamınızda kullanabilirsiniz. Bu bölümde, GitHub Copilot'u JetBrains PyCharm'da çalıştıracağız. İlk olarak, GitHub Copilot'a gidin: https://github.com/features/copilot . Başlamak için belgeleri okuyabilirsiniz: https://docs.github.com/en/copilot/getting-started-with-github-copilot . Bu bölümde, JetBrains PyCharm seçildi: https://www.jetbrains.com/products/compare/?product=pycharm&product=pycharm-ce . JetBrains, PyCharm ve GitHub Copilot'u yüklemek için belgeler sağlar. PyCharm, GitHub Copilot'u yüklemek için bir işlev içerir: 
## Şekil 7.5: PyCharm'da GitHub Copilot'u yüklemekten bir adım uzakta

PyCharm'da GitHub'u etkinleştirebilir ve birkaç tıklamayla çalışmaya başlayabilirsiniz, Şekil 7.6'da gösterildiği gibi:
## Şekil 7.6: PyCharm'da GitHub Copilot etkinleştirme yolu

PyCharm'ın sezgisel bir arayüzü vardır ve kod oluşturmayı etkinleştirmenizi sağlar:
## Şekil 7.7: GitHub Copilot eklentisi adım adım

İstediğiniz bir işlevi, örneğin bir Fibonacci dizisini, bir yorumda (istem) açıklayarak başlayabilirsiniz: 
```python
#create a Fibonacci sequence
```
Kod otomatik olarak oluşturulacaktır ve Tab tuşuna basarak seçebilirsiniz:
```python
def fib(n):
    if n == 0:
        return 0
    elif n == 1:
        return 1
    else:
        return fib(n-2) + fib(n-1)  # recursive call
```
Daha sonra diğer yorumları girerek devam edersiniz, bunlar bir istem görevi görür ve kod göründüğünde Tab tuşuna basarsınız:
```python
# calculate the 10th Fibonacci number
fib(10)
#print output
print(fib(10))
```
Daha sonra kodu ortamınızda çalıştırabilirsiniz. GitHub Copilot, bir kodlama asistanı olarak, üretkenliğinizi artıracaktır. Düşünün ki, daha şimdiden birçok asistanı ele aldık! Ve bunlar, piyasada yayılan asistan sayısının sadece görünen kısmını temsil ediyor. Genel amaçlı örnekler, bizi başka bir NLP görevine ve kodlama asistanına götürecektir.

### Python Kodlarının Açıklaması

1. `#create a Fibonacci sequence`: Bu bir yorumdur ve Python yorumlayıcısı tarafından dikkate alınmaz. GitHub Copilot'a bir Fibonacci dizisi oluşturmasını söyleyen bir istemdir.

2. `def fib(n):`: Bu, `fib` adında bir fonksiyon tanımlar. Bu fonksiyon, Fibonacci dizisinin `n`-inci elemanını hesaplar.

3. `if n == 0: return 0`: Eğer `n` 0 ise, fonksiyon 0 döndürür. Bu, Fibonacci dizisinin ilk elemanıdır.

4. `elif n == 1: return 1`: Eğer `n` 1 ise, fonksiyon 1 döndürür. Bu, Fibonacci dizisinin ikinci elemanıdır.

5. `else: return fib(n-2) + fib(n-1)`: Eğer `n` 0 veya 1 değilse, fonksiyon `n-2` ve `n-1` indeksli elemanların toplamını döndürür. Bu, Fibonacci dizisinin tanımına uygun olarak, her elemanın önceki iki elemanın toplamı olduğu anlamına gelir.

6. `fib(10)`: Bu, `fib` fonksiyonunu `n=10` için çağırır ve 10. Fibonacci sayısını hesaplar.

7. `print(fib(10))`: Bu, `fib(10)` ifadesinin sonucunu yazdırır. 

Bu kod, özyinelemeli (recursive) bir şekilde Fibonacci dizisini hesaplar. Ancak, büyük `n` değerleri için verimsiz olabilir çünkü aynı alt problemleri birçok kez çözer. Daha verimli bir yaklaşım, dinamik programlama kullanmaktır.

---

