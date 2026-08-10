# Qwen Code Türkçe - Hata Çözme ve Sorun Giderme Rehberi
Bu rehber, Qwen Code kullanırken karşılaşılabilecek yaygın kurulum, bağlantı, model, API, terminal, MCP ve proje çalışma sorunlarını sistematik biçimde çözmek için hazırlanmıştır.
ÖNEMLİ: Bu depo Qwen ekibinin resmi projesi değildir. Bağımsız bir Türkçe topluluk dokümantasyonu çalışmasıdır.
## 1. İlk Kontrol
Bir hata oluştuğunda doğrudan program kaldırmak, paket silmek veya sistem ayarlarını değiştirmek yerine önce mevcut ortamı kontrol edin.
PowerShell açın ve aşağıdaki komutları tek tek çalıştırın:
node --version
npm --version
git --version
qwen --version
qwen --version desteklenmiyorsa:
qwen --help
Bu kontroller Node.js, npm, Git ve Qwen Code kurulumunun temel olarak çalışıp çalışmadığını gösterir.
## 2. qwen Komutu Bulunamıyor
Örnek hata:
'qwen' is not recognized as an internal or external command
veya:
The term 'qwen' is not recognized
Önce global npm paketlerini kontrol edin:
npm list -g --depth=0
npm global klasörünü görmek için:
npm prefix -g
Kurulum yeni yapıldıysa terminali tamamen kapatıp yeniden açın.
Sorun devam ediyorsa npm global klasörü PATH içerisinde olmayabilir.
## 3. Node.js Bulunamıyor
Kontrol:
node --version
Komut bulunamıyorsa Node.js kurulu olmayabilir veya PATH yapılandırması eksik olabilir.
Kurulumdan sonra terminali kapatıp yeniden açın.
Ardından tekrar kontrol edin:
node --version
npm --version
## 4. npm Bulunamıyor
Kontrol:
npm --version
Node.js çalışıyor fakat npm çalışmıyorsa Node.js kurulumu eksik veya bozuk olabilir.
PATH içerisinde Node.js klasörünün bulunduğunu kontrol edin.
## 5. Git Bulunamıyor
Kontrol:
git --version
Git kurulu değilse Git for Windows kurulmalıdır.
Kurulum tamamlandıktan sonra yeni bir terminal açın.
## 6. PowerShell Execution Policy Hatası
Bazı npm tabanlı komutlarda şu tür hata görülebilir:
running scripts is disabled on this system
Mevcut PowerShell politikasını görmek için:
Get-ExecutionPolicy
Ayrıntılı görünüm:
Get-ExecutionPolicy -List
Güvenlik politikasını nedenini anlamadan sistem genelinde devre dışı bırakmayın.
Bazı durumlarda aynı komutun .cmd sürümünü kullanmak veya Windows Terminal üzerinden farklı bir shell açmak daha güvenli olabilir.
## 7. Qwen Code Açılıyor Ama Model Cevap Vermiyor
Şu sırayla kontrol edin:
1. Qwen Code çalışıyor mu?
2. Model veya provider yapılandırılmış mı?
3. Model adı doğru mu?
4. API endpoint doğru mu?
5. API anahtarı gerekiyorsa doğru mu?
6. Model servisi erişilebilir mi?
7. Rate limit veya kota sorunu var mı?
Yerel model kullanıyorsanız model sunucusunun gerçekten çalıştığını da doğrulayın.
## 8. API Bağlantı Hatası
Örnek:
Connection refused
veya:
Unable to connect
Kontrol edin:
- API adresi
- Port
- İnternet bağlantısı
- Firewall
- Proxy
- VPN
- Model sunucusunun durumu
LM Studio gibi yerel OpenAI uyumlu bir sunucu için örnek kontrol:
Invoke-RestMethod http://localhost:1234/v1/models
Bu komut başarısızsa problem Qwen Code'dan önce API sunucusunda olabilir.
## 9. 401 Unauthorized
Örnek:
401 Unauthorized
Muhtemel nedenler:
- API key eksik
- API key yanlış
- Token geçersiz
- Authentication yöntemi yanlış
- Yanlış provider kullanılıyor
API anahtarlarını terminal çıktılarında veya GitHub repository içerisinde paylaşmayın.
## 10. 403 Forbidden
Örnek:
403 Forbidden
Muhtemel nedenler:
- Hesabın modele erişimi yok
- Provider izin vermiyor
- Bölgesel kısıtlama
- Eksik yetki
- Yanlış authentication yöntemi
## 11. 404 Not Found
Örnek:
404 Not Found
Yaygın nedenler:
- Yanlış API base URL
- Yanlış endpoint
- Yanlış model route
- /v1 eksik
- Gereksiz /v1 kullanımı
- Provider farklı endpoint yapısı kullanıyor
Kullandığınız sağlayıcının resmi dokümantasyonundaki endpoint ile karşılaştırın.
## 12. 429 Rate Limit
Örnek:
429 Too Many Requests
veya:
Rate limit exceeded
Muhtemel nedenler:
- Çok hızlı istek gönderiliyor
- Provider kota sınırı
- Günlük veya aylık limit
- Concurrency sınırı
Çözüm seçenekleri:
- Kısa süre beklemek
- Concurrency azaltmak
- Kota durumunu kontrol etmek
- Farklı model kullanmak
- Farklı provider kullanmak
## 13. Model Bulunamadı
Örnek:
model not found
Yerel OpenAI uyumlu sunucuda model listesini kontrol edin:
Invoke-RestMethod http://localhost:1234/v1/models
API'nin döndürdüğü gerçek model ID'sini kullanın.
Arayüzde görünen model adı ile API model ID'si aynı olmayabilir.
## 14. LM Studio Bağlantı Sorunu
Önce LM Studio içerisinde şunları doğrulayın:
- Model yüklü mü?
- Local Server açık mı?
- Doğru port kullanılıyor mu?
Sonra aşağıdaki komutu deneyin:
Invoke-RestMethod http://localhost:1234/v1/models
Yanıt geliyorsa LM Studio API katmanı çalışıyor demektir.
## 15. Yerel Model Çok Yavaş
Yaygın nedenler:
- Model donanıma göre fazla büyük
- Context çok yüksek
- VRAM yetersiz
- CPU offload fazla
- Ağır quantization
- Başka uygulamalar GPU kullanıyor
Deneyebileceğiniz yöntemler:
- Daha küçük model kullanmak
- Uygun quantization seçmek
- Context değerini azaltmak
- GPU kullanımını optimize etmek
- Arka plandaki ağır uygulamaları kapatmak
## 16. Context Length Hatası
Örnek:
context length exceeded
Çözüm seçenekleri:
- Görevi küçültün
- Gereksiz dosyaları context'ten çıkarın
- Konuşma geçmişini azaltın
- Daha uzun context destekleyen model kullanın
- Projeyi modüllere bölerek analiz ettirin
## 17. Model Aynı Cevabı Tekrar Ediyor
Model aynı yaklaşımı tekrar tekrar kullanıyorsa şu talimat verilebilir:
Aynı yöntemi tekrar etme.
Daha önce denenmiş yöntemleri belirle.
Yeni kanıt yoksa mevcut stratejiyi bırak.
Farklı bir root-cause hipotezi oluştur ve doğrula.
Aynı komutu veya aynı yöntemi yeniden kullanma.
## 18. Kod Yazılıyor Ama Sorun Çözülmüyor
Sadece kod değişikliği başarı değildir.
Şöyle görev verebilirsiniz:
Kod yazmak görevin tamamlandığı anlamına gelmez.
Değişiklikten sonra projeyi derle.
İlgili testleri çalıştır.
Uygulamayı gerçek senaryoda çalıştır.
Beklenen davranışı doğrula.
Hata devam ediyorsa görevi tamamlanmış sayma.
## 19. Yanlış Dosya Değiştiriliyor
Önce root cause analizi isteyin:
Problemi çözmeden önce ilgili kod akışını bul.
Problemin hangi dosya ve methoddan kaynaklandığını kanıtla.
Root cause belli olmadan dosya değiştirme.
Git üzerinden değişiklikleri kontrol edin:
git status
git diff
## 20. Çok Fazla Dosya Değiştirildi
Değişiklik özetini görmek için:
git diff --stat
Ayrıntılı değişiklikler:
git diff
Görev verirken şu kural kullanılabilir:
Sorunu çözmek için gerekli minimum güvenli değişikliği yap.
İlgisiz dosyaları değiştirme.
## 21. Build Başarısız
Projenin teknolojisine uygun build komutunu çalıştırın.
.NET:
dotnet build
Node.js:
npm run build
Java veya Maven:
mvn test
Gerçek hata çıktısını Qwen Code'a verin:
Build başarısız.
Gerçek build çıktısını analiz et.
Root cause'u belirle.
Tahmine dayalı değişiklik yapma.
Sorunu düzelt.
Build'i tekrar çalıştır.
## 22. Testler Başarısız
İlk gerçek root cause'u bulmak önemlidir.
Örnek görev:
Test sonuçlarını analiz et.
Başarısız testleri tek tek incele.
İlk gerçek root cause'u belirle.
Zincirleme başarısızlık varsa önce ana sebebi çöz.
Düzeltmeden sonra bütün ilgili testleri tekrar çalıştır.
## 23. Dependency Bulunamıyor
Kontrol edin:
- Paket gerçekten kurulu mu?
- Doğru proje klasöründe misiniz?
- Package lock mevcut mu?
- Virtual environment aktif mi?
- Paket adı doğru mu?
- Paket sürümü uyumlu mu?
Node.js:
npm install
Python:
pip install -r requirements.txt
Komutları çalıştırmadan önce projenin gerçek dependency yapısını kontrol edin.
## 24. Python ModuleNotFoundError
Kontrol:
python --version
pip --version
Kurulu paketleri görmek için:
pip list
Virtual environment kullanılıyorsa doğru environment'ın aktif olduğundan emin olun.
## 25. .NET SDK Bulunamıyor
Kontrol:
dotnet --info
Kurulu SDK sürümleri:
dotnet --list-sdks
Projede global.json varsa gerekli SDK sürümünü ayrıca kontrol edin.
## 26. Java veya JDK Sorunu
Kontrol:
java -version
javac -version
java çalışıyor ancak javac çalışmıyorsa yalnızca runtime kurulmuş olabilir.
JAVA_HOME ve PATH ayarlarını kontrol edin.
## 27. Maven Bulunamıyor
Kontrol:
mvn -version
Komut yoksa Maven kurulu olmayabilir veya PATH yapılandırması eksik olabilir.
## 28. Gradle Sorunu
Projede Gradle Wrapper varsa sistemdeki global Gradle yerine wrapper kullanılabilir.
Windows:
.\gradlew.bat tasks
Linux veya macOS:
./gradlew tasks
Wrapper, projenin ihtiyaç duyduğu Gradle sürümünün kullanılmasını kolaylaştırır.
## 29. MCP Sunucusu Görünmüyor
Qwen Code içerisinde:
/mcp
komutunu kullanın.
Kontrol edin:
- MCP config mevcut mu?
- Command doğru mu?
- Executable PATH içerisinde mi?
- MCP server gerçekten başlıyor mu?
- Transport doğru mu?
- Timeout oluşuyor mu?
## 30. MCP Sunucusu Var Ama Tool Görünmüyor
Bir MCP sunucusunun başlatılması tek başına yeterli değildir.
Gerçek doğrulama zinciri:
MCP Server başladı
Qwen Code bağlandı
Tool discovery gerçekleşti
Tool listesi geldi
Tool gerçek görevde çağrıldı
Beklenen sonuç üretildi
## 31. MCP Tool Çağrısı Başarısız
Kontrol edin:
- Tool parametreleri
- Required alanlar
- Authentication
- Path izinleri
- Timeout
- External dependency
- Server error çıktısı
Gerçek MCP tool error mesajını inceleyin.
## 32. Git Değişiklikleri Kayboldu
Kontrol:
git status
Commit geçmişi:
git log --oneline
Önemli çalışma noktalarında commit almak veri kaybı riskini azaltır.
## 33. Yanlış Değişiklikleri Geri Alma
Önce:
git diff
ile değişiklikleri inceleyin.
Ne yaptığınızı anlamadan destructive komutları kullanmayın.
Özellikle aşağıdaki komutlara dikkat edin:
git reset --hard
git clean -fd
Bu komutlar geri alınması zor veri kaybına yol açabilir.
## 34. API Anahtarı GitHub'a Eklendi
Bir secret public repository'ye girdiyse artık gizli kabul edilmemelidir.
İlk yapılması gerekenler:
1. API anahtarını iptal edin.
2. Yeni anahtar oluşturun.
3. Repository geçmişinden secret'ı temizleyin.
4. .gitignore yapılandırmasını düzeltin.
Sadece dosyayı silmek anahtarın Git geçmişinden silindiği anlamına gelmez.
## 35. Qwen Code Çok Fazla Terminal Komutu Çalıştırıyor
Şu sınırlar verilebilir:
Önce analiz yap.
Gerekli olmadığı sürece sistem genelinde değişiklik yapma.
Yalnız proje klasörü içinde çalış.
Destructive komut kullanma.
Her terminal işlemi görev hedefiyle doğrudan ilişkili olsun.
## 36. Ajan Döngüye Girdi
Belirtiler:
- Aynı komut tekrar çalışıyor
- Aynı dosyalar tekrar okunuyor
- Aynı hata yeniden açıklanıyor
- Yeni kanıt oluşmuyor
Örnek müdahale:
Durumu yeniden değerlendir.
Son adımlarda üretilen yeni kanıtları belirle.
Yeni kanıt yoksa mevcut stratejiyi bırak.
Aynı komutu tekrar kullanma.
Farklı bir root-cause hipotezi oluştur ve doğrula.
## 37. Ajan Çok Uzun Süre Çalışıyor
Uzun çalışma her zaman hata anlamına gelmez.
Ancak process çalışıyor olması gerçek ilerleme olduğu anlamına gelmez.
Şunları kontrol edin:
- Yeni artifact oluşuyor mu?
- Build ilerliyor mu?
- Test sonucu değişiyor mu?
- Yeni hata veya kanıt elde ediliyor mu?
- Yalnızca aynı loglar mı tekrar ediyor?
## 38. Hata Bildirirken Verilmesi Faydalı Bilgiler
İyi bir hata raporunda şu bilgiler bulunabilir:
İşletim sistemi:
Qwen Code sürümü:
Node.js sürümü:
npm sürümü:
Model:
Provider:
API endpoint türü:
Çalıştırılan görev:
Beklenen davranış:
Gerçek davranış:
Tam hata mesajı:
Tekrar üretme adımları:
API key, token veya password eklemeyin.
## 39. Sistematik Hata Çözme Akışı
Hata oluştu -> Hata çıktısını kaydet -> Ortamı doğrula -> Hatayı tekrar üret -> Root cause belirle -> En küçük güvenli çözümü uygula -> Aynı testi tekrar çalıştır -> Regression kontrolü -> Sonucu doğrula
## 40. Genel Hata Çözme Görev Örneği
Bu problemi çöz.
Tahmin ederek kod değiştirmeye başlama.
Önce gerçek hata çıktısını analiz et.
İlgili kod akışını bul.
Environment ve dependency durumunu kontrol et.
Root cause'u kanıtla.
Daha önce başarısız olan yöntemleri tekrar etme.
Güncel bilgi gerekiyorsa resmi kaynakları araştır.
En uygun çözümü uygula.
Build çalıştır.
İlgili testleri çalıştır.
Gerçek runtime senaryosunu doğrula.
Regression kontrolü yap.
Görevi yalnız sorun gerçekten çözüldüğünde tamamlanmış kabul et.
## 41. Güvenlik Kuralları
Sorun gidermeye çalışırken aşağıdaki işlemleri nedenini anlamadan kullanmayın:
- Disk silme
- Recursive klasör silme
- Registry temizleme
- Firewall kapatma
- Antivirüs kapatma
- Credential silme
- Production database sıfırlama
- git reset --hard
- git clean -fd
Bir hatayı çözmek için sistem güvenliğini tamamen devre dışı bırakmak genellikle doğru çözüm değildir.
## 42. Doğrulama Prensibi
Bir yapay zeka ajanının "Tamamlandı", "Başarılı", "PASS" veya "Ready" demesi tek başına kanıt değildir.
Mümkün olduğunda sonucu aşağıdakilerle doğrulayın:
- Gerçek build sonucu
- Gerçek test sonucu
- Gerçek runtime sonucu
- Oluşturulan dosya veya artifact
- Beklenen kullanıcı davranışının gerçekleşmesi
## Sonuç
Sorun giderirken en önemli prensip şudur:
Hata mesajını bastırmak çözüm değildir.
Gerçek root cause'u ortadan kaldırmak çözümdür.
Qwen Code veya kullandığınız model bir işlemin başarılı olduğunu söylese bile mümkün olduğunda sonucu gerçek build, test, runtime ve dosya çıktılarıyla doğrulayın.
