# WordPiece Tokenizer Nedir?
WordPiece, BPE gibi, bireysel karakterlerden oluşan bir kelime haznesi ile başlar. Bu, herhangi bir kelimenin tokenize edilebilmesini sağlar. Ardından, eğitim süreci alt kelimeleri (subwords) oluşturur. Alt kelimelerin sayısını en aza indirmek için bir optimizasyon süreci kullanır. Eğitim süreci tamamlandığında, tokenizer dizileri kelime haznesindeki en uzun dizi kelimelere ayıracaktır. Orijinal kelimenin başında olmayan alt kelimeler ## ön eki içerir. Örneğin, "undo" ["un", "##do"] olarak temsil edilecektir. Bunu aklınızda tutun çünkü WordPiece tokenizörlerini tanımlamamıza yardımcı olacaktır. Tokenizer'lar bir transformer modelinin eğitimi üzerinde güçlü bir etkiye sahip olacaktır. Doğru tokenizer'ı seçmek genellikle başlangıçtan itibaren sonucunu belirleyecektir. Şimdi, bir WordPiece tokenizer'ın çıktısını inceleyelim.

Python kodu bulunmamaktadır, sadece bir ingilizce paragrafın türkçeye çevirisi yapılmıştır. 

Eğer bir python kodu olsaydı, satır satır açıklama yapardım. Ancak burada sadece bir metin çevirisi mevcut. 

İlgili kavramlar hakkında python kodu örneği isterseniz, örneğin WordPiece tokenization için Hugging Face kütüphanesinin `BertTokenizer` sınıfını kullanabilirsiniz:
```python
from transformers import BertTokenizer

# Tokenizer'ı yükle
tokenizer = BertTokenizer.from_pretrained('bert-base-uncased')

# Metni tokenize et
inputs = tokenizer("undo", return_tensors="pt")

# Tokenize edilmiş metni yazdır
print(inputs)
```
Bu kod, "undo" kelimesini WordPiece tokenization kullanarak tokenize eder ve çıktısını yazdırır.

---

