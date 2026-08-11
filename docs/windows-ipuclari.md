# Qwen Code Türkçe - Windows İpuçları
Bu rehber, Qwen Code'u Windows üzerinde daha sorunsuz kullanmak isteyen kullanıcılar için kısa ve pratik ipuçları içerir.
Bu depo Qwen ekibinin resmi projesi değildir. Bağımsız bir Türkçe topluluk dokümantasyonu çalışmasıdır.
## 1. Terminal Tercihi
Windows üzerinde PowerShell veya Windows Terminal kullanabilirsiniz.
Windows Terminal kullanmak birden fazla shell ve sekme ile çalışmayı kolaylaştırabilir.
## 2. PATH Sorunları
Bir araç kurulduktan sonra komut bulunamıyorsa ilk olarak terminali kapatıp yeniden açın.
Ardından ilgili komutu kontrol edin.
Örnek:
node --version
npm --version
git --version
qwen --version
Yeni kurulan executable PATH'e eklenmiş ancak açık terminal eski environment bilgisini kullanıyor olabilir.
## 3. Hangi Executable Çalışıyor?
Bir komutun hangi dosyadan çalıştığını görmek için:
Get-Command qwen
Get-Command node
Get-Command git
Bu yöntem aynı programın birden fazla sürümü kurulu olduğunda faydalıdır.
## 4. PATH İçeriğini Görmek
PowerShell içerisinde:
$env:PATH -split ';'
komutu ile PATH girişlerini satır satır görebilirsiniz.
## 5. Çalışma Klasörünü Kontrol Etme
Mevcut klasörü görmek için:
Get-Location
Dosyaları görmek için:
Get-ChildItem
Yanlış klasörde Qwen Code başlatmak yanlış proje bağlamının kullanılmasına neden olabilir.
## 6. Proje Klasörüne Geçme
Örnek:
cd C:\Projeler\BenimUygulamam
Ardından:
qwen
## 7. Dosya Yollarında Boşluk
Bir path içerisinde boşluk varsa tırnak kullanın.
Örnek:
cd "C:\Users\Kullanici\My Projects\Test App"
Bu özellikle terminal komutlarında path parsing hatalarını azaltır.
## 8. PowerShell ve cmd Farkı
Bazı komut örnekleri PowerShell'e, bazıları cmd.exe'ye özel olabilir.
PowerShell değişken örneği:
$env:MY_VARIABLE="value"
cmd.exe örneği:
set MY_VARIABLE=value
Komutun hangi shell için yazıldığını kontrol edin.
## 9. Execution Policy
PowerShell bazı scriptlerin çalıştırılmasını güvenlik nedeniyle engelleyebilir.
Kontrol:
Get-ExecutionPolicy
Get-ExecutionPolicy -List
Policy ayarlarını nedenini anlamadan sistem genelinde değiştirmeyin.
## 10. qwen.ps1 ve qwen.cmd
npm tabanlı global paketler Windows üzerinde birden fazla launcher oluşturabilir.
Örneğin:
qwen.ps1
qwen.cmd
PowerShell policy sorunu varsa hangi launcher'ın çalıştığını kontrol etmek faydalı olabilir.
Get-Command qwen
## 11. npm Global Klasörü
Global npm klasörünü görmek için:
npm prefix -g
Global paketleri görmek için:
npm list -g --depth=0
Qwen Code kurulmuş fakat komut bulunamıyorsa global npm path'i PATH içerisinde olmayabilir.
## 12. Node.js Sürümü
Kontrol:
node --version
npm --version
Qwen Code'un ihtiyaç duyduğu Node.js sürümü zamanla değişebilir.
Güncel gereksinimleri resmi Qwen Code dokümantasyonundan kontrol edin.
## 13. Git Kontrolü
Kontrol:
git --version
Proje durumunu görmek için:
git status
Agent ile kod değiştirirken Git kullanmak geri dönüş ve değişiklik incelemesini kolaylaştırır.
## 14. Git Diff
Agent tarafından yapılan değişiklikleri görmek için:
git diff
Özet:
git diff --stat
Bu kontrol, beklenmeyen dosya değişikliklerini hızlıca fark etmenize yardımcı olur.
## 15. Windows Uzun Path Sorunları
Bazı projelerde çok derin klasör yapıları path uzunluğu sorunlarına yol açabilir.
Proje klasörlerini gereksiz derecede uzun path'ler altında tutmamaya çalışın.
Örnek daha basit yapı:
C:\Projects\App
çok uzun kullanıcı ve alt klasör zincirlerinden daha kolay yönetilebilir.
## 16. OneDrive Klasörleri
Proje klasörleri OneDrive gibi senkronizasyon araçlarının içinde olduğunda bazı geliştirme araçları dosya kilidi veya sync kaynaklı davranışlarla karşılaşabilir.
Sorun yaşarsanız projeyi normal yerel bir çalışma klasöründe test etmek faydalı olabilir.
## 17. Antivirüs ve Güvenlik Yazılımı
Build araçları, package manager cache'leri veya local server process'leri zaman zaman güvenlik yazılımları tarafından incelenebilir.
Sorun yaşadığınızda antivirüsü tamamen kapatmak yerine hangi dosya veya process'in engellendiğini belirleyin.
## 18. Firewall
LM Studio, Ollama veya başka bir local model server kullanıyorsanız firewall bağlantıyı etkileyebilir.
Önce servisin gerçekten dinlediğini doğrulayın.
Örnek:
Test-NetConnection localhost -Port 1234
Ollama için tipik port:
Test-NetConnection localhost -Port 11434
Gerçek port kullandığınız yapılandırmaya göre değişebilir.
## 19. Port Kontrolü
Belirli bir portu hangi process'in kullandığını görmek için:
Get-NetTCPConnection -LocalPort 1234
veya:
netstat -ano | findstr :1234
Port çakışması local API servislerinin başlamasını engelleyebilir.
## 20. Process Kontrolü
Çalışan processleri görmek için:
Get-Process
Belirli process:
Get-Process | Where-Object ProcessName -Like "*node*"
Bir process'i yalnız gerçekten takıldığı doğrulanmışsa sonlandırın.
## 21. CPU ve RAM
Büyük projelerde veya yerel modellerde yüksek kaynak kullanımı normal olabilir.
Ancak sistem tamamen yavaşlıyorsa:
- model boyutunu
- context değerini
- çalışan paralel process sayısını
- background uygulamalarını
kontrol edin.
## 22. VRAM
Yerel coding modellerinde VRAM önemli olabilir.
Model VRAM kapasitesini aşıyorsa RAM veya CPU offload nedeniyle performans düşebilir.
Daha küçük model veya uygun quantization seçmek gerekebilir.
## 23. LM Studio Testi
LM Studio API kontrolü için:
Invoke-RestMethod http://localhost:1234/v1/models
Gerçek port LM Studio yapılandırmasına göre değişebilir.
## 24. Ollama Testi
Ollama kontrol:
ollama list
API kontrol:
Invoke-RestMethod http://localhost:11434/api/tags
## 25. Localhost ve 127.0.0.1
Yerel API'lerde:
localhost
ve:
127.0.0.1
genellikle aynı bilgisayarı ifade eder.
Ancak bazı network veya bind yapılandırmalarında davranış farklı olabilir.
## 26. Proxy
Kurumsal ağ veya özel proxy kullanıyorsanız npm, Git veya API bağlantıları etkilenebilir.
Proxy sorununda önce sistem ve uygulama proxy ayarlarını doğrulayın.
## 27. VPN
VPN bazı model sağlayıcılarının endpoint'lerine erişimi veya DNS davranışını değiştirebilir.
Bağlantı problemi araştırırken VPN'in etkisini kontrol etmek gerekebilir.
## 28. DNS
Domain çözümleme problemi varsa:
Resolve-DnsName example.com
gibi komutlar kullanılabilir.
İnternet erişiminin olması belirli API domain'inin çözüldüğü anlamına gelmez.
## 29. HTTPS Hataları
Certificate veya TLS hatalarında güvenliği kapatmak yerine gerçek certificate problemini belirleyin.
Kurumsal proxy, eski runtime veya yanlış sistem saati gibi nedenler olabilir.
## 30. Sistem Saati
Authentication ve HTTPS sistemleri yanlış saat nedeniyle hata verebilir.
Windows saat ve timezone ayarlarının doğru olduğunu kontrol edin.
## 31. Yönetici Yetkisi
Her aracı sürekli Administrator olarak çalıştırmayın.
Yalnız gerçekten gerekli olduğunda yükseltilmiş yetki kullanın.
Normal proje geliştirme işlemlerinin çoğu standart kullanıcı hesabıyla yapılabilir.
## 32. Geçici Dosyalar
Build veya package manager sorununda cache temizliği bazen gerekli olabilir.
Ancak cache'i otomatik olarak ilk çözüm olarak silmeyin.
Önce gerçek hata mesajını inceleyin.
## 33. Disk Alanı
Kontrol:
Get-PSDrive C
Model dosyaları, npm cache, build artifacts ve repository'ler önemli disk alanı kullanabilir.
Yetersiz disk alanı beklenmeyen build ve download hatalarına neden olabilir.
## 34. UTF-8 ve Türkçe Karakterler
Türkçe dosya içeriklerinde encoding problemleri yaşanabilir.
Modern araçlarda UTF-8 tercih edilmesi genellikle en uyumlu yaklaşımdır.
Agent tarafından dosya yazıldıktan sonra Türkçe karakterlerin doğru göründüğünü kontrol edin.
## 35. Dosya Kilitleri
Bir build çıktısı veya dosya silinemiyorsa başka process tarafından açık tutuluyor olabilir.
Dosyayı zorla silmeden önce hangi uygulamanın kullandığını belirlemek daha güvenlidir.
## 36. Restart Testi
Environment variable, PATH veya kurulum değişikliklerinden sonra:
1. terminali kapatın
2. yeni terminal açın
3. ilgili komutu tekrar çalıştırın
Gerekli durumlarda uygulamayı veya bilgisayarı yeniden başlatmak environment değişikliklerini doğrulamaya yardımcı olabilir.
## 37. Minimum Test Ortamı
Karmaşık bir projede hata alıyorsanız küçük bir test klasöründe aynı aracın çalışıp çalışmadığını doğrulayın.
Örnek:
C:\Temp\qwen-test
Bu yöntem problemin Qwen Code'da mı yoksa mevcut projede mi olduğunu ayırmaya yardımcı olabilir.
## 38. Sorun Giderme Sırası
Windows üzerinde problem yaşadığınızda:
Komut var mı? -> Doğru executable mı? -> Doğru klasörde miyim? -> Dependency mevcut mu? -> API erişiliyor mu? -> Gerçek hata ne? -> En küçük güvenli düzeltme -> Tekrar test
## 39. Temel Windows Kontrol Komutları
where.exe node
where.exe git
where.exe qwen
node --version
npm --version
git --version
qwen --help
Get-Location
git status
Bu komutlar başlangıç teşhisi için faydalıdır.
## Sonuç
Windows üzerinde Qwen Code kullanırken birçok problem Qwen Code'un kendisinden değil PATH, runtime, shell, API endpoint, dosya yolu veya dependency yapılandırmasından kaynaklanabilir.
En güvenli yaklaşım rastgele sistem değişiklikleri yapmak yerine problemi hangi katmanın oluşturduğunu önce doğrulamaktır.
