# Qwen Code Türkçe - MCP Kullanım Rehberi
Bu rehber, Qwen Code ile Model Context Protocol (MCP) kullanımını Türkçe olarak açıklamak için hazırlanmıştır.
Bu depo Qwen ekibinin resmi projesi değildir. Bağımsız bir Türkçe topluluk dokümantasyonu çalışmasıdır.
## 1. MCP Nedir?
MCP, yapay zeka uygulamalarının harici araçlar ve veri kaynaklarıyla standart bir yapı üzerinden iletişim kurmasını sağlayan açık bir protokoldür.
Bir MCP sunucusu yapay zeka istemcisine çeşitli yetenekler sağlayabilir.
Örnekler:
- Dosya sistemi erişimi
- Veritabanı sorguları
- GitHub işlemleri
- Web servisleri
- Geliştirici araçları
- Özel şirket sistemleri
- Yerel otomasyon araçları
Temel yapı:
Qwen Code -> MCP Client -> MCP Server -> Tool veya Kaynak
## 2. MCP Neden Kullanılır?
Normal bir dil modeli yalnızca kendisine verilen bağlam üzerinden cevap üretir.
MCP sayesinde desteklenen istemciler harici yeteneklere bağlanabilir.
Örneğin bir MCP sunucusu:
- dosya okuyabilir
- belirli bir API'ye bağlanabilir
- veritabanından bilgi alabilir
- geliştirme araçlarıyla iletişim kurabilir
Bu özellikler kullanılan MCP sunucusuna ve verilen izinlere bağlıdır.
## 3. MCP Server Nedir?
MCP Server belirli araçları veya kaynakları MCP protokolü üzerinden istemciye sunan programdır.
Örneğin teorik bir dosya sistemi MCP sunucusu şu araçları sağlayabilir:
read_file
write_file
list_directory
search_files
Her MCP sunucusunun sunduğu araçlar farklı olabilir.
## 4. MCP Client Nedir?
MCP Client, MCP sunucularına bağlanan taraftır.
Qwen Code'un MCP destekleyen sürümlerinde Qwen Code istemci rolünü üstlenebilir.
MCP Client sunucudan kullanılabilir araçları öğrenir ve uygun görevlerde bunları modele sunabilir.
## 5. MCP Tool Nedir?
Tool, MCP sunucusunun dış dünyada gerçekleştirebildiği belirli bir işlemdir.
Örneğin:
read_file
Bir dosyanın içeriğini okuyabilir.
search_repository
Bir repository içerisinde arama yapabilir.
query_database
Bir veritabanında sorgu gerçekleştirebilir.
Tool isimleri ve parametreleri MCP sunucusuna göre değişir.
## 6. MCP Resource Nedir?
MCP yalnızca araç çağırmak için kullanılmaz.
Sunucular modele okunabilir kaynaklar da sunabilir.
Örneğin:
- doküman
- yapılandırma
- veritabanı içeriği
- proje bilgisi
- uygulama verisi
Tool işlem gerçekleştirebilirken resource genellikle bağlam sağlamak amacıyla kullanılır.
## 7. MCP Prompt Kavramı
MCP sunucuları yeniden kullanılabilir prompt şablonları da sağlayabilir.
Bunlar belirli görevler için önceden hazırlanmış çalışma kalıpları olabilir.
Bir MCP sunucusunun tools, resources ve prompts özelliklerinin tamamını desteklemesi zorunlu değildir.
## 8. MCP Transport
MCP istemcisi ile sunucusu arasında iletişim için farklı transport yöntemleri kullanılabilir.
Kullanılan yöntem MCP sunucusuna ve istemci desteğine bağlıdır.
Yerel MCP sunucuları genellikle istemci tarafından bir process olarak başlatılabilir.
Uzak MCP servislerinde ağ tabanlı transport kullanılabilir.
Güncel transport seçenekleri için MCP ve Qwen Code resmi dokümantasyonunu kontrol edin.
## 9. Qwen Code İçerisinde MCP Kontrolü
Qwen Code'un güncel sürümünde kullanılabilir MCP komutlarını görmek için yardım komutlarını kontrol edin.
MCP yapılandırması yaptıktan sonra Qwen Code içerisinde:
 /mcp
komutu destekleniyorsa bağlı MCP sunucularını ve durumlarını kontrol etmek için kullanılabilir.
Komutlar Qwen Code sürümüne göre değişebileceğinden güncel resmi dokümantasyon esas alınmalıdır.
## 10. MCP Server Kurmadan Önce
Bir MCP sunucusunu sisteminize eklemeden önce şu bilgileri kontrol edin:
- Projenin resmi kaynağı nedir?
- Repository güvenilir mi?
- Hangi izinleri istiyor?
- Dosya sistemine erişiyor mu?
- İnternete bağlanıyor mu?
- Shell komutu çalıştırabiliyor mu?
- Credential kullanıyor mu?
- Son güncelleme tarihi nedir?
- Kurulum komutu ne yapıyor?
MCP sunucuları gerçek sistem yetkilerine sahip olabileceğinden rastgele kaynaklardan kurulum yapılmamalıdır.
## 11. Node.js Tabanlı MCP Server
Bazı MCP sunucuları Node.js tabanlı olabilir.
Önce ortamı kontrol edin:
node --version
npm --version
Bir MCP projesinin README dosyasında npx ile çalıştırma örneği bulunabilir.
Ancak internette bulunan herhangi bir npx komutunu doğrulamadan çalıştırmayın.
Önce paketin resmi kaynağını kontrol edin.
## 12. Python Tabanlı MCP Server
Bazı MCP sunucuları Python kullanabilir.
Kontrol:
python --version
pip --version
Projeye göre virtual environment kullanılması önerilebilir.
Kurulum yöntemi ilgili MCP sunucusunun resmi dokümantasyonundan alınmalıdır.
## 13. MCP Yapılandırmasının Temel Mantığı
Bir MCP sunucusunun yapılandırmasında genellikle şu tür bilgiler bulunabilir:
- sunucu adı
- çalıştırılacak command
- command arguments
- environment variables
- transport bilgisi
Gerçek alan isimleri Qwen Code sürümüne göre değişebilir.
Bu nedenle örnek bir yapılandırmayı doğrudan kopyalamadan önce güncel Qwen Code dokümantasyonunu kontrol edin.
## 14. Environment Variables
Bazı MCP sunucuları API anahtarı veya başka yapılandırmaları environment variable üzerinden alabilir.
Örneğin kavramsal olarak:
SERVICE_API_KEY
SERVICE_URL
ACCESS_TOKEN
Gerçek değişken isimleri kullanılan MCP sunucusunun dokümantasyonundan alınmalıdır.
Secret değerlerini public GitHub repository içerisinde paylaşmayın.
## 15. MCP Server Çalışıyor Ama Qwen Code Görmüyor
Şunları kontrol edin:
- yapılandırma dosyası doğru yerde mi?
- JSON veya yapılandırma syntax'ı geçerli mi?
- command gerçekten çalışıyor mu?
- executable PATH içerisinde mi?
- arguments doğru mu?
- gerekli environment variables mevcut mu?
- server başlangıç sırasında hata veriyor mu?
- Qwen Code yeniden başlatılmalı mı?
## 16. Server Başlıyor Ama Tool Görünmüyor
Server process'inin çalışması entegrasyonun tamamlandığı anlamına gelmez.
Gerçek zincir:
Server process başladı -> MCP bağlantısı kuruldu -> Capability discovery gerçekleşti -> Tool listesi alındı -> Tool modele sunuldu -> Tool gerçek görevde çağrıldı -> Sonuç istemciye döndü
Bu zincirin herhangi bir noktasında sorun oluşabilir.
## 17. Tool Discovery
MCP bağlantısı kurulduktan sonra istemci sunucunun sunduğu yetenekleri öğrenir.
Örneğin sunucu şu araçları sağlayabilir:
search
read
write
fetch
Gerçek araç isimleri sunucuya bağlıdır.
Qwen Code içerisinde MCP durum ekranı destekleniyorsa keşfedilen araçları buradan kontrol edebilirsiniz.
## 18. Tool Parametre Hatası
Tool çağrılırken sunucunun beklediği parametre yapısı kullanılmalıdır.
Örneğin bir araç:
path
parametresi beklerken farklı alan gönderilirse çağrı başarısız olabilir.
Kontrol edin:
- required parametreler
- veri tipleri
- path formatı
- enum değerleri
- authentication
- tool schema
## 19. Permission Hatası
MCP sunucusu bir dosyaya veya sisteme erişemiyorsa permission hatası oluşabilir.
Örneğin:
Permission denied
Access denied
Bu durumda uygulamayı doğrudan yönetici olarak çalıştırmak yerine önce hangi kaynağın hangi izne ihtiyaç duyduğunu belirleyin.
Gereksiz yüksek yetki vermeyin.
## 20. Timeout Hatası
Bir MCP tool işlemi uzun sürerse timeout oluşabilir.
Muhtemel nedenler:
- harici servis yavaş
- internet bağlantısı sorunlu
- tool takıldı
- işlem çok büyük
- server cevap vermiyor
- timeout değeri düşük
Önce MCP server loglarını kontrol edin.
## 21. MCP Server Sürekli Kapanıyor
Server başlatıldıktan hemen sonra kapanıyorsa terminal üzerinden doğrudan çalıştırarak gerçek hata çıktısını görmek faydalı olabilir.
Kontrol edin:
- dependency eksikliği
- yanlış command
- yanlış argument
- environment variable eksikliği
- port çakışması
- runtime sürümü
- configuration hatası
## 22. Birden Fazla MCP Server
Qwen Code yapılandırması destekliyorsa farklı görevler için birden fazla MCP sunucusu kullanılabilir.
Örneğin kavramsal yapı:
Qwen Code -> Filesystem MCP
Qwen Code -> GitHub MCP
Qwen Code -> Database MCP
Qwen Code -> Custom MCP
Her sunucu yalnızca ihtiyaç duyduğu yetkilere sahip olmalıdır.
## 23. MCP ve Agent Sistemleri
MCP, agent sistemleri için önemli bir araç katmanı sağlayabilir.
Örneğin:
Agent -> karar verir -> MCP Tool seçer -> Tool çalışır -> sonuç Agent'a döner -> Agent sonucu değerlendirir
Ancak MCP kendi başına tam bir agent orchestration sistemi değildir.
Görev planlama, agent seçimi, memory, validation ve recovery gibi özellikler ayrı mimari katmanlar gerektirebilir.
## 24. Tool Calling ile MCP Arasındaki Fark
Tool calling modelin yapılandırılmış bir araç çağrısı üretme yeteneğidir.
MCP ise araçların ve kaynakların istemcilere standart biçimde sunulmasını sağlayan protokoldür.
Basitleştirilmiş yapı:
Model -> Tool Calling -> MCP Client -> MCP Server -> Gerçek Tool
Her model tool calling konusunda aynı başarı seviyesine sahip değildir.
## 25. Yerel Model ve MCP
Yerel bir model MCP araçlarıyla kullanılacaksa yalnızca normal sohbet kalitesi yeterli olmayabilir.
Modelin şu yetenekleri önemlidir:
- tool calling
- instruction following
- structured output
- tool sonucunu yorumlama
- çok adımlı görev takibi
Model tool calling konusunda zayıfsa MCP sunucusu doğru çalışsa bile agent davranışı kötü olabilir.
## 26. MCP Güvenlik Riski
Bir MCP sunucusu sahip olduğu yetkiye göre gerçek sistem üzerinde işlem yapabilir.
Örneğin:
- dosya okuyabilir
- dosya yazabilir
- repository değiştirebilir
- API çağrısı yapabilir
- veritabanına erişebilir
- shell çalıştırabilir
Bu nedenle MCP sunucularını normal yazılım dependency'leri kadar dikkatli değerlendirin.
## 27. Least Privilege
Bir MCP sunucusuna yalnızca ihtiyacı olan yetki verilmelidir.
Örneğin yalnız belirli proje klasörünü okuması gereken bir MCP sunucusuna bütün diske yazma yetkisi vermek gereksizdir.
Temel prensip:
İhtiyaç duyulan minimum yetki + minimum erişim alanı
## 28. Secret Güvenliği
MCP yapılandırmalarında kullanılan:
- API key
- access token
- password
- private key
- database credential
gibi bilgileri repository içerisinde düz metin olarak saklamayın.
Environment variable veya ilgili platformun güvenli secret yönetim yöntemlerini kullanın.
## 29. Güvenilmeyen İçerik
Web veya harici kaynaklara erişebilen MCP araçları güvenilmeyen içerik getirebilir.
Bir web sayfasında modele yönelik talimat bulunması bu talimatın güvenilir olduğu anlamına gelmez.
Harici içerik veri olarak değerlendirilmelidir.
Sistem veya kullanıcı talimatlarının yerine geçmemelidir.
## 30. MCP Sorun Giderme Sırası
Sorun yaşadığınızda şu sırayı kullanabilirsiniz:
1. Qwen Code çalışıyor mu?
2. MCP config okunuyor mu?
3. MCP server command çalışıyor mu?
4. Server process açık kalıyor mu?
5. Client-server bağlantısı kuruluyor mu?
6. Capability discovery gerçekleşiyor mu?
7. Tool listesi geliyor mu?
8. Tool çağrısı oluşturuluyor mu?
9. Tool gerçek işlemi gerçekleştiriyor mu?
10. Sonuç Qwen Code'a geri dönüyor mu?
Bu sıra problemin hangi katmanda olduğunu bulmayı kolaylaştırır.
## 31. MCP Testi
Yeni bir MCP server kurulduğunda yalnızca "connected" mesajıyla yetinmeyin.
Gerçek test:
Server Connected -> Tool Discovered -> Tool Called -> Real Operation Executed -> Expected Artifact Produced -> Result Verified
Örneğin dosya okuma aracı test ediliyorsa gerçekten test dosyasının doğru içeriğini okuyabildiğini doğrulayın.
## 32. Log Kullanımı
MCP problemi araştırırken mümkünse hem istemci hem sunucu loglarını inceleyin.
Önemli bilgiler:
- process exit code
- stderr
- connection error
- tool request
- tool response
- timeout
- schema validation error
- authentication error
Sadece son kullanıcıya gösterilen genel hata mesajına güvenmeyin.
## 33. Güncelleme Sonrası MCP Bozuldu
Qwen Code veya MCP server güncellendikten sonra entegrasyon bozulursa şunları karşılaştırın:
- eski sürüm
- yeni sürüm
- config schema değişiklikleri
- transport değişiklikleri
- kaldırılan seçenekler
- yeni authentication gereksinimleri
- dependency sürümleri
Resmi changelog ve migration belgelerini kontrol edin.
## 34. Genel MCP Hata Çözme Görevi
Bir yapay zeka ajanına MCP problemi çözdürürken şu yaklaşım kullanılabilir:
MCP problemini tahmin ederek düzeltmeye çalışma.
Önce Qwen Code sürümünü belirle.
MCP yapılandırmasını kontrol et.
Server process'ini gerçek ortamda çalıştır.
stderr ve exit code'u incele.
Client-server bağlantısını doğrula.
Capability discovery sonucunu kontrol et.
Tool schema'yı incele.
Gerçek bir tool çağrısı çalıştır.
Beklenen sonucu doğrula.
Problem devam ediyorsa root cause belirlenmeden config değiştirme.
## 35. Başarı Kriteri
MCP entegrasyonu ancak aşağıdaki zincir gerçek ortamda çalıştığında başarılı kabul edilmelidir:
Qwen Code çalışıyor -> MCP Server bağlandı -> Tool discovery başarılı -> Tool çağrıldı -> Gerçek işlem yapıldı -> Sonuç döndü -> Beklenen çıktı doğrulandı
Sadece server'ın "running" görünmesi yeterli değildir.
## Sonuç
MCP, Qwen Code gibi yapay zeka tabanlı geliştirme araçlarının harici sistemlerle standart biçimde iletişim kurmasını sağlayan güçlü bir altyapıdır.
Ancak güçlü araç erişimi beraberinde güvenlik sorumluluğu getirir.
Her MCP sunucusunu kaynağı, izinleri, erişim alanı ve gerçek çalışma davranışı açısından doğrulayın.
