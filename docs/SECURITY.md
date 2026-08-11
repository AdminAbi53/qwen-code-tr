# Güvenlik Politikası
Bu belge Qwen Code Türkçe topluluk dokümantasyonu deposunun güvenlik politikasını açıklar.
## Güvenlik Açığı Bildirme
Bu repository içerisinde güvenlikle ilgili bir sorun fark ederseniz hassas ayrıntıları herkese açık GitHub Issue içerisinde paylaşmayın.
Özellikle aşağıdaki bilgileri public issue içerisine eklemeyin:
- API anahtarları
- Access token
- Şifreler
- Private key
- Authentication cookie
- Kişisel bilgiler
- Özel repository içerikleri
- Güvenlik açığının kötüye kullanılmasını kolaylaştıracak hassas bilgiler
Mümkün olduğunda GitHub'ın özel güvenlik bildirimi özelliklerini kullanın.
## Dokümantasyon Hataları
Normal dokümantasyon hataları güvenlik açığı değildir.
Aşağıdaki konular normal GitHub Issue olarak bildirilebilir:
- Yazım hataları
- Bozuk bağlantılar
- Güncelliğini kaybetmiş komutlar
- Eksik açıklamalar
- Yanlış kurulum adımları
- Qwen Code sürüm değişiklikleri
## API Anahtarları
Gerçek API anahtarlarını repository içerisinde paylaşmayın.
Örnek olarak yalnız sahte değerler kullanılmalıdır:
YOUR_API_KEY
YOUR_TOKEN
example-key
Bir API anahtarı yanlışlıkla GitHub'a gönderildiyse yalnız dosyadan silmek yeterli değildir.
İlgili anahtarı derhal iptal edin ve yenisini oluşturun.
Anahtarın Git geçmişinde kalmış olabileceğini unutmayın.
## Environment Variables
Secret bilgilerin doğrudan kaynak kod içerisine yazılması yerine mümkün olduğunda environment variable veya uygun secret yönetim sistemi kullanılmalıdır.
## MCP Güvenliği
MCP sunucuları gerçek sistem kaynaklarına erişebilir.
Bir MCP sunucusunu kullanmadan önce:
- resmi kaynağını kontrol edin
- repository adresini doğrulayın
- istediği izinleri inceleyin
- kurulum komutlarını okuyun
- dosya sistemi erişimini kontrol edin
- shell erişimini kontrol edin
- ağ erişimini kontrol edin
- kullandığı credential bilgilerini kontrol edin
Tanımadığınız MCP sunucularına gereksiz sistem yetkileri vermeyin.
## Yerel Agent Güvenliği
Coding agent sistemleri terminal ve dosya araçlarına erişebilir.
Bu nedenle agent teorik olarak:
- dosya oluşturabilir
- dosya değiştirebilir
- dosya silebilir
- terminal komutu çalıştırabilir
- dependency kurabilir
- repository değiştirebilir
Önemli projelerde Git veya başka bir sürüm kontrol sistemi kullanılması önerilir.
## Destructive Komutlar
İnternette bulunan komutları ne yaptığını anlamadan çalıştırmayın.
Özellikle aşağıdaki tür işlemler dikkat gerektirir:
- recursive dosya silme
- disk biçimlendirme
- registry değişiklikleri
- firewall kapatma
- antivirüs kapatma
- credential silme
- git reset --hard
- git clean -fd
- yönetici yetkisi isteyen bilinmeyen scriptler
## Üçüncü Taraf Paketler
npm, pip, NuGet veya diğer paket yöneticilerinden yüklenen paketler üçüncü taraf kod çalıştırabilir.
Paket kullanmadan önce mümkün olduğunda:
- resmi kaynağı kontrol edin
- paket adını doğrulayın
- repository bağlantısını kontrol edin
- bakım durumunu inceleyin
- dependency zincirini değerlendirin
Benzer isimli sahte paketlere karşı dikkatli olun.
## Yerel Model Sunucuları
LM Studio, Ollama veya başka bir yerel model sunucusu kullanırken ağ yapılandırmasını kontrol edin.
Yalnız kendi bilgisayarınızdan erişilmesi gereken bir API'yi gereksiz şekilde genel ağa açmayın.
## Uzak API Sağlayıcıları
Bir bulut model sağlayıcısına gönderilen içerik yerel bilgisayarınızdan dışarı çıkabilir.
Hassas projelerde sağlayıcının:
- gizlilik politikasını
- veri saklama politikasını
- API kullanım koşullarını
- kurumsal güvenlik seçeneklerini
inceleyin.
## Prompt Injection
Web, dosya, repository veya harici servislerden gelen içerikler güvenilmeyen veri içerebilir.
Harici içerik içerisinde modele yönelik bir talimat bulunması bu talimatın güvenilir olduğu anlamına gelmez.
Agent sistemleri güvenilmeyen içeriği kullanıcı veya sistem talimatlarının yerine koymamalıdır.
## Least Privilege
Araçlara yalnız ihtiyaç duydukları minimum yetki verilmelidir.
Örneğin yalnız belirli bir proje klasörünü okuması gereken bir aracın bütün diske yazma yetkisine sahip olması gerekmeyebilir.
Temel prensip:
Minimum gerekli yetki + Minimum gerekli erişim alanı
## Log Güvenliği
Debug veya hata logları hassas bilgiler içerebilir.
Log paylaşmadan önce şu bilgileri kontrol edin:
- API key
- token
- kullanıcı adı
- e-posta
- dosya yollarındaki kişisel bilgiler
- özel kaynak kod
- authentication header
Gerekli hassas alanları paylaşmadan önce temizleyin.
## Katkıda Bulunanlar İçin
Pull Request göndermeden önce:
- gerçek secret bulunmadığını kontrol edin
- örnek credential değerlerinin sahte olduğundan emin olun
- tehlikeli komutları açıklamasız eklemeyin
- üçüncü taraf kurulum komutlarının kaynağını doğrulayın
- güvenlik önlemlerini gereksiz şekilde devre dışı bırakmayın
## Sorumlu Açıklama
Potansiyel bir güvenlik problemi bulduğunuzda sorunun düzeltilmesine fırsat vermeden kötüye kullanım ayrıntılarını herkese açık biçimde yayınlamayın.
Güvenlik araştırmaları yalnız size ait veya test etme izniniz bulunan sistemlerde gerçekleştirilmelidir.
## Desteklenen Sürümler
Bu repository ağırlıklı olarak dokümantasyon içerdiğinden bilgiler mümkün olduğunca Qwen Code'un güncel sürümüne göre tutulmaya çalışılır.
Eski Qwen Code, LM Studio, Ollama, Node.js veya diğer dependency sürümlerinde aynı adımların çalışacağı garanti edilmez.
Bir komutu uygulamadan önce ilgili yazılımın güncel resmi dokümantasyonunu kontrol edin.
## Güvenlik Sorumluluğu
Bu repository eğitim ve topluluk dokümantasyonu amacıyla hazırlanmıştır.
Kullanıcılar çalıştırdıkları komutları, kurdukları paketleri ve verdikleri sistem izinlerini kendi ortamlarına göre değerlendirmelidir.
## Sonuç
Temel güvenlik prensibi:
Kaynağı doğrula -> Yetkiyi kontrol et -> Secret paylaşma -> Komutu anlamadan çalıştırma -> Sonucu doğrula
