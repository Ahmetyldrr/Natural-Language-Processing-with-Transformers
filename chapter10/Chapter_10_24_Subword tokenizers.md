# Transformer Modelleri ve Alt Kelime Tokenizerları

Transformer modelleri büyük ölçekli Büyük Dil Modelleri'dir (LLM). Modellerin boyutu ve gerçekleştirdikleri görev sayısı, yüksek verimli tokenleştiricilere ihtiyaç duyduğunu gösterir. Alt kelime tokenleştiricileri, birçok nedenle LLM'ler için en iyi seçimdir; bunlar arasında:

*   **Sözlüğün Dışındaki (OOV) Kelimeler**: Bir alt kelime tokenleştiricisi, eğitim aşamasında olmayan kelimeleri (OOV) yakalayabilir. Tokenleştirici, OOV'leri bir transformer modelinin işleyebileceği küçük birimlere böler.
*   **Sözlük Optimizasyonu**: Alt kelime tokenleştiricileri, cümle ve kelime tokenleştiricilerinden daha küçük birimlere ayırır. Sözlüğün boyutu optimize edilmiştir.
*   **Biçimbilimsel Esneklik**: Alt kelime tokenleştiricileri kelimeleri daha küçük birimlere böler. Elde edilen birimler, bir modelin dili anlama yeteneğini derinleştirerek diğer küçük birimlerle genellemelere kapı açar.
*   **Gürültü Direnci**: Bir kelime yanlış yazılmış veya yazım hatası içermekteyse bile, bir alt kelime tokenleştiricisi yine de anlamını yakalayabilir ve işleyebilir.
*   **Çoklu Diller**: Kelime düzeyindeki tokenleştiriciler bir dile bağlıdır. Alt kelime tokenleştiricileri ise değildir.

BPE ve WordPiece, genellikle transformer modelleri için kullanılır. Bu iki alt kelime tokenleştiricisinin ilkelerini anlamak, herhangi bir alt kelime tokenleştiricisinin nasıl çalıştığını anlamanıza yardımcı olacaktır. BPE ve WordPiece üzerinde odaklansak da, bunlar tek alt kelime tokenleştiricileri değildir. Projenize bağlı olarak, diğer alt kelime tokenleştiricileri daha verimli olabilir.

Öncesinde BPE ve WordPiece'e geçmeden önce, iki ana tokenleştiriciyi inceleyerek metin dizilerinin alt kelimelere nasıl ayrıldığını görelim.

### Gerekli Kütüphanelerin Kurulması

İlk olarak, Hugging Face kütüphanelerini ve SentencePiece için bir Python wrapper'ı kuracağız:

```python
!pip install transformers -qq
!pip install sentencepiece -qq
```

Şimdi, BPE veya WordPiece olmayan iki alt kelime kütüphanesini inceleyeceğiz. 
`Open Sub_word_tokenizers.ipynb` dosyasını açın.

---

