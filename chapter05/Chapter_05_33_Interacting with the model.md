# Arayüzü Oluşturma

Arayüzü oluşturmak için, ipywidgets'i yükleyin: 
```python
import ipywidgets as widgets
from IPython.display import display

def model_predict_interface(sentence):
    prediction = predict(sentence, model, tokenizer)
    if prediction == 0:
        return "Dilbilgisi Kurallarına Uymuyor"
    elif prediction == 1:
        return "Dilbilgisi Kurallarına Uygun"
    else:
        return f"Etiket: {prediction}"

text_input = widgets.Textarea(
    placeholder='Bir şeyler yazın',
    description='Cümle:',
    disabled=False,
    layout=widgets.Layout(width='100%', height='50px')  # Genişlik ve yükseklik burada ayarlanır
)

output_label = widgets.Label(
    value='',
    layout=widgets.Layout(width='100%', height='25px'),  # Genişlik ve yükseklik burada ayarlanır
    style={'description_width': 'initial'}
)

def on_text_submit(change):
    output_label.value = model_predict_interface(change.new)

text_input.observe(on_text_submit, names='value')
display(text_input, output_label)
```

Son olarak, Şekil 5.9'da gösterildiği gibi, doğru veya yanlış olarak gerçek zamanlı olarak sınıflandırılan cümleleri girerek etkileşimde bulunuyoruz: 
# Şekil 5.9: Dilbilgisi Kurallarına Uygun Bir Cümle

Aşağıda dilbilgisi kurallarına uymayan bir örnek verilmiştir: 
# Şekil 5.10: Dilbilgisi Kurallarına Uymayan Bir Cümle

Model genelleştirildiğinde kapsamı keşfetmek ve sınırları bulmak için daha fazla örnek girin. 
Artık eksiksiz bir eğitim sürecinden geçtik ve eğitilmiş modelimizle etkileşimde bulunduk! 
Şimdi ince ayar yolculuğumuzu özetleyelim.

**Kod Açıklamaları:**

1. `import ipywidgets as widgets`: ipywidgets kütüphanesini widgets takma adıyla içe aktarır.
2. `from IPython.display import display`: IPython.display kütüphanesinden display fonksiyonunu içe aktarır.
3. `def model_predict_interface(sentence):`: model_predict_interface adında bir fonksiyon tanımlar. Bu fonksiyon, bir cümleyi girdi olarak alır ve modelin tahminini döndürür.
4. `prediction = predict(sentence, model, tokenizer)`: predict fonksiyonunu çağırarak cümlenin tahminini yapar.
5. `if prediction == 0: return "Dilbilgisi Kurallarına Uymuyor"`: Tahmin 0 ise, "Dilbilgisi Kurallarına Uymuyor" döndürür.
6. `elif prediction == 1: return "Dilbilgisi Kurallarına Uygun"`: Tahmin 1 ise, "Dilbilgisi Kurallarına Uygun" döndürür.
7. `else: return f"Etiket: {prediction}"`: Tahmin 0 veya 1 değilse, etiket değerini döndürür.
8. `text_input = widgets.Textarea(...)`: Bir Textarea widget'ı oluşturur.
9. `output_label = widgets.Label(...)`: Bir Label widget'ı oluşturur.
10. `def on_text_submit(change):`: on_text_submit adında bir fonksiyon tanımlar. Bu fonksiyon, text_input widget'ındaki değişiklikleri izler.
11. `output_label.value = model_predict_interface(change.new)`: model_predict_interface fonksiyonunu çağırarak yeni değeri işler ve output_label widget'ının değerini günceller.
12. `text_input.observe(on_text_submit, names='value')`: text_input widget'ını izler ve on_text_submit fonksiyonunu çağırır.
13. `display(text_input, output_label)`: text_input ve output_label widget'larını görüntüler.

---

