# Qwen Code Türkçe - Temel Komutlar ve Kısa Başvuru Rehberi
Bu belge, Qwen Code kullanırken sık ihtiyaç duyulan temel komutları ve kontrol adımlarını tek yerde toplamak için hazırlanmıştır.
Bu depo Qwen ekibinin resmi projesi değildir. Bağımsız bir Türkçe topluluk dokümantasyonu çalışmasıdır.
## 1. Qwen Code'u Başlatma
Bir proje klasöründe:
qwen
## 2. Yardım
Kullanılabilir komutları görmek için:
qwen --help
Qwen Code açıkken desteklenen slash komutlarını görmek için yardım ekranını kullanabilirsiniz.
## 3. Sürüm Bilgisi
Desteklenen sürümlerde:
qwen --version
Çalışmıyorsa:
qwen --help
## 4. Proje Klasörüne Geçme
PowerShell:
cd C:\Projects\BenimProjem
Ardından:
qwen
## 5. Mevcut Klasörü Görme
PowerShell:
Get-Location
## 6. Dosyaları Listeleme
PowerShell:
Get-ChildItem
Alt klasörlerle birlikte:
Get-ChildItem -Recurse
Çok büyük projelerde recursive listeleme uzun çıktı üretebilir.
## 7. Git Durumunu Kontrol Etme
git status
## 8. Git Değişikliklerini Görme
git diff
Değişiklik özeti:
git diff --stat
## 9. Git Geçmişi
git log --oneline
## 10. Node.js Kontrolü
node --version
## 11. npm Kontrolü
npm --version
## 12. Global npm Paketleri
npm list -g --depth=0
## 13. npm Global Klasörü
npm prefix -g
## 14. Git Kontrolü
git --version
## 15. Python Kontrolü
python --version
pip --version
## 16. .NET Kontrolü
dotnet --info
Kurulu SDK sürümleri:
dotnet --list-sdks
## 17. Java Kontrolü
java -version
javac -version
## 18. Maven Kontrolü
mvn -version
## 19. Gradle Kontrolü
Gradle:
gradle --version
Projede wrapper varsa Windows:
.\gradlew.bat --version
## 20. LM Studio API Kontrolü
Tipik yerel endpoint:
Invoke-RestMethod http://localhost:1234/v1/models
Gerçek port LM Studio ayarına göre değişebilir.
## 21. Ollama Kontrolü
ollama --version
Kurulu modeller:
ollama list
API kontrolü:
Invoke-RestMethod http://localhost:11434/api/tags
## 22. Ağ Portu Kontrolü
Örnek:
Test-NetConnection localhost -Port 1234
Ollama için:
Test-NetConnection localhost -Port 11434
## 23. Hangi Executable Kullanılıyor?
PowerShell:
Get-Command qwen
Get-Command node
Get-Command git
Get-Command python
## 24. PATH Kontrolü
PowerShell:
$env:PATH -split ';'
## 25. MCP Yönetimi
Qwen Code sürümü destekliyorsa uygulama içerisinde:
/mcp
komutu MCP bağlantılarını incelemek için kullanılabilir.
Komutların güncel davranışı için resmi Qwen Code dokümantasyonunu kontrol edin.
## 26. Authentication
Desteklenen sürümlerde uygulama içerisindeki authentication komutları kullanılabilir.
Örnek olarak:
/auth
bulunabilir.
Gerçek destek Qwen Code sürümüne göre kontrol edilmelidir.
## 27. Sistem Tanılama
Desteklenen sürümlerde:
/doctor
benzeri tanılama komutları bulunabilir.
Güncel komutları qwen --help ve resmi dokümantasyondan doğrulayın.
## 28. Basit Proje Analiz Görevi
Bu projeyi incele.
Kullanılan programlama dillerini, frameworkleri, ana klasörleri ve başlangıç noktalarını belirle.
Henüz hiçbir dosyayı değiştirme.
## 29. Bug Çözme Görevi
Bu hatanın gerçek nedenini bul.
Tahmin ederek değişiklik yapma.
İlgili kod akışını incele.
Root cause'u belirle.
Düzeltmeyi uygula.
Build ve test çalıştır.
## 30. Build Doğrulama Görevi
Projeyi gerçek ortamda build et.
Build hatası varsa root cause'u bul ve düzelt.
Build başarıyla tamamlanmadan görevi bitirme.
## 31. Test Doğrulama Görevi
İlgili testleri çalıştır.
Başarısız test varsa gerçek nedenini belirle.
Sorunu çöz ve testleri tekrar çalıştır.
## 32. Research Görevi
Bu implementasyondan önce kullanılan teknolojinin güncel resmi dokümantasyonunu araştır.
Deprecated yöntem kullanma.
Araştırma sonucuna göre en uygun yöntemi seç.
## 33. Dependency Eksikliği Görevi
Görev için gerekli bir SDK, compiler, tool veya dependency eksikse bunu yalnız raporlama.
Eksikliği doğrula.
Resmi kaynağını araştır.
Güvenli kurulum yöntemini uygula.
Kurulumu doğrula ve ana göreve devam et.
## 34. Loop Önleme Görevi
Aynı komutu veya aynı semantic stratejiyi yeni evidence olmadan tekrar etme.
Yeni ilerleme yoksa mevcut yöntemi bırak.
Farklı root-cause hipotezi oluştur ve doğrula.
## 35. Final Doğrulama Görevi
Görevi yalnızca aşağıdakiler doğrulandığında tamamlanmış kabul et:
Build başarılı
İlgili testler başarılı
Runtime başarılı
Beklenen artifact mevcut
İstenen kullanıcı davranışı gerçek ortamda doğrulandı
## 36. Secret Güvenliği
Aşağıdaki bilgileri terminal çıktısı veya public repository içerisinde paylaşmayın:
API key
Access token
Password
Private key
Authentication cookie
Database credential
## 37. Güncel Komutları Doğrulama
Qwen Code hızla değişebileceği için bu rehberdeki komutların güncel sürümde desteklendiğini doğrulamak için:
qwen --help
ve resmi Qwen Code dokümantasyonunu kontrol edin.
## Kaynaklar
Qwen Code resmi repository:
https://github.com/QwenLM/qwen-code
Qwen Code resmi dokümantasyonu:
https://qwenlm.github.io/qwen-code-docs/
## Sonuç
Bu belge hızlı başvuru amacıyla hazırlanmıştır.
Bir komut veya özellik çalışmıyorsa önce kullandığınız Qwen Code sürümünü ve güncel resmi dokümantasyonu kontrol edin.
