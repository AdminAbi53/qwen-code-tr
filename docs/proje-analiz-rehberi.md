# Qwen Code Türkçe - Proje Analiz Rehberi
Bu rehber, Qwen Code ile mevcut bir yazılım projesini değiştirmeden önce sistematik olarak analiz etmek için kullanılabilecek yöntemleri açıklar.
Bu proje bağımsız bir Türkçe topluluk dokümantasyonu çalışmasıdır.
## 1. Neden Önce Projeyi Analiz Etmeliyiz?
Mevcut bir projede doğrudan kod değiştirmek beklenmeyen sorunlara yol açabilir.
İlk amaç:
Proje yapısı -> Teknolojiler -> Bağımlılıklar -> Giriş noktaları -> Veri akışı -> Build -> Test -> Runtime
zincirini anlamaktır.
## 2. Projenin Kök Klasörünü Belirleyin
Qwen Code'u mümkün olduğunca gerçek proje kökünden başlatın.
PowerShell örneği:
cd C:\Projects\BenimProjem
qwen
## 3. İlk Görev
Başlangıçta kullanılabilecek basit görev:
Bu projeyi analiz et.
Henüz hiçbir dosyayı değiştirme.
Kullanılan teknolojileri, klasör yapısını, ana giriş noktalarını, dependency sistemini, build sistemini ve test altyapısını belirle.
Sonunda bulgularını özetle.
## 4. Dosya Yapısını İnceleyin
Projenin önemli klasörleri belirlenmelidir.
Örnek:
src
tests
docs
scripts
assets
config
build
Gerçek klasör isimleri projeye göre değişir.
## 5. Proje Dosyalarını Belirleyin
Teknoloji hakkında önemli ipuçları sağlayabilecek dosyalar:
package.json
*.csproj
*.sln
pom.xml
build.gradle
Cargo.toml
go.mod
requirements.txt
pyproject.toml
CMakeLists.txt
project.godot
## 6. Programlama Dillerini Belirleyin
Repository birden fazla dil içerebilir.
Örnek:
C#
C++
Python
Java
Kotlin
JavaScript
TypeScript
Rust
Go
Kullanılan ana dil ile yardımcı script dillerini ayırmak faydalıdır.
## 7. Framework Belirleme
Programlama dili tek başına yeterli değildir.
Örnek:
C# -> WPF / ASP.NET / Unity
Java -> Spring / Android
JavaScript -> React / Next.js / Node.js
Python -> Django / FastAPI / Flask
Framework bilgisi doğru build ve test yöntemini belirlemeye yardımcı olur.
## 8. Giriş Noktasını Bulun
Uygulamanın nereden başladığını belirleyin.
Örnek:
Program.cs
main.py
main.cpp
index.js
main.ts
MainActivity.kt
Gerçek giriş noktası framework'e göre değişebilir.
## 9. Dependency Sistemini İnceleyin
Dependency yönetimi:
npm
NuGet
pip
Maven
Gradle
Cargo
Go Modules
gibi sistemlerden biri veya birkaçı olabilir.
Dependency sürümleri analiz edilmeden rastgele paket güncellemek risklidir.
## 10. Build Sistemini Belirleyin
Gerçek build komutunu bulun.
Örnek:
dotnet build
npm run build
mvn package
gradle build
cargo build
cmake --build
Ancak komutu proje dosyalarından doğrulamadan varsaymayın.
## 11. Test Sistemini Belirleyin
Test frameworklerini araştırın.
Örnek:
xUnit
NUnit
MSTest
Jest
Vitest
Pytest
JUnit
GoogleTest
Gerçek test komutunu proje yapılandırmasından belirleyin.
## 12. Configuration Dosyalarını İnceleyin
Önemli configuration örnekleri:
appsettings.json
.env.example
settings.json
launchSettings.json
tsconfig.json
vite.config
webpack.config
docker-compose.yml
Secret içeren dosyaları raporlarken değerleri göstermeyin.
## 13. Environment Gereksinimleri
Projenin ihtiyaç duyduğu:
SDK
runtime
compiler
database
Docker
external service
model server
gibi gereksinimleri belirleyin.
## 14. README'yi İnceleyin
README önemli başlangıç bilgileri sağlayabilir.
Ancak README'nin her zaman güncel olduğu varsayılmamalıdır.
Gerçek proje dosyaları ve build davranışı ile karşılaştırılmalıdır.
## 15. QWEN.md Kontrolü
Projede QWEN.md bulunuyorsa önce okuyun.
Bu dosyada:
build kuralları
test komutları
mimari kısıtlar
değiştirilmemesi gereken alanlar
bulunabilir.
## 16. Git Durumunu Kontrol Edin
Değişiklik öncesi:
git status
Mevcut kullanıcı değişikliklerinin agent tarafından yanlışlıkla değiştirilmemesi önemlidir.
## 17. Git Geçmişini İnceleyin
Gerekirse:
git log --oneline
Son değişiklikler mevcut mimarinin neden bu şekilde olduğunu anlamaya yardımcı olabilir.
## 18. Çalışan Sistemi Önce Doğrulayın
Yeni değişiklik yapmadan önce mevcut baseline belirlenebilir.
Örnek:
Build şu anda geçiyor mu?
Testler şu anda geçiyor mu?
Uygulama şu anda açılıyor mu?
Böylece yeni değişiklik sonrası oluşan regression daha kolay fark edilir.
## 19. Baseline Build
Değişiklikten önce build çalıştırmak önemli olabilir.
Sonuç kaydedilebilir:
Build Before Change: PASS
veya:
Build Before Change: FAIL
Mevcut hata ile yeni hata birbirine karıştırılmamalıdır.
## 20. Baseline Tests
Testler mevcut durumda zaten başarısız olabilir.
Örneğin:
Tests Before Change: 97/100 PASS
Bu bilgi değişiklik sonrası karşılaştırma için kullanılabilir.
## 21. Mimari Katmanları Belirleyin
Projede:
UI
Domain
Services
Data
Infrastructure
API
Tests
gibi katmanlar bulunabilir.
Yeni özelliğin hangi katmana ait olduğunu anlamak gereksiz bağımlılıkları azaltır.
## 22. Veri Akışını Takip Edin
Özellikle bug araştırırken:
UI -> ViewModel -> Service -> Database
veya:
Request -> Controller -> Service -> Repository -> Database
gibi gerçek akışı takip edin.
## 23. Hata Noktasından Geriye Doğru Gitmek
Bir runtime hatası varsa:
Hata -> Stack Trace -> Method -> Caller -> Input -> Root Cause
zinciri kullanılabilir.
## 24. Search Kullanımı
Büyük repository içerisinde:
class adı
method adı
error mesajı
config anahtarı
endpoint
aranabilir.
Ancak aynı aramayı tekrar tekrar yapmak yeni bilgi üretmez.
## 25. Generated Dosyaları Ayırın
Bazı klasörler elle değiştirilmemelidir.
Örnek:
bin
obj
node_modules
dist
generated
vendor
Gerçek proje kurallarına göre değişebilir.
## 26. Third-Party Kodları Ayırın
Repository içerisinde üçüncü taraf kod bulunabilir.
Bug'ın kaynağı doğrulanmadan vendor kodunu değiştirmek risklidir.
## 27. Büyük Dosyalara Dikkat
Binary, model, video veya build artifact dosyaları agent context'ine gereksiz şekilde alınmamalıdır.
Önce ilgili source dosyaları belirleyin.
## 28. Secret Taraması
Analiz sırasında:
.env
credential
token
API key
dosyaları görülebilir.
Secret değerleri kullanıcıya veya loglara gereksiz şekilde yazılmamalıdır.
## 29. Network Bağımlılıkları
Proje dış servislere bağlı olabilir.
Örnek:
REST API
database
model API
OAuth
cloud storage
Build başarılı olsa bile runtime için bu servisler gerekli olabilir.
## 30. Platform Bağımlılıkları
Proje:
Windows
Linux
macOS
Android
iOS
gibi belirli platformlara bağlı olabilir.
Agent değişiklik yaparken hedef platformu doğru belirlemelidir.
## 31. Donanım Bağımlılıkları
Bazı projeler:
GPU
kamera
mikrofon
USB cihaz
Android telefon
özel accelerator
gerektirebilir.
Bu gereksinimler test planında dikkate alınmalıdır.
## 32. CI/CD Dosyaları
Repository içerisinde:
.github/workflows
azure-pipelines.yml
GitLab CI
Jenkinsfile
bulunabilir.
CI yapılandırması gerçek build ve test komutları hakkında önemli bilgi sağlayabilir.
## 33. Docker
Dockerfile veya compose dosyaları varsa uygulamanın bağımlı servislerini anlamaya yardımcı olabilir.
Ancak Docker'ın gerçekten aktif geliştirme yolu olup olmadığını doğrulayın.
## 34. Test Fixture
Testlerde:
mock
fixture
sample data
test database
kullanılabilir.
Gerçek runtime davranışı ile test ortamını birbirine karıştırmayın.
## 35. TODO ve FIXME
TODO veya FIXME kayıtları proje hakkında ipucu verebilir.
Ancak her TODO mevcut görevin parçası değildir.
Görev kapsamını gereksiz şekilde genişletmeyin.
## 36. Kod Değişikliğine Geçmeden Önce
Şu sorular cevaplanabilmelidir:
Proje ne yapıyor?
Hangi teknoloji kullanılıyor?
Build nasıl yapılıyor?
Test nasıl çalışıyor?
Değiştirilecek davranış nerede?
Hangi dosyalar etkilenebilir?
Regression riski nedir?
## 37. Analiz Sonucu Şablonu
Örnek:
Project Type:
Primary Language:
Framework:
Entry Point:
Build System:
Test System:
Important Directories:
External Dependencies:
Current Build:
Current Tests:
Relevant Components:
Potential Risks:
Recommended Implementation Area:
## 38. Analizden Sonra Plan
Analiz tamamlandıktan sonra:
Root Cause veya Requirement -> Etkilenen Bileşenler -> Minimum Değişiklik -> Build -> Tests -> Runtime -> Regression
planı oluşturulabilir.
## 39. Ne Zaman Kullanıcıya Sorulmalı?
Teknik olarak repository veya resmi dokümantasyondan bulunabilecek bilgi için kullanıcıya gereksiz soru sorulmamalıdır.
Ancak sonucu değiştiren gerçek kullanıcı tercihi varsa soru sorulabilir.
Örnek:
İki farklı UI davranışından hangisini istiyorsunuz?
## 40. Başarı Kriteri
İyi proje analizi:
Dosyaları listelemek
ile sınırlı değildir.
Başarılı analiz:
Proje yapısı anlaşıldı -> Build/Test yolu belirlendi -> İlgili kod akışı bulundu -> Riskler belirlendi -> Değişiklik alanı kanıtlandı
sonucunu üretmelidir.
## Sonuç
Qwen Code ile güvenilir geliştirme yapmanın en önemli adımlarından biri mevcut projeyi değiştirmeden önce doğru anlamaktır.
İyi analiz, gereksiz dosya değişikliklerini azaltır, root cause bulmayı kolaylaştırır ve sonraki build, test ve runtime doğrulamalarının daha güvenilir olmasını sağlar.
