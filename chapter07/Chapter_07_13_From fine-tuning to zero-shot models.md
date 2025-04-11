# GPT Modellerinin Arkasındaki Motivasyonlar

Başlangıçtan itibaren, Radford ve ekibi (2018) tarafından liderlik edilen OpenAI'ın araştırma takımları, önceden eğitilmiş modellerden GPT modellerine geçmek istediler. Hedef, dönüştürücüleri etiketlenmemiş veriler üzerinde eğitmekti. Dikkat katmanlarının denetimsiz verilerden bir dil öğrenmesine izin vermek akıllıca bir hareketti. Dönüştürücüleri belirli NLP görevleri yapmaya öğretmek yerine, OpenAI dönüştürücüleri bir dil öğrenmeye eğitmiştir. 
Not: Denetimsiz terimi, etiket olmadan yapılan eğitimi tanımlar. Bu anlamda, GPT modelleri denetimsiz eğitimden geçer. Ancak, eğitim sırasında bir token tahmin ettiğinde, çıktı, gerçek girdi dizisiyle karşılaştırılarak kayıp hesaplanır, gradyanlar bulunur ve geri yayılım yapılır. Bu anlamda, GPT tamamen denetimsiz olmaktan ziyade daha çok kendi kendini denetler. Üretken modellere bağlı olarak denetimsiz terimini gördüğünüzde bunu aklınızda tutun. 
OpenAI, görevden bağımsız bir model oluşturmak istedi. Bu nedenle, uzmanlar tarafından etiketlenmiş verilere güvenmek yerine, ham veriler üzerinde dönüştürücü modelleri eğitmeye başladılar. Verileri etiketlemek zaman alıcıdır ve dönüştürücünün eğitim sürecini önemli ölçüde yavaşlatır. 
İlk adım, bir dönüştürücü modelinde denetimsiz eğitimle başlamaktı. Ardından, modelin denetimli öğrenimini yalnızca ince ayar yapacaklardı. 
OpenAI, yalnızca kod çözücü içeren bir dönüştürücü seçti; bu, "Kod Çözücü Katmanlarını Yığma" bölümünde açıklanacaktır. Sonuçların ölçütleri inandırıcıydı ve kısa sürede diğer NLP araştırma laboratuvarlarının en iyi NLP modellerinin seviyesine ulaştı. 
GPT dönüştürücü modellerinin ilk sürümünün umut verici sonuçları, Radford ve ekibi (2019) tarafından sıfır-atış transfer modellerinin ortaya çıkmasına kısa sürede yol açtı. 
Felsefelerinin özü, GPT modellerini ham metinden öğrenmeye devam ettirmekti. Daha sonra, denetimsiz dağılımların örnekleri aracılığıyla dil modellemeye odaklanarak araştırmalarını bir adım öteye taşıdılar. 
Hedef, eğitilmiş GPT modeli yoğun bir eğitimle bir dili anladıktan sonra bu kavramı herhangi bir aşağı akış görevine genelleştirmekti. 
GPT modelleri hızla 117M parametreden 345M parametreye, diğer boyutlara ve ardından 1,542M parametreye evrildi. 
1,000,000,000+ parametreli dönüştürücüler doğdu. İnce ayar miktarı keskin bir şekilde azaltıldı. 
Bu, OpenAI'ı daha da ileri gitmeye teşvik etti. 
Brown ve ekibi (2020), koşullu olasılık dönüştürücü modellerinin derinlemesine eğitilebileceği varsayımıyla yola devam etti ve aşağı akış görevleri için çok az ince ayar yaparak veya hiç yapmadan mükemmel sonuçlar üretebildiler. 
OpenAI, bir model eğitme ve aşağı akış görevlerini doğrudan daha fazla ince ayar yapmadan çalıştırma hedefine ulaşıyordu. 
Bu olağanüstü ilerleme dört aşamada tanımlanabilir:

## İnce Ayar (Fine-Tuning, FT)
Önceki bölümlerde incelediğimiz anlamda gerçekleştirilmesi amaçlanmıştır. 
Bir dönüştürücü modeli eğitilir ve ardından aşağı akış görevlerinde ince ayar yapılır. 
Radford ve ekibi (2018), birçok ince ayar görevi tasarladı. 
OpenAI ekibi daha sonra aşağıdaki adımlarda görev sayısını kademeli olarak 0'a indirdi.

## Az Atış (Few-Shot, FS)
Büyük bir ilerlemeyi temsil eder. 
GPT eğitilir. Model, çıkarım yapması gerektiğinde, koşullandırma olarak gerçekleştirilecek görevin örnekleri sunulur. 
Koşullandırma, GPT ekibinin işlemden hariç tuttuğu ağırlık güncellemesinin yerini alır. 
Bu bölümde inceleyeceğimiz not defterlerinde metin tamamlama elde etmek için modele sağladığımız içerik aracılığıyla koşullandırma uygulayacağız.

## Bir Atış (One-Shot, 1S)
Süreci daha da ileri taşır. 
Eğitilen GPT modeli, gerçekleştirilecek aşağı akış görevinin yalnızca bir örneğiyle sunulur. 
Ağırlık güncelleme de izin verilmez.

## Sıfır Atış (Zero-Shot, ZS)
En son hedeftir. 
Eğitilen GPT modeli, gerçekleştirilecek aşağı akış görevinin hiçbir örneği sunulmaz. 
Bu yaklaşımların her birinin çeşitli verimlilik düzeyleri vardır. 
OpenAI GPT ekibi, bu son teknoloji dönüştürücü modelleri üretmek için çok çalıştı. 
Artık GPT modellerinin mimarisine yol açan motivasyonları açıklayabiliriz:
- Dönüştürücü modellerine kapsamlı bir eğitimle bir dil öğrenmeyi öğretmek.
- Bağlam koşullandırması yoluyla dil modellemeye odaklanmak. 
Dönüştürücü, bağlamı alır ve yenilikçi bir şekilde metin tamamlama üretir. 
Aşağı akış görevlerini öğrenmek için kaynak tüketmek yerine, hangi görev olursa olsun girdiyi anlamaya ve çıkarım yapmaya çalışır.
- Girdi dizilerinin bölümlerini maskelemek suretiyle modelleri eğitmenin verimli yollarını bulmak, dönüştürücüyü makine zekası ile düşünmeye zorlar. 
Böylece, makine zekası, insanca olmasa da verimlidir. 
GPT modellerinin mimarisine yol açan motivasyonları anlıyoruz. Şimdi yalnızca kod çözücü katmanlı GPT modeline bakalım.

Python kodları bulunmamaktadır, ancak metinde geçen bazı kavramlar python kodları ile örneklendirilebilir. Örneğin, GPT modellerinin eğitiminde kullanılan "maskeleme" işlemi aşağıdaki gibi python kodu ile gösterilebilir:
```python
import torch

# Girdi dizisi
input_sequence = torch.tensor([1, 2, 3, 4, 5])

# Maskeleme işlemi
masked_input_sequence = input_sequence.clone()
masked_input_sequence[torch.rand_like(input_sequence) < 0.2] = 0  # %20 olasılıkla maskeleme

print(masked_input_sequence)
```
Bu kod, girdi dizisinin bazı elemanlarını %20 olasılıkla maskeler. Gerçek GPT modellerinde bu maskeleme işlemi daha karmaşık şekillerde uygulanır.

---

