# Bu Kitapta Keşfedeceklerimiz
Bu kitapta, çeşitli kütüphaneleri keşfedeceğiz. Örneğin, Google dünyadaki en gelişmiş yapay zeka kaynaklarından bazılarına sahiptir. Google Trax, Google Colab'da birkaç satır kod ile kurulabilir. Ücretsiz veya ücretli hizmetler arasından seçim yapabiliriz. Kaynak koduna erişebilir, modelleri değiştirebilir ve hatta bunları kendi sunucularımızda veya Google Cloud'da eğitebiliriz. Örneğin, çeviri görevleri için bir transformer modelini özelleştirmek, kullanıma hazır API'lere göre bir adım geridir. Ancak, bazı durumlarda hem eğitici hem de etkili olabilir. Google'ın çevirilerdeki son gelişmelerini keşfedecek ve Google Trax'ı 4. Bölüm'de, Google Trax, Google Translate ve Google Bard ile Çevirilerdeki Gelişmeler başlığı altında uygulayacağız.

# API'ler ve Kütüphaneler
API'lerin, OpenAI gibi, sınırlı geliştirici becerileri gerektirdiğini ve Google Trax gibi kütüphanelerin biraz daha derine, kodlara indiğini gördük. Her iki yaklaşım da, AI API'lerinin API'nin editör tarafında daha fazla geliştirme gerektireceğini, ancak transformerları uygularken çok daha az çaba gerektireceğini gösteriyor. Google Translate, transformer kullanan en ünlü çevrimiçi uygulamalardan biridir. Google Translate, çevrimiçi olarak veya bir API aracılığıyla kullanılabilir.

# Google Translate ile Çeviri
İngilizce'den Fransızca'ya coreference resolution gerektiren bir cümleyi Google Translate ile çevirmeyi deneyin. Cümle şudur: "A user visited the AllenNLP website, tried a transformer model, and found it interesting." Google Translate aşağıdaki çeviriyi üretir: 
Figure 1.7: Google Translate kullanarak bir çeviride coreference resolution 
Google Translate, coreference resolution'ı çözmüş gibi görünüyor, ancak Fransızca'da "transformateur" kelimesi elektronik bir cihaz anlamına geliyor. "Transformer" kelimesi Fransızca'da bir neolojizmdir (yeni kelime). Belirli bir proje için bir AI uzmanının dil ve dilbilim becerilerine sahip olması gerekebilir. Bu durumda önemli bir geliştirme gerekmeyebilir. Ancak, proje, bir çeviri istemeden önce girdiyi netleştirmeyi gerektirebilir.

# Dilbilim ve Geliştirme
Bu örnek, bir girdi bağlamı üzerinde çalışmak için bir dilbilimci ile takım kurmanız veya dilbilim becerileri edinmeniz gerekebileceğini gösteriyor. Ayrıca, bağlamlar için bir arayüz ile girdiyi geliştirmek için çok fazla geliştirme gerekebilir. Google, kitabın yayınlandığı zamana kadar bu örneği geliştirebilir, ancak sistemde binlerce daha fazla sınırlama var. Yani, Google Translate'i kullanmak için hala scriptler eklememiz gerekebilir. Veya, BERT, T5 veya bu kitapta daha sonra keşfedeceğimiz diğer modeller gibi belirli bir çeviri ihtiyacı için bir transformer model bulmamız gerekebilir. Bir API seçmek bir görevdir. Uygun bir transformer model bulmak başka bir görevdir ve artan çözüm yelpazesi ile kolay değildir.

Python kodları bulunmamaktadır, ancak Google Colab'da Google Trax kurulumu aşağıdaki gibi olabilir:
```python
# Google Trax kurulumu
!pip install trax
```
veya 
```python
# Google Colab'da Google Trax kurulumu
!pip install -q -U trax
import trax
```

---

