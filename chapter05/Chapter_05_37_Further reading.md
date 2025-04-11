# Çeviri
Vladislav Mosin, Igor Samenko, Alexey Tikhonov, Borislav Kozlovskii, ve Ivan P. Yamshchikov , 2021, Transformers'ı İnce Ayarlama: Sözcük Transferi : https://arxiv.org/abs/2112.14569  
Yi Tay, Mostafa Dehghani, Jinfeng Rao, William Fedus, Samira Abnar, Hyung Won Chung, Sharan Narang, Dani Yogatama, Ashish Vaswani, ve Donald Metzler , 2022, Ölçeklendirme Verimliliği: Transformers'ı Ön Eğitimi ve İnce Ayarlama : https://arxiv.org/abs/2109.10686  
Discord'da Topluluğumuza Katılın  
Yazarlar ve diğer okuyucularla tartışmak için topluluğumuzun Discord alanına katılın: https://www.packt.link/Transformers

# Python Kodları Yok

Bu metinde herhangi bir Python kodu bulunmamaktadır. Dolayısıyla, satır satır açıklama yapmaya gerek yoktur. Çeviri işlemi basit bir metin çevirisidir. 

Eğer çeviri işlemini Python kullanarak yapmak isteseydik, aşağıdaki gibi bir kod kullanabilirdik:

```python
import translators as ts

# Çeviri yapılacak metin
metin = """
Vladislav Mosin, Igor Samenko, Alexey Tikhonov, Borislav Kozlovskii, and Ivan P. Yamshchikov , 2021, Fine-Tuning Transformers: Vocabulary Transfer : https://arxiv.org/abs/2112.14569 Yi Tay, Mostafa Dehghani, Jinfeng Rao, William Fedus, Samira Abnar, Hyung Won Chung, Sharan Narang, Dani Yogatama, Ashish Vaswani, and Donald Metzler , 2022, Scale Efficiently: Insights from Pre-training and Fine-tuning Transformers : https://arxiv.org/abs/2109.10686 Join our community on Discord Join our community’s Discord space for discussions with the authors and other readers: https://www.packt.link/Transformers
"""

# Çeviri işlemi
ceviri = ts.google(metin, to_language='tr')

# Çıktı
print(ceviri)
```

Bu kod, `translators` kütüphanesini kullanarak verilen metni İngilizce'den Türkçe'ye çevirir. 

1. `import translators as ts`: `translators` kütüphanesini `ts` takma adıyla içe aktarır.
2. `metin = "..."`: Çeviri yapılacak metni değişkene atar.
3. `ceviri = ts.google(metin, to_language='tr')`: `translators` kütüphanesinin `google` fonksiyonunu kullanarak metni Türkçe'ye çevirir.
4. `print(ceviri)`: Çeviri sonucunu yazdırır.

---

