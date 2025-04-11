# Transformer Modelinin Çalışması

Transformer modeli otoregresif bir modeldir. Önceki çıktı dizilerini ek girdi olarak kullanır. Kodlayıcıdaki (encoder) çoklu baş dikkat katmanları (multi-head attention layers) aynı işlemi kullanır. Ancak, maskeli çoklu baş dikkat alt katmanı 1, dikkatin yalnızca mevcut konuma kadar olan pozisyonlara uygulanmasına izin verir. Gelecekteki kelimeler Transformer'dan gizlenir ve bu, onun tahmin etmeyi öğrenmeye zorlar.

## Decoder Katmanının Çalışması

Decoder katmanındaki çoklu baş dikkat katmanları, encoder ile aynı işlemi kullanır. Maskeli çoklu baş dikkat alt katmanı 1, yalnızca mevcut konuma kadar olan pozisyonlara dikkat uygulamasına izin verir. 

### Maskeli Çoklu Baş Dikkat Alt Katmanı 1

Maskeli çoklu baş dikkat alt katmanı 1'in ardından, encoder'da olduğu gibi bir post-layer normalizasyon işlemi uygulanır.

### Çoklu Baş Dikkat Alt Katmanı 2

Çoklu baş dikkat alt katmanı 2 de, Transformer'ın tahmin etmesi gereken diziyi görmemek için yalnızca mevcut konuma kadar olan pozisyonlara dikkat eder. Bu alt katman, dot-product dikkat işlemleri sırasında encoder (K, V) değerlerini dikkate alarak encoder'dan bilgi çeker. Ayrıca, dot-product dikkat işlemleri sırasında maskeli çoklu baş dikkat alt katmanı 1'in (maskeli dikkat) çıktısını (Q) dikkate alarak bu alt katmandan da bilgi çeker. Böylece decoder, encoder'ın eğitilmiş bilgisini kullanır.

Decoder'ın kendi dikkat çoklu baş alt katmanının girdisini şu şekilde tanımlayabiliriz:
```python
Input_Attention = (Output_decoder_sub_layer-1(Q), Output_encoder_layer(K, V))
```
Burada:
- `Output_decoder_sub_layer-1(Q)`: Decoder'ın bir önceki alt katmanının çıktısı (Q)
- `Output_encoder_layer(K, V)`: Encoder katmanının çıktısı (K, V)

Bu girdiler kullanılarak dot-product dikkat işlemi uygulanır.

### İşlem Sırası

1. Maskeli çoklu baş dikkat alt katmanı 1 uygulanır.
2. Post-layer normalizasyon işlemi uygulanır.
3. Çoklu baş dikkat alt katmanı 2 uygulanır.
4. Post-layer normalizasyon işlemi uygulanır.
5. FFN (Feed Forward Network) alt katmanı uygulanır.
6. Post-LN (Layer Normalization) uygulanır.
7. Linear layer uygulanır.

Transformer modeli bu şekilde çalışarak, girdi dizisini işler ve çıktı dizisini oluşturur.

---

