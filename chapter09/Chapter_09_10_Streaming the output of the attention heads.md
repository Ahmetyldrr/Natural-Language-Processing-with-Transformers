# Dikkat Çıktılarını Görselleştirme

Artık dikkat çıktılarını aldığımıza göre, modelin 12 katmanının ve 12 kafasının her birinin içeriğini çıkarabiliriz:

```python
# Her bir katman ve kafa için dikkat aktivitesini görselleştirme
for layer, attention in enumerate(attentions):
    print(f"Katman {layer+1}:")
    for head, head_attention in enumerate(attention[0]):
        print(f"Kafa {head+1}:")
        for source_token, target_tokens in enumerate(head_attention[:len(tokens)]):
            print(f"Kaynak token '{tokens[source_token]}' (index {source_token+1}):")
            for target_token, attention_value in enumerate(target_tokens[:len(tokens)]):
                print(f"Target token '{tokens[target_token]}' (index {target_token+1}): {attention_value}")
```

Program çıktıyı aşağıdaki alıntılarda gösterildiği gibi görüntüler:
Katman 4:
Kafa 1:
Kaynak token 'the' (index 1):
Target token 'the' (index 1): 0.35965585708618164
Target token 'output' (index 2): 0.016658220440149307
Target token 'shows' (index 3): 0.0013477668398991227
Target token 'the' (index 4): 0.002952627604827285
Target token 'attention' (index 5): 0.015658415853977203
Target token 'values' (index 6): 0.0007451129495166242
Kaynak token 'output' (index 2):
Target token 'the' (index 1): 0.12423665076494217
Target token 'output' (index 2): 0.1629541665315628
Target token 'shows' (index 3): 0.003638952737674117
Target token 'the' (index 4): 0.0013890396803617477
Target token 'attention' (index 5): 0.46722540259361267
Target token 'values' (index 6): 0.0005048955790698528
… 

Çıktı incelemek için ilginçtir. Bir sonraki hücreye geçmeden önce çıktının her bir öğesini incelemek için biraz zaman ayırın:

- **Katman**: Analiz edilen katman numarası (0'dan n'ye kadar).
- **Kafa**: Bir katmandaki kafa numarası (0'dan n'ye kadar).
- **Kaynak token**: Dikkat değerlerinin hesaplandığı token. Token her bir kelime veya alt kelimedir.
- **Target token**: Kaynak token'ın dikkat uyguladığı token.
- **Index**: Giriş sırasındaki 0'dan n'ye kadar olan pozisyon.

Görüntülenen değerler, Bölüm 2'de açıklandığı gibi bir dikkat kafasının mimarisine dayanan dikkat değerleridir. Gerekirse bölümü gözden geçirin. Değerler, Bölüm 2'de incelediğimiz çıktının sürecini temsil eder: Ancak, dikkat kafasının çıktısını V'yi uygulamadan önce çıkardık. 

Bu durumda, softmax fonksiyonu kullanışlıdır çünkü şimdi dikkat skorları 1'e toplanır, böylece %100'e ulaşır. Böylece kaynak token'ın her bir hedef fonksiyona ne kadar dikkat ettiği görülebilir. Skor ne kadar yüksekse, ilişki o kadar güçlüdür.

Bu durumda, 12 katmanımız var, her biri 12 kafa içerir. Giriş embeddinginin boyutu 768'dir. 12 kafa olduğu için, ölçeklendirme parametresi d_k = 768/12 = 64'tür. Bu açıklama not defterinin Ek Bilgiler bölümünde bulunabilir.

İnterpretasyon fonksiyonuna V'yi dahil etmedik çünkü eğer V uygulanırsa, çıktının analizini zorlaştıracaktı. Ayrıca, ek işlemler eklemek ilk değerleri bulanıklaştırır. Kafaların stokastik değerlerini nasıl ürettiğini görmek için akışa gelen değerlere bir göz atın.

Şimdi, kelimeler arasındaki ilişkileri netleştirmek için bir skor matrisi arayüzü oluşturacağız.

---

