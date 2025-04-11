# Doğruluk Değerlendirmesi

Aşağıdaki ifadelerin doğruluğunu değerlendireceğiz.

## İfadeler ve Doğruluk Değerleri

1. RoBERTa, bayt düzeyinde bayt çifti kodlama tokenizer kullanır. (Doğru/Yanlış)
2. Eğitilmiş bir Hugging Face tokenizer, merges.txt ve vocab.json üretir. (Doğru/Yanlış)
3. RoBERTa, token-tipi ID'leri kullanmaz. (Doğru/Yanlış)
4. DistilBERT'in 6 katmanı ve 12 başlığı vardır. (Doğru/Yanlış)
5. 80 milyon parametreli bir transformer modeli çok büyüktür. (Doğru/Yanlış)
6. Bir tokenizer'ı eğitemeyiz. (Doğru/Yanlış)
7. BERT benzeri bir modelin altı kod çözücü katmanı vardır. (Doğru/Yanlış)
8. MLM, bir cümledeki maske tokenında bulunan bir kelimeyi tahmin eder. (Doğru/Yanlış)
9. BERT benzeri bir modelin kendi dikkatini çekme alt katmanları yoktur. (Doğru/Yanlış)
10. Veri toplayıcıları, geri yayılım için yararlıdır. (Doğru/Yanlış)

## Cevaplar

1. RoBERTa, bayt düzeyinde bayt çifti kodlama tokenize edicisi kullanır. 
   - Doğru, RoBERTa bayt düzeyinde BPE tokenize edicisi kullanır.

2. Eğitilmiş bir Hugging Face tokenizer, merges.txt ve vocab.json üretir. 
   - Doğru, Hugging Face kütüphanesindeki tokenizer'lar genellikle merges.txt ve vocab.json dosyaları üretir.

3. RoBERTa, token-tipi ID'leri kullanmaz. 
   - Doğru, RoBERTa token-tipi ID'leri kullanmaz.

4. DistilBERT'in 6 katmanı ve 12 başlığı vardır. 
   - Doğru, DistilBERT genellikle 6 katmana ve her katmanda 12 dikkat başlığına sahiptir.

5. 80 milyon parametreli bir transformer modeli çok büyüktür. 
   - Yanlış, 80 milyon parametre göreceli olarak küçük bir modeldir.

6. Bir tokenizer'ı eğitemeyiz. 
   - Yanlış, tokenizer'lar eğitilebilir.

7. BERT benzeri bir modelin altı kod çözücü katmanı vardır. 
   - Yanlış, BERT benzeri modeller kodlayıcı (encoder) mimarisine sahiptir, kod çözücü (decoder) değil.

8. MLM, bir cümledeki maske tokenında bulunan bir kelimeyi tahmin eder. 
   - Doğru, Maskelenmiş Dil Modeli (MLM), maskelenmiş tokenlardaki orijinal kelimeleri tahmin eder.

9. BERT benzeri bir modelin kendi dikkatini çekme alt katmanları yoktur. 
   - Yanlış, BERT benzeri modeller kendi dikkat (self-attention) mekanizmalarına sahiptir.

10. Veri toplayıcıları, geri yayılım için yararlıdır. 
    - Doğru, veri toplayıcıları (data collators) eğitim verilerini hazırlamada ve geri yayılım sırasında yararlı olurlar.

Python kodları bulunmamaktadır, bu nedenle açıklama yapılmamıştır. Yukarıdaki metin, verilen İngilizce paragrafın birebir Türkçe çevirisidir.

---

