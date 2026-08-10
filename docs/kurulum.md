# Qwen Code Türkçe — Windows Kurulum Rehberi

Bu belge, Qwen Code'u Windows üzerinde kullanmaya başlamak isteyen Türkçe konuşan kullanıcılar için hazırlanmıştır.

> [!IMPORTANT]
> Bu depo Qwen ekibinin resmi projesi değildir. Bağımsız bir Türkçe topluluk dokümantasyonu çalışmasıdır. Qwen Code hızla gelişen bir proje olduğundan komutlar ve gereksinimler zaman içinde değişebilir. Güncel sürüm için resmi Qwen Code kaynaklarını da kontrol edin.

---

## İçindekiler

- Qwen Code nedir?
- Sistem gereksinimleri
- Node.js kurulumu
- Git kurulumu
- Qwen Code kurulumu
- Kurulumun doğrulanması
- İlk çalıştırma
- Bir proje klasöründe kullanma
- Model ve API yapılandırması
- Yerel model kullanımı
- LM Studio ile kullanım
- MCP hakkında
- Windows'ta sık karşılaşılan sorunlar
- Güncelleme
- Kaldırma
- Güvenlik önerileri

---

## 1. Qwen Code Nedir?

Qwen Code, yazılım geliştirme görevlerinde yapay zekâ modellerinden yararlanmayı kolaylaştıran terminal tabanlı bir kodlama aracıdır.

Bir proje üzerinde çalışırken yapay zekâya doğal dille görev verebilir ve proje bağlamı üzerinde çalışmasını sağlayabilirsiniz.

Örnek kullanım alanları:

- mevcut kodu inceleme,
- proje yapısını anlama,
- hata araştırma,
- kod üretme,
- mevcut kodu değiştirme,
- refactoring,
- test hazırlama,
- dokümantasyon oluşturma,
- terminal tabanlı geliştirme görevleri,
- büyük projelerde dosyalar arasında ilişki kurma,
- MCP tabanlı harici araçlarla çalışma.

Qwen Code kullanırken yapay zekânın yaptığı değişiklikleri kontrol etmek ve önemli projelerde Git kullanmak önerilir.

---

# 2. Sistem Gereksinimleri

Kuruluma başlamadan önce aşağıdaki bileşenlerin mevcut olması önerilir:

- Windows 10 veya Windows 11
- 64-bit işletim sistemi
- İnternet bağlantısı
- Node.js
- npm
- Git
- PowerShell veya Windows Terminal
- Kullanılacak modele/API sağlayıcısına erişim

Mevcut sürümleri kontrol etmek için terminal açın.

```powershell
node --version
npm --version
git --version
Komutlardan biri bulunamıyorsa ilgili bileşenin kurulması gerekir.

3. Node.js Kurulumu

Node.js'in güncel LTS sürümünün kullanılması önerilir.

Kurulumdan sonra yeni bir PowerShell veya Windows Terminal penceresi açın ve doğrulayın:

node --version
npm --version

Her iki komut da sürüm bilgisi döndürmelidir.

Örneğin:

vXX.XX.X
XX.X.X

Sürüm numaralarının örnektekilerle aynı olması gerekmez.

4. Git Kurulumu

Git'in sistemde bulunup bulunmadığını kontrol edin:

git --version

Git kuruluysa aşağıdakine benzer bir çıktı alınır:

git version X.XX.X.windows.X

Komut bulunamıyorsa Git for Windows kurulmalıdır.

Kurulum tamamlandıktan sonra terminali kapatıp yeniden açın.

5. Qwen Code Kurulumu

Qwen Code'un güncel resmi kurulum yöntemini kullanın.

npm tabanlı kurulum kullanılan sürümlerde paket, resmi dokümantasyonda belirtilen npm komutuyla kurulabilir.

Kurulumdan önce npm'in çalıştığını doğrulayın:

npm --version

Ardından Qwen Code'un resmi deposundaki güncel kurulum komutunu uygulayın.

[!NOTE]
Paket adı veya kurulum yöntemi sürümler arasında değişebileceğinden bu dokümanda eski bir komutu kalıcı olarak sabitlemek yerine güncel resmi Qwen Code dokümantasyonunun kontrol edilmesi önerilir.

6. Kurulumun Doğrulanması

Kurulum tamamlandıktan sonra Qwen Code komutunun sistem tarafından görüldüğünü doğrulayın.

Öncelikle yardım veya sürüm komutlarını deneyin:

qwen --help

ve destekleniyorsa:

qwen --version

Komut çalışıyorsa temel kurulum tamamlanmıştır.

7. İlk Çalıştırma

Yeni bir çalışma klasörü oluşturabilirsiniz:

mkdir qwen-test
cd qwen-test

Daha sonra Qwen Code'u başlatın:

qwen

İlk çalıştırmada kullanılan sürüme ve sağlayıcıya bağlı olarak model veya kimlik doğrulama yapılandırması gerekebilir.

8. Mevcut Bir Projede Kullanma

Örneğin projeniz:

C:\Projeler\BenimUygulamam

klasöründeyse:

cd C:\Projeler\BenimUygulamam
qwen

şeklinde çalıştırabilirsiniz.

Böylece Qwen Code proje bağlamında çalışabilir.

İlk görev olarak doğrudan kod değiştirmek yerine projeyi analiz ettirmek yararlı olabilir.

Örneğin:

Bu projeyi incele. Önce klasör yapısını, kullanılan teknolojileri,
çalıştırma yöntemini ve önemli bileşenleri belirle.
Henüz hiçbir dosyayı değiştirme.
9. Git ile Güvenli Çalışma

Yapay zekâ araçlarıyla kod değiştirirken Git kullanılması önemlidir.

Yeni projede:

git init
git add .
git commit -m "Initial project state"

Mevcut değişiklikleri görmek için:

git status

Farkları görmek için:

git diff

Bu yöntem, yapay zekâ tarafından yapılan değişiklikleri kontrol etmeyi kolaylaştırır.

10. Model ve API Yapılandırması

Qwen Code farklı model veya servis yapılandırmalarıyla kullanılabilir.

Kullanılan sürüme bağlı olarak yapılandırma aşağıdakilerden biri veya birkaçı üzerinden yapılabilir:

ortam değişkenleri,
yapılandırma dosyaları,
komut satırı seçenekleri,
OpenAI uyumlu API uç noktaları,
desteklenen bulut sağlayıcıları,
yerel model sunucuları.

API anahtarlarını doğrudan proje kaynak koduna yazmayın.

Örneğin şu yaklaşım kullanılmamalıdır:

API_KEY=gercek-gizli-api-anahtarim

ve bu bilgi GitHub'a gönderilmemelidir.

11. Ortam Değişkenleri

Windows PowerShell oturumunda bir ortam değişkeni geçici olarak şu mantıkla tanımlanabilir:

$env:DEGISKEN_ADI="deger"

Kalıcı değişkenler oluşturulurken API anahtarlarının güvenli biçimde saklanmasına dikkat edilmelidir.

Projeye .env benzeri gizli bilgi içeren dosyalar ekleniyorsa .gitignore kullanılmalıdır.

Örneğin:

.env
.env.*
secrets.json
*.key

Gerçek API anahtarlarını hiçbir zaman örnek dokümantasyona veya public GitHub deposuna eklemeyin.

12. Yerel Model Kullanımı

Qwen Code'un kullanılan sürümü OpenAI uyumlu bir API endpoint'i destekliyorsa yerel model sunucularıyla entegrasyon mümkün olabilir.

Bu yaklaşımda genel mimari şöyledir:

Qwen Code
    |
    v
OpenAI uyumlu API
    |
    v
Yerel model sunucusu
    |
    v
LLM

Yerel kullanımın avantajları:

verilerin yerel sistemde tutulabilmesi,
bazı senaryolarda API maliyetinin azaltılması,
farklı modellerin denenebilmesi,
geliştirici ortamının özelleştirilebilmesi.

Ancak yerel modellerin performansı kullanılan donanıma, modele, quantization seviyesine ve context büyüklüğüne bağlıdır.

13. LM Studio ile Kullanım

LM Studio, yerel modelleri çalıştırabilen ve uygun yapılandırmalarda OpenAI uyumlu API sunabilen araçlardan biridir.

Genel kullanım akışı:

LM Studio
   |
   +-- Model yükle
   |
   +-- Local Server başlat
   |
   +-- OpenAI compatible endpoint
                |
                v
             Qwen Code

Tipik yerel endpoint yapısı aşağıdakine benzeyebilir:

http://localhost:1234/v1

Ancak port ve endpoint LM Studio yapılandırmasına göre değişebilir.

Entegrasyon yapılırken Qwen Code'un güncel sürümünün desteklediği model/API ayarları kontrol edilmelidir.

14. MCP Nedir?

MCP, yani Model Context Protocol, yapay zekâ uygulamalarının harici araçlar ve veri kaynaklarıyla standartlaştırılmış biçimde iletişim kurmasını amaçlayan bir protokoldür.

MCP sayesinde uygun istemciler:

dosya sistemleri,
geliştirici araçları,
veri kaynakları,
servisler,
özel araçlar

ile entegre edilebilir.

Basitleştirilmiş mimari:

Qwen Code
    |
    v
MCP Client
    |
    v
MCP Server
    |
    +-- Tool
    +-- Resource
    +-- External Service

MCP kurulumu ve yapılandırması ayrı bir rehberde ele alınacaktır.

15. Windows'ta Sık Karşılaşılan Sorunlar
node komutu bulunamadı

Örnek:

'node' is not recognized...

Muhtemel nedenler:

Node.js kurulu değildir.
PATH güncellenmemiştir.
Terminal kurulumdan önce açılmıştır.

Terminali kapatıp yeniden açın ve tekrar deneyin:

node --version
npm komutu bulunamadı

Kontrol edin:

npm --version

Node.js kurulumu bozuk veya PATH eksik olabilir.

qwen komutu bulunamadı

Öncelikle npm global paket konumunu kontrol edin:

npm prefix -g

Daha sonra Qwen Code paketinin gerçekten kurulduğunu doğrulayın.

Terminali yeniden başlatmak da gerekebilir.

PowerShell script çalıştırma hatası

Bazı npm tabanlı komutlarda PowerShell execution policy nedeniyle .ps1 dosyalarının çalıştırılması engellenebilir.

Mevcut ayarı görmek için:

Get-ExecutionPolicy

ve:

Get-ExecutionPolicy -List

Güvenlik ayarlarını nedenini anlamadan sistem genelinde düşürmeyin.

Alternatif olarak aynı komutun .cmd sürümü veya farklı bir terminal kullanılabilir.

API bağlantı hatası

Kontrol edilmesi gerekenler:

internet bağlantısı,
API endpoint,
API anahtarı,
model adı,
sağlayıcı durumu,
proxy,
firewall,
rate limit,
kota.

Özellikle OpenAI uyumlu API kullanılırken endpoint ile model adının birbiriyle uyumlu olduğundan emin olun.

Yerel model cevap vermiyor

Kontrol edin:

Model gerçekten yüklenmiş mi?
Local server çalışıyor mu?
Port doğru mu?
API endpoint doğru mu?
Model adı doğru mu?
Yeterli RAM/VRAM mevcut mu?
Context değeri donanıma göre aşırı yüksek mi?
16. Sorun Giderme İçin Temel Kontrol

Aşağıdaki komutlar temel ortam bilgisini toplamak için kullanılabilir:

node --version
npm --version
git --version
qwen --version

Qwen Code sürümü --version seçeneğini desteklemiyorsa:

qwen --help

kullanılabilir.

Bir hata bildirirken mümkünse şu bilgileri ekleyin:

Windows sürümü:
Node.js sürümü:
npm sürümü:
Qwen Code sürümü:
Kullanılan model:
Kullanılan sağlayıcı:
Hata mesajı:
Sorunun oluştuğu komut:

API anahtarlarını hata raporlarına eklemeyin.

17. Güncelleme

Qwen Code npm üzerinden kurulmuşsa güncelleme yöntemi kullanılan paket ve sürüme bağlıdır.

Öncelikle mevcut sürümü kontrol edin:

qwen --version

Ardından resmi Qwen Code dokümantasyonundaki güncel yükseltme yöntemini uygulayın.

Büyük sürüm değişikliklerinde yapılandırma formatının değişebileceğini unutmayın.

18. Kaldırma

Kaldırma işlemi kullanılan kurulum yöntemine göre değişir.

npm ile global kurulum yapılmışsa ilgili npm paketinin kaldırma komutu kullanılabilir.

Paket adını doğrulamadan kaldırma komutu çalıştırmayın.

Kurulu global paketleri görmek için:

npm list -g --depth=0
19. Güvenlik Önerileri

Qwen Code gibi bilgisayar üzerinde işlem yapabilen yapay zekâ araçları kullanılırken:

önemli projelerde Git kullanın,
değişiklikleri commit etmeden önce inceleyin,
API anahtarlarını GitHub'a göndermeyin,
.env dosyalarını public repoya eklemeyin,
bilinmeyen MCP sunucularını doğrudan çalıştırmayın,
yapay zekânın önerdiği terminal komutlarını kontrol edin,
önemli dosyaların yedeğini tutun,
yönetici yetkisini yalnızca gerektiğinde kullanın,
internetten indirilen scriptleri incelemeden çalıştırmayın.
20. Önerilen Çalışma Düzeni

Yeni bir projede aşağıdaki yaklaşım kullanılabilir:

1. Projeyi Git ile yedekle
        ↓
2. Qwen Code'u proje klasöründe başlat
        ↓
3. Önce projeyi analiz ettir
        ↓
4. Yapılacak işi açıkça tanımla
        ↓
5. Değişiklikleri uygulat
        ↓
6. Testleri çalıştır
        ↓
7. git diff ile değişiklikleri incele
        ↓
8. Sonuç doğruysa commit oluştur

Bu yaklaşım özellikle büyük projelerde istenmeyen değişiklik riskini azaltır.

Sonraki Rehberler

Bu Türkçe dokümantasyon aşağıdaki bölümlerle genişletilecektir:

Windows ayrıntılı yapılandırma
Linux kurulumu
macOS kurulumu
Qwen Code temel kullanım
Qwen Code ileri seviye kullanım
LM Studio entegrasyonu
Ollama entegrasyonu
OpenAI uyumlu API yapılandırması
MCP kurulumu
MCP sunucu örnekleri
Agent ve subagent kullanımı
Türkçe kullanım örnekleri
Hata giderme rehberi
Güvenlik rehberi
Katkıda Bulunma

Hatalı veya güncelliğini kaybetmiş bir bilgi görürseniz Issue veya Pull Request açarak katkıda bulunabilirsiniz.

Bu projenin amacı Türkçe konuşan geliştiriciler için anlaşılır, güncel ve topluluk tarafından geliştirilebilen bir Qwen Code bilgi kaynağı oluşturmaktır.
