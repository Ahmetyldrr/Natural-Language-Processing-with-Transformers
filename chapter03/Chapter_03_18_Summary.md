# ChatGPT'nin Tetiklediği Paradigma Değişimi

ChatGPT tarafından tetiklenen paradigma değişimi, bir NLP görevinin ne olduğunu yeniden tanımlamamıza neden oldu. ChatGPT'nin, diğer LLM modelleri gibi, gelişmiş ortaya çıkış yoluyla birçok SuperGLUE görevi de dahil olmak üzere, eğitilmediği görevleri yerine getirebildiğini gördük. Sayısal hesaplamalar ile kelime dizileri üretme arasındaki boşluğu doldurmak için dikkat başlıklarının çıktılarını inceledik.

## Çoklu Görev Transformerlarının Performansını Ölçme

Daha sonra, çoklu görev transformerlarının performansını nasıl ölçeceğimizi araştırdık. Transformerların downstream görevler için üst sıralarda sonuçlar elde etme yeteneği, NLP tarihinde benzersizdir. GLUE ve SuperGLUE lider tablolarının üst sıralarına transformerları getiren zorlu SuperGLUE görevlerini inceledik. BoolQ, CB, WiC ve kapsadığımız diğer birçok görev, insanlar için bile işlemesi kolay değildir. Transformer modellerinin verimliliklerini kanıtlama zorluğunu gösteren birkaç downstream görev örneğini inceledik.

### Transformerların Değeri ve Uygulaması

Transformerlar, eski NLU mimarilerini geride bırakarak değerlerini kanıtladılar. Downstream ince ayarlı görevleri uygulamanın ne kadar basit olduğunu göstermek için, daha sonra Hugging Face'in transformerlar için pipeline'ını kullanarak bir Google Colaboratory notebook'unda birkaç görev çalıştırdık. Winograd şemalarında, Transformer'a İngilizce-Fransızca çeviri için bir Winograd belirsizlik problemi çözme zorluğunu verdik.

## NLP Değerlendirme İşlemi

Bu bölümde, SuperGLUE ve bazı görevlerle NLP değerlendirme işlemini inceledik. Daha fazlası için bu bölümün "İleri Okuma" bölümüne bakınız.

# İleri Bölüm: Çeviri Görevlerinde İlerlemeler

Bölüm 4, "Google Trax, Google Translate ve Gemini ile Çeviri Görevlerinde İlerlemeler", çeviri görevlerini bir adım öteye taşıyacak ve Trax ile bir çeviri modeli oluşturacağız.

Python kodu bulunmamaktadır, bu nedenle açıklama yapılmamıştır. Çeviri birebir yapılmıştır.

---

