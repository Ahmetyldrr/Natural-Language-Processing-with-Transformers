# Winograd Şeması Sorununu Çözme

Bu bölümün Winograd Şeması Zorluğu (WSC) kısmında Winograd şemalarını tanımladık. Eğitim seti İngilizce idi. Peki ya bir transformer modelinden İngilizce-Fransızca çeviride bir zamir cinsiyet sorununu çözmesini istersek? Fransızca, dilbilgisel cinsiyetleri (dişil ve eril) olan isimler için farklı yazımlar içerir. Aşağıdaki cümlede, "car" veya "garage" kelimelerine atıfta bulunabilen "it" zamirini içermektedir. Bir transformer bu zamiri belirsizlikten kurtarabilir mi?

## Transformer Kodunu Çalıştırma

Open `Transformer_tasks.ipynb` dosyasını açın, `#Winograd` hücresine gidin ve örneğimizi çalıştırın:
```python
from transformers import pipeline
translator = pipeline("translation_en_to_fr", model="t5-base")
print(translator("The car could not go in the garage because it was too big.", max_length=40))
```
Çeviri kabul edilebilir:
```python
[{'translation_text': "La voiture ne pouvait pas aller dans le garage parce qu'elle était trop grosse."}]
```
Transformer, "it" kelimesinin "car" kelimesine atıfta bulunduğunu tespit etti, bu da dişil bir formdur. Dişil form, "it" ve "big" sıfatına uygulanır. "elle" Fransızca'da "she" anlamına gelir, bu da "it" çevirisinin dişil formudur. Eril form "il" olurdu, bu da "he" anlamına gelir. "grosse" ise "big" kelimesinin çevirisinin dişil formudur. Aksi takdirde, eril form "gros" olurdu.

## Sonuç

Transformer'a zor bir Winograd şeması verdik ve doğru cevabı üretti. Daha birçok veri seti güdümlü NLU görevi mevcuttur. Bu kitapta, transformer araç kutumuza daha fazla yapı taşı eklemek için bazılarını keşfedeceğiz.

---

