# İnce Ayar BERT
Bu bölümde BERT'i ince ayar yapma hedefi, Bölüm 3'te görüldüğü gibi CoLA veri seti ile bir metnin gramatik kabul edilebilirliğini değerlendirme yeteneğine odaklanmaktır. Bu nedenle, gerekirse Bölüm 3'ün CoLA bölümüne geri dönmek için biraz zaman ayırın. Projenize bağlı olarak, Bölüm 3'te incelediğimiz bazı görevleri de dahil olmak üzere diğer görevleri ince ayar için seçebilirsiniz. Tahminleri, Matthews Korelasyon Katsayısı (MCC) ile ölçeceğiz, bu da Değerlendirme bölümünde Matthews korelasyon katsayısı kullanılarak açıklanacaktır.

## Google Colab'de BERT_Fine_Tuning_Sentence_Classification_GPU.ipynb Dosyasını Açma
Google Colab'de BERT_Fine_Tuning_Sentence_Classification_GPU.ipynb dosyasını açın (bir Gmail hesabınız olduğundan emin olun). Notebook, bu kitabın GitHub deposunda Chapter05'te bulunmaktadır. Notebook'taki her hücrenin başlığı, her bölüm alt başlığının başlığı ile aynı veya çok yakındır. Öncelikle, neden transformer modellerinin donanım kısıtlamalarını dikkate almak zorunda olduğunu inceleyeceğiz.

**Çeviride kullanılan Python kodları bulunmamaktadır.**

Eğer bir kod bloğu olsaydı, satır satır açıklama aşağıdaki gibi olurdu:
```python
# Örnek bir python kodu
def example_function():
    # Fonksiyon tanımlama
    x = 5  # x değişkenine 5 değerini atama
    y = x * 2  # y değişkenine x'in 2 katını atama
    return y  # y değerini döndürme

# Fonksiyonu çağırma
result = example_function()
print(result)  # sonucu yazdırma
```
Bu kod bloğu için açıklama:
1. `def example_function():` satırı, `example_function` adında bir fonksiyon tanımlamaktadır.
2. `x = 5` satırı, `x` değişkenine 5 değerini atamaktadır.
3. `y = x * 2` satırı, `y` değişkenine `x` değerinin 2 katını atamaktadır.
4. `return y` satırı, `y` değerini fonksiyonun döndürmesini sağlamaktadır.
5. `result = example_function()` satırı, tanımlanan fonksiyonu çağırmakta ve sonucu `result` değişkenine atamaktadır.
6. `print(result)` satırı, `result` değişkeninin değerini yazdırmaktadır.

---

