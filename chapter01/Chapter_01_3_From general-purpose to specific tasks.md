# Transformer ile Sürüklenen Yapay Zeka Çalışma Şeklimizi Nasıl Değiştiriyor?

Bu bölüm, transformer ile sürüklenen yapay zekanın çalışma şeklimizi nasıl sonsuza kadar değiştirdiğini gösteriyor. ChatGPT, bir sınıflandırma programını otomatik olarak tasarlayacak, yazacak ve açıklayacaktır. Bu bölümde, ChatGPT'den gerçekleştirmesini isteyeceğimiz görevde ayrımcı, üretken, göreve özgü ve genel amaçlı özellikler bulacaksınız. Yanılmayın! Transformer ile sürüklenen yapay zeka henüz ilk aşamalarında. Modeller evrimleştikçe ve yeni olanlar ortaya çıktıkça, yapay zeka giderek daha karmaşık görevleri yerine getirebilecek.

## ChatGPT ile Sınıflandırma Algoritması Yazma ve Açıklama

İlk olarak ChatGPT'nin kendi başına bir sınıflandırma algoritması yazmasını ve açıklamalarını izleyeceğiz! Bu bölümün GitHub deposunda bulunan `ChatGPT_Plus_writes_and_explains_AI.ipynb` dosyasını açın. ChatGPT Plus'a iki istek gönderildi: 
- Iris için matplotlib grafiği içeren bir sklearn sınıflandırması sağlayın ve OpenAI API'lerini kullanmayın.
- Bu kod için Python'da yeni başlayanlar için ayrıntılı bir açıklama yazın.

ChatGPT, özellikle GPT-3.5-turbo, bu tüm not defterini, açıklamalarıyla birlikte yazdı! Tek insan müdahalesi, not defterini oluşturmak ve ChatGPT tarafından sağlanan metin ve kodu kopyalamaktı.

### Programın Açıklaması

ChatGPT, programı açıklayarak başlıyor: 
Bu program, Scikit-learn'ün popüler bir makine öğrenimi kitaplığını kullanarak Iris veri kümesi için bir karar ağacı sınıflandırıcısı oluşturmayı gösteren basit bir makine öğrenimi projesidir. Iris veri kümesi, makine öğrenimi topluluğunda ünlü bir veri kümesidir ve genellikle sınıflandırma algoritmaları için bir ölçüt olarak kullanılır.

Bu programda, önce Iris veri kümesini yükleyecek ve eğitim ve test kümelerine ayıracaksınız. Ardından, Scikit-learn'ün DecisionTreeClassifier sınıfını kullanarak bir karar ağacı sınıflandırıcı modeli oluşturacak ve eğitim verileri üzerinde eğiteceksiniz. Sonra, modelin doğruluğunu test kümesi üzerinde değerlendirecek ve modelin performansını özetleyen bir tablo olan karışıklık matrisini hesaplayacaksınız. Son olarak, karışıklık matrisini Matplotlib kullanarak çizeceksiniz.

### Kodun Adım Adım Açıklaması

#### 1. Gerekli Kütüphanelerin İthali

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split
from sklearn.tree import DecisionTreeClassifier
from sklearn.metrics import confusion_matrix
from sklearn.tree import plot_tree
```

Bu kod, veri manipülasyonu için NumPy ve Pandas, veri görselleştirme için Matplotlib ve makine öğrenimi için Scikit-learn kütüphanelerini içe aktarır.

#### 2. Iris Veri Kümesinin Yüklenmesi

```python
iris = load_iris()
```

Bu kod, Scikit-learn'ün datasets modülünden Iris veri kümesini `iris` adlı bir değişkene yükler.

#### 3. Veri Kümesinin Eğitim ve Test Kümelerine Ayrılması

```python
X_train, X_test, y_train, y_test = train_test_split(iris.data, iris.target, test_size=0.2, random_state=42)
```

Bu kod, veri kümesini eğitim ve test kümelerine ayırır. `test_size=0.2` parametresi, verilerin %20'sinin test için, %80'inin eğitim için kullanılacağını belirtir.

#### 4. Karar Ağacı Sınıflandırıcı Modelinin Eğitilmesi

```python
model = DecisionTreeClassifier(random_state=42)
model.fit(X_train, y_train)
```

Bu kod, Scikit-learn'ün DecisionTreeClassifier sınıfını kullanarak bir karar ağacı sınıflandırıcı modeli oluşturur ve `X_train` ve `y_train` üzerinde eğitir.

#### 5. Modelin Değerlendirilmesi

```python
score = model.score(X_test, y_test)
print(f"Accuracy: {score:.2f}")
```

Bu kod, eğitilmiş modelin `X_test` ve `y_test` üzerindeki doğruluğunu değerlendirir ve sonucu yazdırır.

#### 6. Karışıklık Matrisinin Hesaplanması ve Çizilmesi

```python
y_pred = model.predict(X_test)
cm = confusion_matrix(y_test, y_pred)

fig, ax = plt.subplots()
im = ax.imshow(cm, interpolation="nearest", cmap=plt.cm.Blues)
ax.figure.colorbar(im, ax=ax)
# ... (diğer kodlar)
```

Bu kod, modelin `X_test` üzerindeki tahminlerini kullanarak karışıklık matrisini hesaplar ve Matplotlib ile çizer.

#### 7. Karar Ağacının Çizilmesi

```python
plt.figure(figsize=(20, 10))
plot_tree(model, feature_names=iris.feature_names, class_names=iris.target_names, filled=True)
plt.show()
```

Bu kod, eğitilmiş karar ağacını Scikit-learn'ün `plot_tree` fonksiyonu ile çizer.

Bu bölümde, ChatGPT'nin bir sınıflandırma programını otomatik olarak nasıl tasarlayıp, yazıp, açıklayabildiğini gördük. Yapay zeka, karmaşık görevleri daha küçük bileşenlere ayırarak gerçekleştirebiliyor. Bizim görevimiz, bu teknolojiyi nasıl kendi avantajımıza çevirebileceğimizi düşünmek.

---

