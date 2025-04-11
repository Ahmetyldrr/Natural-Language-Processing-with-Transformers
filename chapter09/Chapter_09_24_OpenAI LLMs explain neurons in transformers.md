# Büyük Dil Modelleri ve Nöron Açıklamaları

GPT-4 gibi Büyük Dil Modelleri, dil modellerindeki nöronları açıklayabilir. OpenAI, sezgisel bir arayüz oluşturdu ve Mayıs 2023'te halka açık hale getirdi. Yapay zeka tarihinin çok kısa bir sürede başka bir seviyeye gittiğini görüyoruz. Büyük Dil Modellerinin (LLM) ilk nesli, diğer alanlara da genişleyebilecek üstel bir ilerlemeye yol açacaktır. Yeni bir dönemin tarihöncesindeyiz!

Aşağıdaki bağlantıya tıklayarak açıklayıcıyı çalıştırabilirsiniz: https://openaipublic.blob.core.windows.net/neuron-explainer/neuron-viewer/index.html . Gösterilen örnek için bir nöron seçmeniz istenecektir: 
## Şekil 9.22: Nöron Seçme
Bir nöron seçin ve + nörona gidin. İlk nöron, 0. katmanda, 0 indeksinde bulunuyor. Bu durumda, ME tokeni bir açıklama ile birlikte görünür: 
## Şekil 9.23: ME Kelimesi için Açıklama
Daha iyi bir açıklama önerip puanlama detaylarını görmek için GPT-4 kullanarak nöronun puanlama detaylarını vurgulayarak açıklayabiliriz, gerçek aktivasyonların aşağıdaki alıntısında gösterildiği gibi: 
## Şekil 9.24: Puanlama Detayları
GPT-4 tarafından önerilen açıklamaları görmek için Aktivasyonlar'a tıklayarak içgörüler elde edebiliriz: 
## Şekil 9.25: GPT-4 İçgörüler
GPT-4 nesilleri uygulandığında, sistem en yüksek aktivasyonların üst kuantil aralığını seçer. Sayfanın altında, ilgili tokenleri bulabilirsiniz: 
## Şekil 9.26: İlgili Tokenler
Son olarak, ilgili nöronları görebiliriz: 
## Şekil 9.27: İlgili Nöronlar
Arayüz henüz ilk aşamalarında. Bununla birlikte, bir LLM'yi GPT-4 ile açıklamak oldukça ileriye doğru atılmış bir adım. Bu arayüzdeki nöronları keşfetmek, bir transformatörün aktivitesini nöron seviyesinde görselleştirmeye yardımcı olacaktır.

# Özet
Açıklamalar, GPT-4 ile gerçek ve simüle edilmiş aktivasyonları karşılaştırarak elde edilir. Bu araştırma, transformatör modellerinin kara kutusunu bir kez daha parçaladı. Arayüzün netliğini ve açıklamaların kalitesini geliştirmek için uzun bir yol var. Ancak ilk adım atıldı! Bu yaklaşımın evrimi, transformatör yorumlama sorunlarının büyük bir kısmını çözebilir. İleride insan kontrolünün neden gerekli olduğunu göstereceğiz.

Paragrafta Python kodları bulunmamaktadır. Sadece metin ve bazı şekil referansları içermektedir. Eğer kod içeriyor olsaydı, satır satır açıklama verebilirdim.

---

