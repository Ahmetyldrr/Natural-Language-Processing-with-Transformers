# Eğitilmiş Modeli Kaydetme

Eğitildikten sonra Generative AI ajanı ile sohbet etmek için bağımsız bir oturum çalıştırmak üzere modeli kaydedebilirsiniz: 
```python
trainer.save_model("/content/model/model/")
```
Google Colab, oturum kapandığında modeli geri dönüştürür. Modeli istediğiniz herhangi bir konuma kaydedebilirsiniz, örneğin Google Drive'da:
```python
# trainer.save_model("drive/MyDrive/files/model_C6/model/")
```
Yukarıdaki satırdaki `#` işareti, bu satırın yorum satırı olduğunu belirtir. Python yorumlayıcısı bu satırı çalıştırmaz. Gelecekte kullanmak üzere çıktıyı kaydetmek için bu satırın başındaki `#` işaretini kaldırmanız gerekir.

# Kod Açıklaması

1. `trainer.save_model("/content/model/model/")` : 
   - `trainer` nesnesinin `save_model` methodunu çağırır.
   - Eğitilen modeli `/content/model/model/` dizinine kaydeder.

2. `#trainer.save_model("drive/MyDrive/files/model_C6/model/")` : 
   - Bu satır yorum satırıdır, Python tarafından çalıştırılmaz.
   - `#` işaretini kaldırdığınızda, modeli "drive/MyDrive/files/model_C6/model/" dizinine kaydeder.

# Özet
Verilen İngilizce paragrafın birebir Türkçe çevirisi yukarıdaki gibidir. Python kodları satır satır açıklanmıştır. Markdown formatına uygun başlıklar kullanılmıştır.

---

