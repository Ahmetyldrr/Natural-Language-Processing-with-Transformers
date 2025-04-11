# 6. Bölüm Özeti

Bu bölümde, Hugging Face tarafından sağlanan yapı taşlarını kullanarak sıfırdan KantaiBERT adlı RoBERTa benzeri bir model transformatörü oluşturduk. İlk olarak, Immanuel Kant'ın eserleriyle ilgili belirli bir konudaki özelleştirilmiş bir veri setini yükleyerek başladık. Hedefleriniz doğrultusunda, mevcut bir veri setini yükleyebilir veya kendi veri setinizi oluşturabilirsiniz. Özelleştirilmiş bir veri seti kullanmanın, bir transformatör modelinin nasıl düşündüğüne dair içgörüler sağladığını gördük. Ancak bu deneysel yaklaşımın sınırları vardır. Bir modeli eğitimsel amaçların ötesinde eğitmek için çok daha büyük bir veri seti gerekir.

## KantaiBERT Projesinin Uygulanması

KantaiBERT projesi, `kant.txt` veri seti üzerinde bir tokenizer eğitmek için kullanıldı. Eğitilen `merges.txt` ve `vocab.json` dosyaları kaydedildi. Önceden eğitilmiş dosyalarımızla bir tokenizer yeniden oluşturuldu. KantaiBERT, özelleştirilmiş veri setini oluşturdu ve geri yayılım için eğitim partilerini işlemek üzere bir veri toplayıcı tanımladı.

### Modelin Eğitimi ve Kaydedilmesi

Eğitici başlatıldı ve RoBERTa modelinin parametreleri ayrıntılı olarak incelendi. Model eğitildi ve kaydedildi. Modeli kaydettik ve bir sonraki dil modelleme görevi için yükledik. Hedef, Immanuel Kant'ın mantığını kullanarak maskeyi doldurmaktı.

## Üretken Yapay Zeka Müşteri Desteği Modelinin Eğitimi

Son olarak, X (eski adıyla Twitter) üzerinde bir Üretken Yapay Zeka müşteri desteği modeli önceden eğittik. Açık kaynaklı bir RoBERTa modeli ve ücretsiz bir veri seti kullandık. Bu prototip, gerektiğinde belirli alanlar için bağımsız sohbet ajanları oluşturabileceğimizi gösterdi.

## Gelecek Adımlar

Kapı şimdi sizin için deneyler yapmak üzere açık. Mevcut veya özelleştirilmiş veri setleri üzerinde deneyler yapabilir ve sonuçlarınızı görebilirsiniz. Modelinizi Hugging Face topluluğuyla paylaşabilirsiniz. Transformatörler veri odaklıdır. Bunu, transformatörleri kullanmanın yeni yollarını keşfetmek için kendi avantajınıza kullanabilirsiniz. Artık, önceden eğitilmeye veya ince ayar yapmaya gerek duymayan API'lerle hazır kullanımlık transformatör motorlarını nasıl çalıştıracağınızı öğrenmeye hazırsınız.

# 7. Bölüm: ChatGPT ile Üretken Yapay Zeka Devrimi

7. Bölüm, sizi insanüstü LLM'lerin dünyasına götürecektir. Ve bu bölümün ve önceki bölümlerin bilgisiyle, hazır olacaksınız!

Python kodları bulunmamaktadır, ancak yukarıdaki metin içerisinde bazı teknik terimlerin açıklamaları aşağıda verilmiştir:

- **Tokenization**: Metni token adı verilen alt birimlere ayırma işlemidir.
- **RoBERTa**: Bir tür transformatör modelidir.
- **Hugging Face**: Transformatör modelleri için popüler bir kütüphane ve topluluktur.
- **veri toplayıcı (data collator)**: Eğitim verilerini modele uygun bir biçimde hazırlayan fonksiyondur.
- **geri yayılım (backpropagation)**: Modelin eğitimi sırasında kullanılan bir algoritmadır.
- **LLM (Large Language Model)**: Büyük dil modeli, çok büyük miktarda veri ile eğitilen dil modelleridir.

---

