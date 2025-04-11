# Yazılımın Girdi ve Çıktılarını Kontrol Etme

Herhangi bir yazılımı uygulamak, girdi ve çıktılarını kontrol etmeyi gerektirir. Üretken Yapay Zeka da istisna değildir. Bu bölümde, bir Büyük Dil Modeli'nin (LLM) girdi ve çıktılarını kontrol etmenin bazı yollarını ele alacağız.

## OpenAI Moderasyon API'sini Kullanma

Bir metni işlemek ve OpenAI'ın en son moderasyon endpoint'ine göndermek için bir fonksiyon oluşturabiliriz:
```python
import requests

# OpenAI moderasyon API'si için URL
url = "https://api.openai.com/v1/moderations"

# Yetkilendirme ve İçerik Türü başlıkları dahil başlıklar
headers = {
    "Authorization": f"Bearer {openai.api_key}",
    "Content-Type": "application/json"
}

# Veri yükü
data = {
    "input": text
}

# POST isteği
response = requests.post(url, json=data, headers=headers)

# Yanıtı yazdır (veya gerektiği gibi işleyin)
print(response.json())
```
Bu kod, OpenAI'ın moderasyon API'sine bir metni gönderir ve yanıtı yazdırır.

## Moderasyon API'sinin Sınırlamaları

OpenAI'ın moderasyon aracı, metni analiz ettiği için, bir kuruluş içinde zararlı içerik olup olmadığını belirleyemez. Örneğin, bir cümle gramatik olarak doğru olabilir, ancak içerik zararlı olabilir.

## Kuruluş Politikalarını Uygulama

Her kuruluşun kendi politikaları vardır ve tam uyum gerektirir. Bu nedenle, bir kural tabanı oluşturmak ve duyarlı bilgilerin API'ye gönderilmeden önce filtrelenmesini sağlamak önemlidir.

## Kural Tabanı Oluşturma

Aşağıdaki kod, bir kural tabanı simüle eder:
```python
def rule_base(text):
    words = ['bad', 'distasteful', 'evil', 'unproductive', 'null']
    for word in words:
        if word in text:
            print("Girdi işaretlendi: True")
            return
    print("Girdi işaretlendi: False")
```
Bu fonksiyon, metinde yasaklı kelimelerin olup olmadığını kontrol eder.

## Kural Tabanını Uygulama

Kullanıcı girdilerini moderasyon modeline göndermeden önce kural tabanını etkinleştiririz:
```python
# Fonksiyonu test edin
rule_base("Bu kötü bir örnek")
rule_base("Bu iyi bir örnek")
```
Bu, yasaklı kelimelerin filtrelenmesini sağlar.

## Moderasyon Modelinin Çıktısı

Moderasyon modelinin çıktısı, girdinin durumunu içerir:
```python
response = moderator(text)
response["results"][0]["flagged"]
```
Bu, moderasyon modelinin girdiyi işaretleyip işaretlemediğini gösterir.

## Kategorileri ve Kategori Skorlarını Görüntüleme

Moderasyon modelinin çıktısı, kategorileri ve kategori skorlarını içerir:
```python
response["results"][0]["categories"]
response["results"][0]["category_scores"]
```
Bu, her kategori için durumu ve güvenilirlik seviyesini gösterir.

## Model Çıktısını Kontrol Etme

Model çıktısı da kural tabanından geçmelidir. Daha sonra, içerik kural tabanına göre güvenliyse, moderasyon modeline gönderilir.

Bu şekilde, hem girdi hem de çıktı kontrol edilir ve kuruluş politikalarına uyum sağlanır.

---

