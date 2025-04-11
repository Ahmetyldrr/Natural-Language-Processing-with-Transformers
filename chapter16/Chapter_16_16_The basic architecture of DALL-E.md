# DALL-E Modelinin Açıklaması

CLIP'in aksine, DALL-E 256'ya kadar BPE kodlu metin tokenını 32×32 = 1,024 görüntü tokenıyla birleştirir, Şekil 16.11'de gösterildiği gibi:

# Şekil 16.11: DALL-E Metin ve Görüntü Girişini Birleştirir

Şekil 16.11'de gösterildiği gibi, bu sefer kedimiz görüntü, giriş metniyle birleştirilir. OpenAI, DALL-E'in kaynak kodunu halka açık bir şekilde yayınlamamıştır. OpenAI tarafından yayınlanmayan herhangi bir kaynak kodu şüpheyle karşılanmalıdır. Bu bölümdeki açıklama, yaklaşımın kavramlarını yansıtmaktadır, ancak Ocak 2024 itibarıyla modelin mimarisi muhtemelen gelişmiştir.

Modelin genel mimarisini anlamak için resmi bir makaleye güvenebiliriz: Ramesh ve ark. (2021), Zero-Shot Text-to-Image Generation : https://arxiv.org/abs/2102.12092 .

# Zero-Shot Text-to-Image Generation Makalesi

Zero-Shot Text-to-Image Generation makalesi, iki aşamalı bir yöntemden bahseder:

## Aşama 1: Ayrık Varyasyonlu Otomatik Kodlayıcı (DVAE) Kullanımı

Algoritmanın amacı, 256x256=65536 değerinde bir RGB görüntüsünü giriş olarak almaktır. Çıktı, her bir tokenın 8192 (ampirik seçim) olası değerden birine sahip olabileceği, çok daha küçük bir 32x32=1024 görüntü token ızgarasıdır.

## Aşama 2: BPE Kodlu Metin Tokenlarının 32x32=1024 Görüntü Tokenlarıyla Birleştirilmesi

Şekil 16.11'de gösterildiği gibi, "256'ya kadar BPE kodlu metin tokenının 32x32=1024 görüntü tokenıyla birleştirilmesi". Modelin amacı, transformer aracılığıyla metin ve görüntü tokenlarının ortak dağılımını eğitmek. Transformer'ın dikkat mekanizması, modelin çıktı oluştururken görüntü ve metin girişinin farklı bölümlerine odaklanmasını sağlar. Bu durumda, transformer özellikle uzun görüntü ve metin veri dizilerini işleme konusunda yararlıdır.

Şimdi, görüntü oluşturmak için DALL-E 2 ve DALL-E 3 API'sine el atalım!

Bu çeviride Python kodları bulunmamaktadır.

---

