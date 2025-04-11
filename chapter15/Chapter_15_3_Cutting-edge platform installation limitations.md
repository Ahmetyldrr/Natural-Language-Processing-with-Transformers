# Kesintisiz Güncellemeler ve OpenAI Kurulumu

Kesintisiz güncellenen platformlar sürekli olarak uygulamalarını değiştiriyor, yükseltiyor ve güncelliyor, bu da düzenli istikrarsızlıklar yaratıyor. 16 Ocak 2024 tarihinde Google Colab'da OpenAI'ın kurulumunu herhangi bir not defteri için inceleyelim:

## OpenAI'ı İçe Aktarma
```python
!pip install openai
```
Birkaç paket başarıyla kurulur, ancak belirli sürümlerle:
```
Requirement already satisfied: anyio<5,>=3.5.0 in /usr/local/lib/python3.10/dist-packages (from openai) (3.7.1)
Requirement already satisfied: distro<2,>=1.7.0 in /usr/lib/python3/dist-packages (from openai) (1.7.0)
Collecting httpx<1,>=0.23.0 (from openai)
  Downloading httpx-0.26.0-py3-none-any.whl (75 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 75.9/75.9 kB 7.6 MB/s eta 0:00:00
Requirement already satisfied: pydantic<3,>=1.9.0 in /usr/local/lib/python3.10/dist-packages (from openai) (1.10.13)
Requirement already satisfied: sniffio in /usr/local/lib/python3.10/dist-packages (from openai) (1.3.0)
Requirement already satisfied: tqdm>4 in /usr/local/lib/python3.10/dist-packages (from openai) (4.66.1)
Collecting typing-extensions<5,>=4.7 (from openai)
  Downloading typing_extensions-4.9.0-py3-none-any.whl (32 kB)
```
Sürüm kısıtlamalarına dikkat edin. Eğer Google Colab platformunu güncellerse veya OpenAI paketlerini yükseltiyorsa, kurulum başarısız olur.

### Kurulum Sırasındaki Sorunlar
Kurulum aşağıdaki üç sorun nedeniyle tamamlanmaz (Ocak 2024):
- typing_extensions

Kurulum şu bilgiyi sağlar:
```
Installing collected packages: typing-extensions, h11, httpcore, httpx, openai
  Attempting uninstall: typing-extensions
    Found existing installation: typing_extensions 4.5.0
    Uninstalling typing_extensions-4.5.0:
      Successfully uninstalled typing_extensions-4.5.0
```
Ancak daha sonra şu mesajı alırız:
```
tensorflow-probability 0.22.0 requires typing-extensions<4.6.0, but you have typing-extensions 4.9.0 which is incompatible.
```
OpenAI, önerdiği sürümü kaldırdı veya belki kendi sürümüne sahip.

### cohere Kurulumu
cohere için şu mesajı alırız:
```
llmx 0.0.15a0 requires cohere, which is not installed.
```
Ancak önce `!pip install cohere` ile cohere kurmaya çalıştığımızda, openai ve tiktoken gerektirir:
```
llmx 0.0.15a0 requires openai, which is not installed.
llmx 0.0.15a0 requires tiktoken, which is not installed.
```

### tiktoken Kurulumu
`tiktoken` kurmaya çalıştığımızda (`!pip install tiktoken`), hata mesajı alırız:
```
llmx 0.0.15a0 requires cohere, which is not installed.
llmx 0.0.15a0 requires openai, which is not installed.
```

## Çözümler
Eğer `!pip install openai` tek başına çalışmazsa, üç çözüm vardır:
1. **OpenAI'ın kurulum sürümünü sabitleyin.** `!pip install openai==0.28` kullanılabilir. Ancak bu, çağırdığımız modelde sorunlara yol açabilir.
2. **Belirli bir ortam oluşturun.** Sunucunuzda tüm gereksinimlerle bir ortam oluşturun ve modelin iptal tarihlerini izleyin. Bu, üretim ortamları için önerilir.
3. **Zor yolu seçin!** Bu kitap için, GitHub deposunu güncel tutmak amacıyla bu yolu seçtik. Paketleri manuel olarak kurmak gerekir.

### Manuel Kurulum Sırası
Aşağıdaki sıra ile kurulum yapılır (16 Ocak 2024):
```python
!pip install openai
!pip install cohere
!pip install tiktoken
!pip install cohere
!pip install openai
```
Bu kez OpenAI kurulumunda hata olmaz:
```
Requirement already satisfied: openai in /usr/local/lib/python3.10/dist-packages (1.7.2)
...
```
`typing-extensions` sorunu, yukarıdaki kurulum sırası ile çözülür.

Artık Google Colab'da "Run all" butonuna tıklayabilir veya ortamınızda "run all" komutunu çalıştırabilirsiniz. Bazı not defterleri `tiktoken` veya `core` gerektirmez ve sorunsuz çalışır.

---

