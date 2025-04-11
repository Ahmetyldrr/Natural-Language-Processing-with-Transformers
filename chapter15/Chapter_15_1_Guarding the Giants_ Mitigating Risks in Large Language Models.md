# 16 Mayıs 2023 Tarihinde Yapılan Açıklama
16 Mayıs 2023 tarihinde, ChatGPT'nin sahibi OpenAI'ın CEO'su Sam Altman, Amerika Birleşik Devletleri Kongresi'ne hitaben yaptığı konuşmada, "Amacımız, yapay zekayı gizemden arındırmak ve yeni teknolojileri hesap verebilir kılmak ve geçmişin bazı hatalarından kaçınmaktır" dedi. Bu açıklama, Büyük Dil Modelleri (LLM'ler) ile ilgili riskleri azaltmamız gerektiğini gösteriyor.

# Gelişmiş Yapay Zeka Teknolojileri
Bu kitapta bu bölüme kadar olan yolculuğumuz, 1. Bölüm'de sorulan "Transformers Nedir?" sorusunu yanıtladı - transformer'lar Genel Amaçlı Teknolojilerdir (GPT'ler). Ana akım uygulamalar aracılığıyla, her alanda asistan haline geldiler: sosyal medya, üretkenlik yazılımları (kelime işlemciler, elektronik tablolar ve slaytlar), geliştirme yardımcıları ve daha fazlası. Yapay zeka, elektrik, nükleer enerji, yanmalı motorlar, bilgisayar çipleri ve elektronik bağlantılar dahil olmak üzere birçok GPT'den sadece biridir. Tüm bu teknolojilerin ortak bir noktası var: detaylı olarak nasıl kullanılacağını hayal etmek imkansızdır.

# Elektriğin Keşfi ve Geleceği
M.Ö. 600 civarında, Antik Yunan filozof Thales, kehribar ve ipeği ovuşturdu ve bunun tüyleri ve diğer nesneleri çektiğini gördü. İngilizceye çevrilen "kehribar" kelimesi "elektron"dur ve bu, "elektrik" kelimesine yol açtı. Kim, icat edilmeden önce her elektrikli cihaz için düzenlemeleri hayal edebilirdi? Hiç kimse. Yeni ortaya çıkan bir GPT'nin, örneğin yapay zeka destekli Temel Model transformer'larının bilinmeyen fırsatları ve riskleri, insanlık tarihindeki her icat için kabul edilmelidir. Transformer-üretken yapay zeka da bir istisna değildir. Bunu bilmemiz ve projelerimizde yapay zekayı uygulamak için en etik yolu bulmaya odaklanmamız gerekiyor.

# Yapay Zeka Riskleri ve Yönetimi
Bu noktaya kadar transformer'ların fırsatlarını gördük. Bilgisayar vizyonunun potansiyelini keşfetmeye başlamadan önce, bu yeni devlerin risklerini nasıl azaltacağımızı görmemiz gerekiyor! Fonksiyonel yapay zekanın muhtemelen gelecek yıllarda gereklilikten ortaya çıkacağını anlayarak başlayacağız. Daha sonra risk yönetimi ve risk azaltma araçları olmak üzere iki ana bölümde devam edeceğiz. Risk yönetimi, aralarında hiyerarşi olmadan bazı ana riskleri ele alacaktır. Bu riskler bir yapay zeka projesini yok edebilir: halüsinasyonlar, ezberleme, riskli ortaya çıkan davranış, yanlış bilgilendirme, etki operasyonları, zararlı içerik, düşmanca saldırılar ("jailbreaks"), gizlilik, siber güvenlik ve aşırı güven.

# Risk Azaltma Araçları
Bu potansiyel olarak zararlı risklerden kaçınmak ve sadece LLM'lerin sunduğu fırsatlar hakkında yazmak çok daha hoş olurdu. Ancak, müşterilerimiz, takımlarımız ve son kullanıcılarla güvenilir bir ilişki kurmak için bu riskleri ele almalıyız. Daha sonra gelişmiş prompt mühendisliği, moderasyon modeli uygulama, bilgi tabanı, anahtar kelime ayrıştırma, prompt pilotları, işlem sonrası moderasyon ve embeddings gibi bazı risk azaltma araçlarını ele alacağız. Bölümün sonunda, bazı ana riskleri ve azaltma yöntemlerini anlayacaksınız. Riskleri azaltmak ve yeniliklerin tadını çıkarmak için daha fazla yol icat edebilirsiniz!

# Bu Bölümde İşlenecek Konular
Bu bölüm aşağıdaki konuları kapsar:
- Fonksiyonel YZ Taklidi
- Risk yönetimi
- Risk azaltma araçları
- Moderasyon transformer'ları
- Bilgi tabanı oluşturma, RAG ve RLHF
- Anahtar kelime ayrıştırma
- İşlem sonrası moderasyon
- Embeddings
- Token yönetimi

# Kod Örnekleri ve Güncellemeler
Bu son teknoloji alanında yapılan tüm yenilikler ve kütüphane güncellemeleri ile paketler ve modeller düzenli olarak değişmektedir. Lütfen en son kurulum ve kod örnekleri için GitHub deposuna gidiniz: https://github.com/Denis2054/Transformers-for-NLP-and-Computer-Vision-3rd-Edition/tree/main/Chapter15 . Bu veya diğer bölümlerdeki kodları çalıştırırken herhangi bir sorunuz varsa Discord topluluğumuza bir mesaj gönderebilirsiniz ( https://www.packt.link/Transformers ).

# Risk Yönetimini İncelemeye Başlamak
Risk yönetimini incelemeye başlamadan önce, fonksiyonel YZ'yi anlamaya başlayacağız.

Python kodları bulunmamaktadır, eğer python kodları içeren bir metin verecekseniz, kodları satır satır açıklayabilirim.

---

