# Hazır Veri Kümeleri ve Transformer Eğitimi

Hazır veri kümeleri, transformer modellerini eğitmek ve karşılaştırmak için nesnel bir yol sağlar. Bu bölüm, sonuç elde etmek için saatlerce beklemeden, gerçek zamanlı olarak çalıştırılabilen not defteri hücreleri ile bir transformer'ın eğitim sürecini anlamayı amaçlamaktadır. Aydınlanma Çağı'nın doruk noktası olan Alman filozof Immanuel Kant'ın (1724–1804) eserlerini kullanmayı seçtim. İnsan benzeri mantık ve önceden eğitilmiş akıl yürütmeyi, aşağı akış akıl yürütme görevleri için tanıtmak fikri benimsenmiştir. Project Gutenberg (https://www.gutenberg.org), metin formatında indirilebilen çok çeşitli ücretsiz e-Kitaplar sunar. Kendi kitaplarınıza dayalı özel veri kümeleri oluşturmak istiyorsanız diğer kitapları kullanabilirsiniz.

Immanuel Kant'ın aşağıdaki üç kitabını **kant.txt** adında bir metin dosyasına derledim:
- Saf Aklın Eleştirisi
- Pratik Aklın Eleştirisi
- Ahlak Metafiziğinin Temel İlkeleri

**kant.txt**, bu bölümün transformer modelini eğitmek için küçük bir eğitim veri kümesi sağlar. Elde edilen sonuç deneyseldir. Gerçek bir proje için Immanuel Kant, Rene Descartes, Pascal ve Leibnitz'in tüm eserlerini eklerdim. Metin dosyası, kitapların ham metnini içerir: 
“…Zira bu tür araştırmalara karşı _kayitsizlik_ göstermek gerçekte boşunadır, çünkü bunların nesnesi insanlık için kayıtsız kalamaz.”

Veri kümesi, KantaiBERT.ipynb not defterinin ilk hücresinde GitHub'dan otomatik olarak indirilir. Ayrıca, bu bölümün GitHub'daki dizininde bulunan **kant.txt**'yi Colab'ın dosya yöneticisini kullanarak yükleyebilirsiniz. Bu durumda, dosyayı GitHub'dan almak için curl kullanılır:

### Kant.txt Dosyasını İndirme

```python
#1. kant.txt'yi Colab dosya yöneticisini kullanarak yükleyin
#2. Dosyayı GitHub'dan indirin
!curl -L https://raw.githubusercontent.com/Denis2054/Transformers-for-NLP-and-Computer-Vision-3rd-Edition/master/Chapter06/kant.txt --output "kant.txt"
```

Yükledikten veya indirdikten sonra Colab dosya yöneticisi panelinde görünür:

# Şekil 6.1: Colab Dosya Yöneticisi

Google Colab'ın dosyaları sanal makineyi (VM) yeniden başlattığınızda sildiğini unutmayın. Veri kümesi tanımlanmış ve yüklenmiştir. **kant.txt** olmadan sonraki hücreleri çalıştırmayın. Eğitim verileri bir önkoşuldur.

Şimdi, program Hugging Face transformer'ları kuracaktır.

### Kod Açıklaması

Verilen kod snippet'i, **kant.txt** dosyasını GitHub'dan indirmek için `curl` komutunu kullanır. 
```bash
!curl -L https://raw.githubusercontent.com/Denis2054/Transformers-for-NLP-and-Computer-Vision-3rd-Edition/master/Chapter06/kant.txt --output "kant.txt"
```
- `!curl`: Colab'da bir terminal komutu olan `curl`'ü çalıştırmak için kullanılır.
- `-L`: Yönlendirmeleri takip etmek için kullanılır. Eğer belirtilen URL yönlendirilmişse, `-L` seçeneği `curl`'ün son hedefine ulaşana kadar yönlendirmeleri takip etmesini sağlar.
- `https://raw.githubusercontent.com/Denis2054/Transformers-for-NLP-and-Computer-Vision-3rd-Edition/master/Chapter06/kant.txt`: İndirilecek dosyanın URL'si.
- `--output "kant.txt"`: İndirilen dosyanın kaydedileceği dosya adı ve yolu. Bu örnekte, dosya mevcut çalışma dizinine "kant.txt" olarak kaydedilir.

---

