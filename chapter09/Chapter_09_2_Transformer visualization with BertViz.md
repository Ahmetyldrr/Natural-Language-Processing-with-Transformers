# Jesse Vig'in Makalesinin Çevirisi

Jesse Vig'in makalesi "A Multiscale Visualization of Attention in the Transformer Model" (2019), transformer modellerinin etkinliğini kabul etmektedir. Ancak Jesse Vig, dikkat mekanizmasını çözmenin zor olduğunu açıklamaktadır. Makale, BertViz adlı bir görselleştirme aracının sürecini açıklamaktadır. BertViz, dikkat başlığı aktivitesini görselleştirebilmekte ve bir transformer modelinin davranışını yorumlayabilmektedir. BertViz ilk olarak BERT ve GPT modellerini görselleştirmek için tasarlanmıştır. Bu bölümde, bir BERT modelinin aktivitesini görselleştireceğiz.

Bazı araçlar, bir çıktının "neden"ini vurgulayan "yorumlanabilir" terimini kullanmaktadır. Diğerleri ise bir çıktının "nasıl" elde edildiğini açıklayan "açıklanabilir" terimini kullanmaktadır. Son olarak, bazıları bu terimleri gevşek bir şekilde kullanmaktadır çünkü "neden" bazen "nasıl açıklanır!" anlamına gelebilir. Bu bölümdeki araçların çoğunda olduğu gibi, biz de bu terimleri gevşek bir şekilde kullanacağız.

Şimdi BertViz'i kurup çalıştıralım.

Not: Bu çeviride herhangi bir python kodu bulunmamaktadır. Eğer bir kod snippet'i verilseydi, satır satır açıklamalar yapardım. Ancak burada sadece metin çevirisi yapılmıştır. 

Eğer BertViz kurulumu ve çalıştırılması ile ilgili python kodları verilseydi, örneğin:
```python
# BertViz kurulumu
!pip install bertviz

# BertViz'i import etme
import bertviz

# BertViz'i çalıştırma
bertviz.run()
```
Yukarıdaki kod snippet'i için satır satır açıklama şu şekilde olurdu:

1. `# BertViz kurulumu`: BertViz kütüphanesini kurmak için kullanılan başlıktır.
2. `!pip install bertviz`: BertViz kütüphanesini pip kullanarak kurar.
3. `# BertViz'i import etme`: BertViz kütüphanesini python script'ine import etmek için kullanılan başlıktır.
4. `import bertviz`: BertViz kütüphanesini import eder.
5. `# BertViz'i çalıştırma`: BertViz'i çalıştırmak için kullanılan başlıktır.
6. `bertviz.run()`: BertViz'i çalıştırır.

---

