# Model Parametrelerinin İncelenmesi

Modelin parametrelerini incelemek, mimarisi hakkında ek bilgiler sağlayabilir. Model küçüktür ve 83504416 parametre içerir (bu sayı model güncellemeleriyle değişebilir). Boyutunu kontrol edebiliriz: `print(model.num_parameters())` Çıktı, yaklaşık parametre sayısını gösterir, bu sayı bir transformatör sürümünden diğerine değişebilir: 83504416

Şimdi parametrelere bakalım. Öncelikle parametreleri LP'ye depolarız ve liste uzunluğunu hesaplarız: 
```python
LP = list(model.parameters())
lp = len(LP)
print(lp)
```
Çıktı, yaklaşık 106 matris ve vektör olduğunu gösterir, bu sayı bir transformatör modelinden (veya güncellemeden) diğerine değişebilir: 106

Şimdi, bu 106 matris ve vektörü içeren tensörleri görüntüleyelim: 
```python
for p in range(0, lp):
    print(LP[p])
```
Çıktı, tüm parametreleri görüntüler, aşağıdaki çıktı alıntısında gösterildiği gibi:
```
Parameter containing:
tensor([[-0.0175, -0.0210, -0.0334,  ...,  0.0054, -0.0113,  0.0183],
        [ 0.0020, -0.0354, -0.0221,  ...,  0.0220, -0.0060, -0.0032],
        [ 0.0001, -0.0002,  0.0036,  ..., -0.0265, -0.0057, -0.0352],
        ...,
        [-0.0125, -0.0418,  0.0190,  ..., -0.0069,  0.0175, -0.0308],
        [ 0.0072, -0.0131,  0.0069,  ...,  0.0002, -0.0234,  0.0042],
        [ 0.0008,  0.0281,  0.0168,  ..., -0.0113, -0.0075,  0.0014]],
       requires_grad=True)
```
Transformatörlerin nasıl inşa edildiğini anlamak için parametrelere birkaç dakika göz atın. Parametre sayısı, modeldeki tüm parametrelerin toplanmasıyla hesaplanır, örneğin:
- Kelime hazinesi (52.000) x boyutlar (768)
- Vektörlerin boyutu, 1 x 768
- Bulunan diğer birçok boyut

Dikkate edin ki `d_model = 768`. Modelde 12 başlık vardır. Her başlık için `d_k` boyutunu bu şekilde hesaplarız: Bu, bir transformatörün yapı taşlarının optimize edilmiş LEGO ® kavramını bir kez daha gösterir.

Şimdi, bir modelin parametre sayısının nasıl hesaplandığını ve 83.504.416 rakamına nasıl ulaşıldığını göreceğiz. Aşağıdaki hücre, bu modeldeki 106 tensörün her birinin boyutunu görüntüler:
```python
# Her tensörün boyutu
LP = list(model.parameters())
for i, tensor in enumerate(LP):
    print(f"Shape of tensor {i}: {tensor.shape}")
```
Çıktı, tensör ve boyutunu görüntüler:
```
Shape of tensor 0: torch.Size([52000, 768])
Shape of tensor 1: torch.Size([514, 768])
Shape of tensor 2: torch.Size([1, 768])
Shape of tensor 3: torch.Size([768])
Shape of tensor 4: torch.Size([768])
Shape of tensor 5: torch.Size([768, 768])
Shape of tensor 6: torch.Size([768])
Shape of tensor 7: torch.Size([768, 768])
Shape of tensor 8: torch.Size([768])
Shape of tensor 9: torch.Size([768, 768])
Shape of tensor 10: torch.Size([768])
Shape of tensor 11: torch.Size([768, 768])
Shape of tensor 12: torch.Size([768])
Shape of tensor 13: torch.Size([768])
Shape of tensor 14: torch.Size([768])
Shape of tensor 15: torch.Size([3072, 768])
Shape of tensor 16: torch.Size([3072])…
```
Kullandığınız transformatör modülünün sürümüne bağlı olarak sayılar değişebilir.

Tensörlerin neyi temsil ettiğini geçici olarak tanımlayabiliriz, örneğin:
- `torch.Size([52000, 768])`: muhtemelen 52.000 kelime içeren embedding matrisi ve 768 boyutlu embedding.
- `torch.Size([514, 768])`: bu konumsal embeddingler olabilir. RoBERTa 512 token kabul eder, başlangıç ve bitiş tokenlarını ekleriz.
- `torch.Size([1, 768])`: bu `<cls>` gibi özel bir tokenin embeddingi olabilir.

Bir transformatör modelinin, öğreneceği dizilerin matematiksel temsili olduğunu görebilirsiniz.

Şimdi, her tensörün parametre sayısını sayacağız. Öncelikle, `np` adlı bir parametre sayacı başlatırız ve parametre listesindeki `lp` (106) sayıda öğeyi dolaşırız:
```python
# Parametreleri sayma
np = 0
for p in range(0, lp):
    # Tensör sayısı
```
Parametreler farklı boyutlardaki matrisler ve vektörlerdir, örneğin: 768 x 768, 768 x 1, 768

Bazı parametrelerin iki boyutlu, bazılarının bir boyutlu olduğunu görebiliriz. Bir parametrenin iki boyutu olup olmadığını görmek için kolay bir yol:
```python
PL2 = True
try:
    L2 = len(LP[p][0])  # 2D ise
except:
    L2 = 1  # 1D ise
    PL2 = False
```
Eğer parametre iki boyuta sahipse, ikinci boyutu `L2 > 0` ve `PL2 = True` (iki boyut = True) olur. Eğer parametre sadece bir boyuta sahipse, ikinci boyutu `L2 = 1` ve `PL2 = False` (iki boyut = False) olur.

`L1` parametrenin ilk boyutunun boyutu:
```python
L1 = len(LP[p])
L3 = L1 * L2
```
Şimdi, her döngü adımında parametreleri ekleyebiliriz:
```python
np += L3  # Tensör başına parametre sayısı
```
Parametrelerin toplamını elde edeceğiz, ancak bir transformatör modelinin parametre sayısının tam olarak nasıl hesaplandığını da görmek istiyoruz:
```python
if PL2 == True:
    print(p, L1, L2, L3)  # Parametre boyutlarını görüntüleme
if PL2 == False:
    print(p, L1, L3)  # Parametre boyutlarını görüntüleme
print(np)  # Toplam parametre sayısı
```
Çıktı, modeldeki tüm tensörler için parametre sayısının nasıl hesaplandığının listesi olur, aşağıdaki alıntıda gösterildiği gibi:
```
0 52000 768 39936000
1 514 768 394752
2 1 768 768
3 768 768
4 768 768
5 768 768 589824
6 768 768
7 768 768 589824
8 768 768
9 768 768 589824
10 768 768
11 768 768 589824
12 768 768
13 768 768
14 768 768
15 3072 768 2359296
16 3072 3072
17 768 3072 2359296
18 768 768
19 768 768
20 768 768
21 768 768 589824
22 768 768
23 768 768 589824
24 768 768
25 768 768 589824
…
94 768 768
95 3072 768 2359296
96 3072 3072
97 768 3072 2359296
98 768 768
99 768 768
100 768 768
101 52000 52000
102 768 768 589824
103 768 768
104 768 768
105 768 768
83504416
```
RoBERTa modelinin toplam parametre sayısı listenin sonunda görüntülenir: 83504416

Kullanılan kütüphanelerin sürümüne bağlı olarak parametre sayısı değişebilir.

Şimdi, bir transformatör modelindeki parametre sayısının neyi temsil ettiğini tam olarak biliyoruz. Birkaç dakika geri gidip konfigürasyon çıktısına, parametrelerin içeriğine ve boyutlarına bakın. Bu noktada, modelin yapı taşlarının kesin bir zihinsel temsilini elde etmiş olacaksınız.

Program şimdi veri setini inşa ediyor.

---

