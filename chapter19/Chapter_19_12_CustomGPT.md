# HuggingGPT ile Doğrulama ve CustomGPT'nin Uygulanması

HuggingGPT aracılığıyla doğrulama veri setimizle bir sonuç elde etmeye çalıştık. HuggingGPT'nin doğru bir şekilde analiz edemediği çok zor bir görüntüyü değiştirecektik. Bu durumda, AI'nın fantastik ve otomatikleştirilmiş F-AGI araçlarıyla kolayca uygulanabilir olduğunu gösteren parlak, iyimser bir not defteri olacaktı. Ne yazık ki, yenilikçi bir HuggingGPT sistemi bile tüm AI problemlerini çözemez. HuggingGPT sistemi, tüm NLP ve bilgisayarlı görü görevleri için mevcut olan tüm modelleri içermemektedir, ancak iyi bir girişimdir. Bir AI uzmanı, belirli bir AI probleminin çözülemeyeceğini veya çözülebileceğini doğrulamak zorunda kalacaktır. Bu bölümde, bazı durumlarda yaratıcı çözümlerin işe yarayabileceğini gösteriyoruz. HuggingGPT gibi çapraz platform çoklu-model bir sistem kavramını temel alacağız. Bu durumda, belirli bir problemi çözmek için özel bir işlem hattı oluşturuyoruz. Şekil 19.7'de gösterilen CustomGPT, çapraz platform zincirli-model çözümü uygulayacağız.

## CustomGPT'nin Dört Adımlı İşlemi
Şekil 19.7: CustomGPT'nin dört adımlı işlemi

Bu bölümdeki CustomGPT işlemi, AI Uzmanlarının yaratıcılıkla karmaşık problemleri çözebileceğini gösteriyor:
- Özel bir uygulama, girdiyi işler ve özel bir görev planlama işlem hattına gönderir.
- Özel denetleyici, model seçimini yönetir. Bu seçim, CustomGPT kullanıcıları tarafından görüntülenebilen bir arayüzde veya sistem tarafından belirli bir görev için otomatik olarak başlatılabilir.
- İşlem hattı daha sonra seçilen modelleri çalıştırır. Bu örnekte, Google Cloud Vision'ın çıktısı ChatGPT'nin girdisine zincirlenir. ChatGPT'nin çıktısı, Google Cloud Vision tarafından sağlanan özelliklerin anlamsal analizini gerçekleştirir.

İlk olarak, doğrulama veri seti için özellikler sağlamak üzere Google Cloud Vision'ı isteyeceğiz. Çok zor görüntü üzerinde ChatGPT'yi çalıştıracağız. CustomGPT, etkileşimli işlevlere sahip bir prototip olsa da, gerçek bir projede otomatikleştirilebilir.

HuggingGPT ve CustomGPT'nin potansiyelini anlamak kritik önem taşıyor. Neden? Çünkü kısa vadede AI yeniliklerini abartma ve uzun vadede hafife alma eğilimindeyiz. Yakın gelecek için hazır olmak, bir AI profesyonelinin kariyerinde temel bir faktör haline geldi. İlk olarak, ChatGPT, GPT-4'ü çalıştırmadan önce Google Cloud Vision'ı çalıştıracağız.

Python kodları bulunmamaktadır, ancak anlatılan işlem adımlarına göre bir pseudo kod aşağıdaki gibi olabilir:
```python
# Özel uygulama, girdiyi işler ve özel görev planlama işlem hattına gönderir
input_data = preprocess_input(data)

# Özel denetleyici, model seçimini yönetir
selected_model = custom_controller.select_model(input_data)

# İşlem hattı, seçilen modelleri çalıştırır
output = pipeline.run(selected_model, input_data)

# Google Cloud Vision'ın çıktısı ChatGPT'nin girdisine zincirlenir
google_cloud_vision_output = google_cloud_vision(input_data)
chatgpt_output = chatgpt(google_cloud_vision_output)

# ChatGPT'nin çıktısı, Google Cloud Vision tarafından sağlanan özelliklerin anlamsal analizini gerçekleştirir
semantic_analysis = analyze(chatgpt_output)
```
Yukarıdaki pseudo kod, anlatılan işlem adımlarını temsil etmektedir. Gerçek bir Python kodu, kullanılan kütüphane ve framework'lere bağlı olarak değişecektir.

---

