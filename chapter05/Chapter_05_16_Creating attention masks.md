# İşlemin Zorlu Kısımları Başlıyor

Şimdi sürecin zor bir kısmı geliyor. Dizileri önceki hücrede doldurduk. Ancak modelin bu doldurulmuş tokenlere dikkat etmesini önlemek istiyoruz! Fikir, her bir token için 1 değerine sahip bir maske uygulamak, ardından doldurma için 0'lar gelecek: 
attention_masks = [] # Her bir token için 1'lerden oluşan, ardından doldurma için 0'lardan oluşan bir maske oluşturun
for seq in input_ids:
  seq_mask = [float(i>0) for i in seq]
  attention_masks.append(seq_mask)

Şimdi kodun satır satır açıklaması:

1. `attention_masks = []` : `attention_masks` adında boş bir liste oluşturur. Bu liste, daha sonra oluşturulacak olan maskeleri saklamak için kullanılacaktır.

2. `for seq in input_ids:` : `input_ids` listesindeki her bir dizi (`seq`) için döngüyü başlatır.

3. `seq_mask = [float(i>0) for i in seq]` : Bu satır, listedeki her bir elemanı (`i`) kontrol eder ve eğer eleman 0'dan büyükse (`i>0`), 1'e (float olarak 1.0) çevirir, aksi takdirde 0'a (float olarak 0.0) çevirir. 
   - `for i in seq` : `seq` listesindeki her bir elemanı sırasıyla `i` değişkenine atar.
   - `float(i>0)` : `i>0` ifadesi bir boolean değer döndürür (True veya False). `float()` fonksiyonu bu boolean değeri float tipine çevirir (True için 1.0, False için 0.0).

4. `attention_masks.append(seq_mask)` : Oluşturulan `seq_mask` listesini `attention_masks` listesine ekler.

Bu işlemden sonra, program verileri bölecektir. 

Python kodu olarak verilen kısım şu şekildedir:
```python
attention_masks = [] 
for seq in input_ids:
  seq_mask = [float(i>0) for i in seq]
  attention_masks.append(seq_mask)
```

---

