# Programın İşlevi
Program, Fransız filozof, bilim adamı ve matematikçi Descartes tarafından yazılmış içerik içeren bir dosyayı indirir:

## 1. Adım: Descartes.txt Dosyasını Colab Dosya Yöneticisi Kullanarak Yükleme
## 2. Adım: Dosyayı GitHub'dan İndirme
Dosyayı GitHub'dan indirmek için aşağıdaki komut kullanılır:
```bash
!curl -H -L https://raw.githubusercontent.com/Denis2054/Transformers-for-NLP-and-Computer-Vision-3rd-Edition/master/Chapter11/Descartes.txt --output "Descartes.txt"
```
Bu komutun açıklaması:
- `!curl`: Curl komutunu çalıştırır. Curl, veri transferi yapmak için kullanılan bir araçtır.
- `-H`: İsteğe ek başlık eklemek için kullanılır, ancak bu örnekte boş görünüyor ve muhtemelen bir hata veya gereksizdir.
- `-L`: İndirilen URL'nin yönlendirilmesini takip etmek için kullanılır. Eğer indirilen URL başka bir URL'ye yönlendiriyorsa, bu flag sayesinde curl yönlendirilen URL'ye gider ve işlemi orada gerçekleştirir.
- `https://raw.githubusercontent.com/Denis2054/Transformers-for-NLP-and-Computer-Vision-3rd-Edition/master/Chapter11/Descartes.txt`: İndirilecek dosyanın URL'sidir.
- `--output "Descartes.txt"`: İndirilen dosyanın kaydedileceği dosya adıdır.

## 3. Adım: Dosyayı Okuma ve İşleme
Dosyayı okumak ve işlemek için Python kodu kullanılır:
```python
with open('Descartes.txt', 'r', encoding='utf-8') as file:
    descartes_book = file.read().replace('\n', '')
```
Bu kodun satır satır açıklaması:
1. `with open('Descartes.txt', 'r', encoding='utf-8') as file:`:
   - `open()`: Bir dosyayı açmak için kullanılır.
   - `'Descartes.txt'`: Açılacak dosyanın adıdır.
   - `'r'`: Dosyanın okunacağını belirtir. "read" modunda açar.
   - `encoding='utf-8'`: Dosyanın kodlamasını belirtir. UTF-8, geniş karakter desteği olan bir kodlamadır.
   - `as file`: Açılan dosya, `file` değişkenine atanır.
2. `descartes_book = file.read().replace('\n', '')`:
   - `file.read()`: Dosya içeriğini okur.
   - `.replace('\n', '')`: Okunan içerikteki newline (`\n`) karakterlerini boş string ile değiştirir. Bu, dosya içeriğini tek bir satır haline getirir.
   - `descartes_book =`: İşlem sonucu `descartes_book` değişkenine atanır.

## 4. Adım: Metni Tokenize Etme
Artık metni tokenize edebiliriz. (Bu adım verilen metinde kod olarak gösterilmemiştir, ancak açıklama olarak bahsedilmiştir.)

---

