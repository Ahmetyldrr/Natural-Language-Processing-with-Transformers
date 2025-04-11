# Google Brain ile Trax Kurulumu ve Transformer Modeli Oluşturma

Google Brain, Trax'i kurulum ve çalıştırma açısından kolay hale getirmiştir. Temel bileşenleri Trax ile birlikte içe aktaracağız, Trax tek satırda kurulabilir:

```python
import os 
import numpy as np
!pip install -q -U trax 
import trax
```

*   `import os`: Bu satır, işletim sistemiyle etkileşime geçmek için kullanılan `os` modülünü içe aktarır. Bu modül, dosya ve dizin işlemleri gibi çeşitli işletim sistemi işlevlerine erişim sağlar.
*   `import numpy as np`: Bu satır, sayısal işlemler için popüler bir kütüphane olan NumPy'yi `np` takma adı altında içe aktarır. NumPy, büyük, çok boyutlu diziler ve matrisler için destek sağlar ve bu tür veri yapıları üzerinde çalışacak çeşitli matematiksel işlevler sunar.
*   `!pip install -q -U trax`: Bu satır, Trax kütüphanesini kurmak için kullanılır. 
    *   `!pip`: Jupyter Notebook veya benzeri bir ortamda, kabuk komutlarını çalıştırmak için kullanılan bir operatördür. Burada `pip` paket yöneticisini çalıştırmak için kullanılır.
    *   `install`: `pip` komutudur ve belirtilen paketi kurar.
    *   `-q`: Bu bayrak, `pip` komutunun çıktılarını kısar, yani sessiz modda çalışmasını sağlar. Kurulum sırasında detaylı çıktıların gösterilmesini engeller.
    *   `-U`: Bu bayrak, "upgrade" anlamına gelir ve belirtilen paketin en son sürüme güncellenmesini sağlar. Eğer paket zaten kuruluysa ve daha yeni bir sürümü varsa, bu bayrak paketin güncellenmesini zorlar.
    *   `trax`: Kurulacak veya güncellenecek paketin adıdır. Bu komut, Trax kütüphanesini kurar veya günceller.
*   `import trax`: Bu satır, yeni kurulan Trax kütüphanesini içe aktarır, böylece kod içinde kullanılabilir hale gelir.

Evet, gerçekten çok basit! Şimdi, Transformer modelimizi oluşturalım.

---

