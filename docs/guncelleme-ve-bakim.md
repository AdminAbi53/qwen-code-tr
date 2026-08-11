# Qwen Code Türkçe - Güncelleme ve Bakım Rehberi
Bu rehber, Qwen Code Türkçe dokümantasyonunu ve kullanılan araçları zaman içinde güncel tutmak için temel bakım yaklaşımını açıklar.
Bu depo Qwen ekibinin resmi projesi değildir. Bağımsız bir Türkçe topluluk dokümantasyonu çalışmasıdır.
## 1. Neden Güncel Tutmak Gerekir?
Qwen Code, model sağlayıcıları, MCP araçları, Node.js, LM Studio, Ollama ve diğer bağımlılıklar zaman içinde değişebilir.
Bu nedenle bugün çalışan bir komut veya yapılandırma ileride eski olabilir.
## 2. Resmi Kaynakları Takip Edin
Güncelleme yaparken öncelikle şu kaynakları kontrol edin:
Qwen Code resmi repository
https://github.com/QwenLM/qwen-code
Qwen Code resmi dokümantasyonu
https://qwenlm.github.io/qwen-code-docs/
İlgili teknoloji veya aracın resmi sitesi ve release notes sayfaları
## 3. Sürüm Değişikliklerini Kontrol Edin
Bir rehberi güncellemeden önce:
- eski sürüm
- yeni sürüm
- kaldırılan özellikler
- değişen komutlar
- yeni dependency gereksinimleri
- migration notları
karşılaştırılmalıdır.
## 4. Eski Komutları Güncel Bilgi Gibi Sunmayın
Bir komut artık çalışmıyorsa yalnız eski komutu silmek yerine neden değiştiğini ve yeni yöntemi doğrulayın.
## 5. Qwen Code Sürümünü Kontrol Etme
Desteklenen sürümlerde:
qwen --version
veya:
qwen --help
kullanılabilir.
Gerçek güncel komutları resmi kaynaklardan doğrulayın.
## 6. Node.js Güncelliği
Kontrol:
node --version
npm --version
Qwen Code'un ihtiyaç duyduğu Node.js sürümü zaman içinde değişebilir.
## 7. LM Studio Güncelliği
LM Studio güncellendikten sonra:
- local server
- port
- API davranışı
- model yükleme
- OpenAI uyumluluğu
yeniden test edilmelidir.
## 8. Ollama Güncelliği
Kontrol:
ollama --version
Yeni sürüm sonrası:
- API endpoint
- model davranışı
- model isimleri
- OpenAI uyumluluğu
kontrol edilmelidir.
## 9. MCP Güncellemeleri
MCP server veya client güncellendiğinde:
- transport
- config schema
- tool isimleri
- authentication
- timeout
- permission
değişiklikleri olabilir.
## 10. Model Güncellemeleri
Yeni model sürümü çıktığında eski model ile aynı davranışın korunacağı varsayılmamalıdır.
Özellikle:
- tool calling
- structured output
- context
- coding kalitesi
- Türkçe anlama
yeniden test edilmelidir.
## 11. Dokümantasyon Kontrol Listesi
Bir belgeyi güncellerken:
1. Kaynak güncel mi?
2. Komut hâlâ çalışıyor mu?
3. URL hâlâ geçerli mi?
4. Sürüm notu değişti mi?
5. Örnek çıktı hâlâ doğru mu?
6. Güvenlik tavsiyesi güncel mi?
7. Yeni kullanıcı için anlaşılır mı?
## 12. Bozuk Link Kontrolü
Repository içindeki bağlantıları düzenli aralıklarla kontrol edin.
Özellikle:
- resmi dokümantasyon
- GitHub repository
- LM Studio
- Ollama
- Node.js
- Git
bağlantılarının çalıştığından emin olun.
## 13. Issue Kullanımı
Güncelliğini kaybetmiş bilgi bulunursa GitHub Issue açılabilir.
Örnek başlık:
Update outdated Qwen Code installation command
Issue içerisinde:
- ilgili dosya
- eski bilgi
- güncel resmi kaynak
- önerilen değişiklik
belirtilebilir.
## 14. Pull Request Kullanımı
Bir dokümantasyon değişikliği Pull Request ile gönderilebilir.
Açıklamada:
- ne değişti
- neden değişti
- hangi kaynakla doğrulandı
- hangi ortamda test edildi
bilgileri faydalıdır.
## 15. Küçük ve Anlamlı Commitler
Her değişiklik için gereksiz büyük commit oluşturmak yerine anlamlı commitler tercih edilebilir.
Örnek:
Update Ollama API section
Fix broken MCP documentation links
Add Windows troubleshooting example
## 16. Commit Mesajları
İyi commit mesajı yapılan değişikliği açıklar.
Örnek:
Add Turkish Qwen Code memory guide
Update LM Studio local API instructions
Fix outdated Node.js requirement note
## 17. Release Kullanımı
Repository belirli bir olgunluğa ulaştığında GitHub Release oluşturulabilir.
Örnek sürüm:
v0.1.0
İlk sürüm açıklamasında mevcut rehberler listelenebilir.
## 18. Changelog
Proje büyüdükçe CHANGELOG.md dosyası eklenebilir.
Örnek:
Added
Changed
Fixed
Removed
başlıkları altında sürüm değişiklikleri tutulabilir.
## 19. README Güncelliği
Yeni belge eklendiğinde README içerisindeki içerik bağlantıları da güncellenmelidir.
Dosya repository'de olup README'de görünmüyorsa kullanıcı bulmakta zorlanabilir.
## 20. Dosya İsimleri
Yeni dokümanlarda kısa ve anlaşılır Türkçe dosya isimleri kullanın.
Örnek:
docs/model-secimi.md
docs/windows-ipuclari.md
docs/hata-cozumleri.md
## 21. Tekrarlanan İçerikten Kaçının
Aynı bilgiyi birçok dosyada uzun şekilde tekrar etmek bakım maliyetini artırır.
Ana konu tek belgede ayrıntılı tutulup diğer belgelerden referans verilebilir.
## 22. Kaynak Gösterme
Teknik iddialar önemliyse ilgili resmi kaynak eklenmelidir.
Özellikle:
- komut
- sürüm
- yapılandırma
- API endpoint
- güvenlik davranışı
konularında kaynak faydalıdır.
## 23. Güncel Olmayan İçerik
Bir bölüm henüz doğrulanmadıysa kesin bilgi gibi sunulmamalıdır.
Örnek:
Bu özellik kullanılan Qwen Code sürümüne göre değişebilir.
Güncel resmi dokümantasyonu kontrol edin.
## 24. Gerçek Test
Dokümantasyondaki önemli bir komut mümkünse gerçek ortamda test edilmelidir.
Örnek:
Kurulum komutu -> gerçek kurulum
API endpoint -> gerçek bağlantı
MCP config -> gerçek tool discovery
## 25. Test Edilmemiş Bilgi
Test edilmemiş içerik varsa bunu açıkça belirtmek daha güvenlidir.
Örnek:
Bu bölüm kavramsal açıklamadır. Gerçek yapılandırma kullanılan sürüme göre doğrulanmalıdır.
## 26. Güvenlik Güncellemeleri
Bir dependency veya araç için güvenlik problemi duyurulursa ilgili rehber gözden geçirilmelidir.
Eski ve riskli kurulum yöntemi varsa güncellenmelidir.
## 27. Secret Kontrolü
Her commit öncesi şu bilgilerin yanlışlıkla eklenmediğini kontrol edin:
API key
Access token
Password
Private key
Authentication cookie
Database credential
## 28. Repository Public Olduğunda
Public repository içerisindeki bütün dosyaların herkes tarafından görülebileceğini unutmayın.
Özel şirket bilgileri veya kişisel secret eklemeyin.
## 29. Contributor Katkıları
Dış katkılar geldiğinde:
- teknik doğruluk
- kaynak
- lisans
- güvenlik
- yazım
- linkler
kontrol edilmelidir.
## 30. Upstream Değişiklikleri
Qwen Code upstream projesindeki önemli değişiklikleri takip edin.
Özellikle:
- install yöntemi
- config
- model provider
- MCP
- agent
- memory
- slash commands
değişiklikleri Türkçe dokümantasyonu etkileyebilir.
## 31. Upstream ile Karıştırmayın
Bu repository bağımsız topluluk dokümantasyonudur.
README ve belgelerde resmi Qwen projesi olduğu izlenimi verilmemelidir.
## 32. Terminoloji Tutarlılığı
Aynı kavramı farklı belgelerde tamamen farklı isimlerle kullanmaktan kaçının.
Örnek:
Agent
Subagent
Tool
MCP
Context
Provider
Model
Bu teknik isimler gerektiğinde İngilizce korunabilir.
## 33. Türkçe Karakterler
Dosyaların UTF-8 olarak tutulması Türkçe karakter uyumluluğunu kolaylaştırır.
Özellikle:
ç
ğ
ı
İ
ö
ş
ü
karakterlerini commit sonrası GitHub üzerinde kontrol edin.
## 34. Markdown Kontrolü
Dosya commit edilmeden önce GitHub Preview kullanarak:
- başlıklar
- listeler
- linkler
- kod bölümleri
kontrol edilebilir.
## 35. Repository Sağlığı
Zaman zaman şu alanları kontrol edin:
README
LICENSE
CONTRIBUTING
SECURITY
docs
Issues
Pull Requests
Releases
## 36. Bakım Rutini
Basit bakım rutini:
Ayda bir -> Qwen Code güncellemelerini kontrol et -> Bozuk linkleri kontrol et -> Kritik rehberleri gözden geçir -> Issue'ları incele -> README'yi güncelle
## 37. Büyük Güncelleme
Qwen Code büyük sürüm değiştirdiğinde:
1. Release notes oku
2. Breaking changes belirle
3. Kurulum rehberini test et
4. Provider rehberlerini kontrol et
5. MCP rehberini kontrol et
6. Agent ve memory rehberlerini kontrol et
7. README güncelle
## 38. Kullanıcı Geri Bildirimi
Gerçek kullanıcıların yaşadığı problemler dokümantasyonu geliştirmek için değerlidir.
Tekrarlanan bir sorun varsa hata çözme rehberine eklenebilir.
## 39. Projenin Hedefi
Bu repository'nin değeri dosya sayısından değil bilgilerin:
- doğru
- güncel
- anlaşılır
- uygulanabilir
- güvenli
olmasından gelir.
## 40. Başarı Kriteri
Bakımı iyi yapılan bir dokümantasyon projesi:
Güncel kaynak -> Doğru bilgi -> Çalışan örnek -> Açık Türkçe anlatım -> Güvenli kullanım -> Düzenli bakım
zincirini korumalıdır.
## Sonuç
Açık kaynak dokümantasyon tek seferde yazılıp bırakılan bir çalışma değildir.
Qwen Code ve bağlı teknolojiler geliştikçe Türkçe rehberlerin de düzenli olarak gözden geçirilmesi ve güncellenmesi gerekir.
