# Eğitim Döngüsü

Eğitim döngüsü standart öğrenme süreçlerini takip eder. Epoch sayısı 4 olarak ayarlanır ve kayıp ve doğruluk ölçümleri çizilir. Ardından, eğitim döngüsü dataloader'ı kullanarak toplu verileri yükler ve eğitir. Son olarak, eğitim süreci ölçülür ve değerlendirilir.

# Kod Açıklaması

Kod, kayıp ve doğruluğu depolayacak olan `train_loss_set`'i başlatarak başlar, bu değerler daha sonra çizilecektir. 
```python
t = []  # Kayıp ve doğruluğumuzu çizmek için saklayacağız
train_loss_set = []  # Eğitim epoch sayısı (yazarlar 2 ila 4 arasında öneriyor)
```
Eğitim epoch sayısını belirleyelim:
```python
epochs = 4
```
`trange`, normal python `range` fonksiyonunun tqdm ile sarılmış halidir. 
```python
for _ in trange(epochs, desc="Epoch"):
```
Bu döngü içinde, eğitim süreci gerçekleştirilir.

# Doğruluk Hesaplanması

Doğruluk hesaplanırken, `logits` ve `label_ids` kullanılarak `tmp_eval_accuracy` hesaplanır:
```python
tmp_eval_accuracy = flat_accuracy(logits, label_ids)
```
Ardından, `eval_accuracy` güncellenir ve `nb_eval_steps` artırılır:
```python
eval_accuracy += tmp_eval_accuracy
nb_eval_steps += 1
```
Son olarak, doğruluk değeri yazdırılır:
```python
print("Validation Accuracy: {}".format(eval_accuracy/nb_eval_steps))
```
# Çıktı

Çıktı, her bir epoch için trange wrapper ile birlikte bilgileri gösterir:
```
Epoch:   0%|          | 0/4 [00:00<?, ?it/s]
Train loss: 0.5381132976395461
Epoch:  25%|██▌       | 1/4 [07:54<23:43, 474.47s/it]
Validation Accuracy: 0.788966049382716
Train loss: 0.315329696132929
Epoch:  50%|█████     | 2/4 [15:49<15:49, 474.55s/it]
Validation Accuracy: 0.836033950617284
Train loss: 0.1474070605354314
Epoch:  75%|███████▌  | 3/4 [23:43<07:54, 474.53s/it]
Validation Accuracy: 0.814429012345679
Train loss: 0.07655430570461196
Epoch: 100%|██████████| 4/4 [31:38<00:00, 474.58s/it]
Validation Accuracy: 0.810570987654321
```
# Sonuç

Transformer modelleri hızla gelişiyor ve kullanımdan kaldırma mesajları ve hataları ortaya çıkabilir. Hugging Face de bunun istisnası değildir ve bu olduğunda kodumuzu buna göre güncellemeliyiz. Model eğitildi. Artık eğitim değerlendirmesini görüntüleyebiliriz.

---

