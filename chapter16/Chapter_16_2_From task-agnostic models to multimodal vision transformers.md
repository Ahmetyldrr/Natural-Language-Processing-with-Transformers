# Temel Modeller (Foundation Models)

1. Bölümde gördüğümüz gibi, Temel Modellerin iki farklı ve benzersiz özelliği vardır: 

## Ortaya Çıkma (Emergence)
 Transformer modelleri, Temel Model olarak nitelendirilen büyük modellerdir ve süper bilgisayarlarda eğitilirler. Diğer birçok model gibi belirli görevleri öğrenmek üzere eğitilmezler. Temel Modeller, dizileri anlamayı öğrenirler.

## Homojenleştirme (Homogenization)
 Aynı model, aynı temel mimariyle birçok alanda kullanılabilir. Temel Modeller, diğer modellerden daha hızlı ve daha iyi bir şekilde veri yoluyla yeni beceriler öğrenebilirler.

OpenAI ChatGPT modelleri (GPT 3 ve GPT 4), Google PaLM ve Google BERT (sadece Google tarafından eğitilen BERT modelleri) görevden bağımsız Temel Modellerdir. Bu görevden bağımsız modeller doğrudan ViT, CLIP ve DALL-E modellerine yol açar. Transformer modellerinin soyutlama düzeyi, multimodal nöronlara yol açar. Multimodal nöronlar, pikseller veya görüntü yamaları olarak tokenize edilebilen görüntüleri işleyebilir. Daha sonra, bu görüntüler görsel transformerlarda kelimeler olarak işlenebilir. Bir görüntü kodlandıktan sonra, transformer modelleri tokenleri herhangi bir kelime tokeni olarak görür, Şekil 16.1'de gösterildiği gibi:

# Şekil 16.1: Görüntüler kelime benzeri tokenlere kodlanabilir

Bu bölümde aşağıdaki konuları ele alacağız:
- **ViT**: Görüntüleri kelime yamaları olarak işleyen görsel transformerlar.
- **CLIP**: Metin ve görüntüleri kodlayan görsel transformerlar.
- **DALL-E**: Metinle görüntüler oluşturan görsel transformerlar.

İlk olarak, görüntüleri kelime yamaları olarak işleyen bir görsel transformer olan ViT'yi keşfederek başlayalım.

Bu çeviride herhangi bir python kodu bulunmamaktadır. Eğer bir kod örneği verseniz, satır satır açıklama yapabilirim.

---

