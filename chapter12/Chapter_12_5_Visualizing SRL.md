# Görselleştirme ve Anlama

SRL'i görselleştirmek, cümlelerin nasıl yapılandırıldığını anlamaya yardımcı olabilir. Hedef şudur: 
- Açıklanan kavramları okuyun ve anlayın 
- Rastgele LLMs çalıştırmadan önce verilen örnekleri anlamak için zaman ayırın.

Şimdi SRL örneğimizi görselleştireceğiz. 
## Şekil 12.2: "Yürüdü" fiili için bir cümlenin SRL gösterimi

Şekil 12.2, Marvin parktayürüdü : cümlesinin bir SRL gösterimidir.

Şekil 12.2'de aşağıdaki etiketleri gözlemleyebiliriz:
- **Fiil (Verb)**: Cümlenin yüklemi (V).
- **Argüman (Argument)**: Cümlenin bir argümanı, ARG0 olarak adlandırılır.
- **Değiştirici (Modifier)**: Cümlenin bir değiştiricisi - bu durumda, bir konum (ARGM-LOC). 
  - Bu, bir zarf, bir sıfat veya yüklemin anlamını değiştiren herhangi bir şey olabilir.

SRL'i tanımladık ve bir örnek üzerinden geçtik. Şimdi bazı SRL deneyleri yapalım.

Python kodu bulunmamaktadır, sadece bir ingilizce paragraf çevirisi yapılmıştır. 

Eğer bir python kodu olsaydı, satır satır açıklama yapılacaktı. Örneğin aşağıdaki gibi bir kod için:

```python
print("Merhaba, Dünya!")
```

Açıklama şu şekilde olacaktı:
- `print()`: Python'da ekrana çıktı veren bir fonksiyondur.
- `"Merhaba, Dünya!"`: Yazdırılacak olan string ifadedir.

---

