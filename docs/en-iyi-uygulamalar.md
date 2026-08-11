# Qwen Code Türkçe - En İyi Kullanım Uygulamaları
Bu rehber, Qwen Code ile daha güvenilir, kontrollü ve verimli çalışmak için uygulanabilecek temel yöntemleri toplar.
Bu depo Qwen ekibinin resmi projesi değildir. Bağımsız bir Türkçe topluluk dokümantasyonu çalışmasıdır.
## 1. Qwen Code'u Doğru Proje Klasöründe Başlatın
Terminali projenin ana klasöründe açın.
Örnek:
cd C:\Projects\BenimProjem
qwen
Yanlış klasörde başlatılan agent gereksiz dosyaları context'e alabilir veya projenin gerçek yapısını yanlış değerlendirebilir.
## 2. Görevi Net Tanımlayın
Sadece:
Bu projeyi düzelt.
demek yerine hedefi belirtin.
Örnek:
Uygulama açılırken oluşan hatanın gerçek nedenini bul, düzelt, Release build çalıştır ve uygulamayı tekrar başlatarak doğrula.
## 3. Beklenen Sonucu Belirtin
Görev verirken tamamlanma kriterini açıkça yazmak faydalıdır.
Örnek:
Görev ancak Release build başarılı olduğunda ve uygulama gerçek runtime testinde hatasız açıldığında tamamlanmış kabul edilecek.
## 4. Önce Analiz
Karmaşık problemlerde agent'ın doğrudan kod değiştirmesi yerine önce mevcut sistemi anlamasını isteyin.
Örnek akış:
Proje inceleme -> Root cause -> Plan -> Değişiklik -> Build -> Test -> Runtime
## 5. Güncel Bilgi Gerekiyorsa Araştırın
Framework, SDK, API veya dependency sürümleri değişebilir.
Güncel teknik bilgi gereken görevlerde resmi kaynaklar öncelikli olmalıdır.
Öncelik:
Resmi dokümantasyon -> Resmi repository -> Release notes -> Maintainer açıklamaları
## 6. Tahmine Dayalı Kod Değişikliğinden Kaçının
Agent'ın:
Sanırım sorun burada.
deyip dosya değiştirmesi yerine problemi kanıtlamasını isteyin.
Gerçek kanıt:
- hata çıktısı
- stack trace
- compiler sonucu
- test sonucu
- ilgili source akışı
olabilir.
## 7. Git Kullanın
Agent ile önemli değişiklikler yapmadan önce repository durumunu kontrol edin:
git status
Değişikliklerden sonra:
git diff
Bu sayede agent'ın hangi dosyaları değiştirdiği görülebilir.
## 8. Küçük ve Kontrol Edilebilir Değişiklikler
Bir hata için bütün mimariyi değiştirmek yerine mümkün olduğunda minimum güvenli değişiklik tercih edilmelidir.
Bu yaklaşım regression riskini azaltır.
## 9. Çalışan Özellikleri Koruyun
Yeni özellik eklenirken mevcut çalışan özelliklerin bozulmadığı doğrulanmalıdır.
Bu nedenle yalnız yeni özelliği test etmek yeterli olmayabilir.
Regression testleri de çalıştırılmalıdır.
## 10. Build Gerçek Kanıttır
Kodun mantıklı görünmesi build'in başarılı olduğu anlamına gelmez.
.NET:
dotnet build
Node.js:
npm run build
Java:
mvn test
Gerçek komut proje teknolojisine göre değişir.
## 11. Test Sonucunu Kontrol Edin
Agent:
Testler başarılı.
dediğinde mümkün olduğunda gerçek test çıktısını kontrol edin.
Önemli bilgiler:
- toplam test
- başarılı test
- başarısız test
- skipped test
- exit code
## 12. Runtime Testi Yapın
Build başarılı olması uygulamanın gerçekten çalıştığını kanıtlamaz.
Mümkün olduğunda uygulamayı gerçek ortamda başlatın ve hedef davranışı test edin.
## 13. Artifact Kontrolü
Görev bir çıktı dosyası üretmekse dosyanın gerçekten oluştuğunu doğrulayın.
Örnek:
- EXE
- APK
- DLL
- DOCX
- PDF
- JSON
- image
- build package
Dosyanın yalnız adının raporda geçmesi yeterli değildir.
## 14. PASS Metnine Güvenmeyin
Bir agent'ın:
PASS
READY
SUCCESS
DONE
yazması gerçek doğrulama değildir.
Başarı gerçek evidence ile desteklenmelidir.
## 15. Tool Çağrısı İlerleme Değildir
Agent'ın sürekli terminal veya dosya aracı kullanması görevin ilerlediği anlamına gelmez.
Gerçek ilerleme:
- yeni artifact
- yeni doğrulanmış bilgi
- yeni test sonucu
- root cause
- tamamlanan acceptance kriteri
üretmelidir.
## 16. Aynı Yöntemin Tekrarını Engelleyin
Aynı hata karşısında aynı komut veya semantic olarak aynı çözüm tekrar tekrar deneniyorsa strateji değiştirilmelidir.
Yeni evidence yoksa tekrar ilerleme değildir.
## 17. Hata Mesajını Saklamayın
Agent'ın hata mesajını görmesi root cause analizi için önemlidir.
Mümkün olduğunda tam:
- error
- stack trace
- exit code
- stderr
bilgisini sağlayın.
Secret içeren logları paylaşmadan önce temizleyin.
## 18. Eksik Dependency'yi Doğrulayın
Bir dependency eksik denildiğinde gerçekten eksik olduğunu kontrol edin.
Örneğin:
dotnet --list-sdks
node --version
npm list
python --version
pip list
java -version
## 19. Rastgele Paket Kurmayın
Agent'ın bilinmeyen bir dependency yüklemesine izin vermeden önce:
- paket adı
- resmi kaynak
- sürüm
- proje
- bakım durumu
kontrol edilmelidir.
## 20. Secret Bilgileri Koruyun
Agent görevlerine gerçek:
- API key
- password
- access token
- private key
bilgilerini gereksiz şekilde eklemeyin.
Public repository içerisinde secret saklamayın.
## 21. Büyük Görevleri Mantıksal Olarak Bölün
Büyük görevler:
Research
Architecture
Implementation
Testing
Validation
gibi aşamalara ayrılabilir.
Ancak kullanıcı her küçük adımı manuel olarak yönetmek zorunda kalmamalıdır.
Agent sistemi mümkün olduğunda bu ayrımı kendisi yapmalıdır.
## 22. Paralel Çalışabilecek İşleri Belirleyin
Birbirine bağımlı olmayan görevler paralel yürütülebilir.
Örneğin:
Research Agent
Security Agent
UI Analysis Agent
aynı anda farklı konuları inceleyebilir.
## 23. Aynı Dosyada Paralel Yazmaya Dikkat
İki coding agent aynı dosyayı eşzamanlı değiştirirse conflict oluşabilir.
Bunun için:
- workspace isolation
- worktree
- file lease
- controlled merge
kullanılabilir.
## 24. Doğru Agent'ı Doğru İşe Verin
Bir agent'ın yalnız adı uzman olduğunu kanıtlamaz.
Agent seçiminde capability ve gerçek validation sonuçları kullanılmalıdır.
Örneğin:
C# görevi -> doğrulanmış C# capability
Godot görevi -> doğrulanmış Godot capability
Research görevi -> gerçek web erişimi olan Research capability
## 25. Agent Registry'yi Güncel Tutun
Agent sistemi kullanılıyorsa her agent için:
- capability
- status
- validation
- tool
- environment
bilgileri tutulabilir.
Bozuk agent Ready olarak görünmemelidir.
## 26. Independent Validation
İşi yapan agent ile final doğrulamayı yapan agent'ın ayrılması daha güvenilir olabilir.
Örnek:
Coding Agent -> Değişiklik
Testing Agent -> Test
Validator Agent -> Acceptance doğrulaması
## 27. Research ile Implementation'ı Ayırın
Research Agent'ın görevi kaynak toplamak ve teknik bulguları sunmaktır.
Coding Agent ise doğrulanmış araştırma sonucunu gerçek projeye uygular.
Bu ayrım özellikle güncel API ve framework görevlerinde yararlıdır.
## 28. Kaynak Kalitesini Kontrol Edin
İnternette bulunan ilk cevabı doğru kabul etmeyin.
Kaynak değerlendirmesinde:
- resmi mi?
- güncel mi?
- kullanılan sürümle uyumlu mu?
- birden fazla kaynak destekliyor mu?
soruları önemlidir.
## 29. Stack Overflow ve Forumlar
Topluluk kaynakları faydalıdır ancak eski cevaplar güncel sürümlerde geçersiz olabilir.
Forum çözümünü uygulamadan önce resmi dokümantasyonla karşılaştırın.
## 30. Model Hafızası Güncel Dokümantasyon Değildir
Bir dil modeli bir framework hakkında bilgi biliyor olabilir.
Ancak modelin eğitim verisi güncel sürümü içermeyebilir.
Yeni teknolojilerde gerçek web araştırması önemlidir.
## 31. Context'i Gereksiz Doldurmayın
Agent'a bütün repository'yi her görevde göndermek yerine ilgili dosyalar seçilebilir.
Minimum yeterli context daha hızlı ve daha odaklı çalışma sağlayabilir.
## 32. Uzun Görevlerde Checkpoint
Uzun görevlerde belirli noktalarda state saklamak yararlıdır.
Örneğin:
Research Complete
Architecture Complete
Implementation Complete
Validation Pending
Crash sonrası agent son doğrulanmış noktadan devam edebilir.
## 33. Restart Testi
Uzun süre çalışan agent sistemlerinde uygulama yeniden başlatıldığında görev durumunun korunması önemlidir.
Test:
Görev başlat -> İlerleme oluştur -> Uygulamayı kapat -> Tekrar aç -> Göreve devam et
## 34. Recovery
Teknik hata olduğunda ilk çözüm görevi tamamen bırakmak olmamalıdır.
Örnek:
Failure -> Classification -> Root Cause -> Alternative Strategy -> Retry -> Validation
## 35. Kullanıcı Müdahalesi Gereken Durumlar
Bazı durumlar gerçekten kullanıcı gerektirebilir:
- CAPTCHA
- MFA
- ödeme
- fiziksel cihaz
- belirsiz kullanıcı tercihi
- geri dönüşü olmayan önemli karar
Normal build veya dependency hataları mümkün olduğunda sistem tarafından çözülmelidir.
## 36. Destructive İşlemler
Agent'a geniş sistem erişimi verilmişse destructive işlemler dikkatle yönetilmelidir.
Örnek:
- disk silme
- recursive deletion
- production database reset
- credential deletion
- git reset --hard
Bu işlemler için güvenli transaction, backup veya kullanıcı onayı gerekebilir.
## 37. Agent Logları
İyi log yalnız:
Tool çalıştı.
dememelidir.
Şunları göstermesi faydalıdır:
- hangi görev
- hangi agent
- hangi tool
- neden seçildi
- sonuç
- evidence
- sonraki karar
## 38. Maliyet ve Kaynak Kullanımı
Bulut modellerinde token maliyeti, yerel modellerde CPU/RAM/VRAM maliyeti vardır.
Her görevi en büyük modele göndermek yerine göreve uygun model seçilebilir.
## 39. Model Fallback
Ana model kullanılamadığında alternatif model kullanılabilir.
Ancak fallback model:
- gerekli context
- coding
- tool calling
- structured output
yeteneklerine sahip olmalıdır.
## 40. Başarılı Görevlerden Öğrenin
Doğrulanmış çözümler gelecekte yeniden kullanılabilir.
Saklanabilecek bilgiler:
- problem fingerprint
- çalışan çözüm
- environment
- sürüm
- test sonucu
- tarih
## 41. Başarısız Yöntemleri Hatırlayın
Sistem yalnız başarıları değil başarısız stratejileri de saklayabilir.
DoNotRetry kaydı aynı yöntemin gereksiz tekrarını azaltabilir.
## 42. Eski Çözümleri Körü Körüne Kullanmayın
Daha önce çalışan çözüm:
- yeni SDK
- yeni dependency
- farklı işletim sistemi
- farklı model
nedeniyle artık geçerli olmayabilir.
Memory freshness kontrolü yapılmalıdır.
## 43. Gerçek Kullanıcı Senaryosu
Final validation yalnız teknik testlerden oluşmamalıdır.
Kullanıcının gerçekten yapacağı işlem de denenmelidir.
Örnek:
Uygulamayı aç -> Dosya seç -> İşlemi çalıştır -> Sonucu görüntüle
## 44. Completion Contract
Göreve başlamadan önce tamamlanma kriterleri belirlenebilir.
Örnek:
Build PASS
Tests PASS
Runtime PASS
Expected Artifact Exists
Regression PASS
Bu kriterlerden biri başarısızsa görev tamamlanmamıştır.
## 45. İyi Bir Qwen Code Görevinin Yapısı
Güçlü bir görev genellikle şu bilgileri içerir:
HEDEF
MEVCUT DURUM
SORUN
KISITLAR
BEKLENEN SONUÇ
DOĞRULAMA
Ancak basit işler için gereksiz uzun prompt yazmak zorunlu değildir.
## 46. Kullanıcı Dili
Kullanıcı Türkçe görev veriyorsa agent teknik işlemleri yaparken hedefi doğru anlamalı ve gerektiğinde Türkçe iletişim kurabilmelidir.
Teknik isimler İngilizce bırakılabilir.
## 47. Belirsizliği Fark Edin
Kullanıcı isteğinde sonucu değiştirecek kritik bir belirsizlik varsa agent rastgele seçim yapmak yerine kullanıcıya sormalıdır.
Ancak teknik olarak araştırılıp çözülebilecek her konuda kullanıcıya soru yöneltmek de gereksizdir.
## 48. Son Rapor
İyi bir final raporu kısa ama kanıtlanabilir olmalıdır.
Örnek:
Root Cause: ...
Değiştirilen dosyalar: ...
Build: PASS
Tests: 24/24 PASS
Runtime: PASS
Artifact: ...
Kalan gerçek engel: Yok
## 49. Altın Kural
Agent'ın ne söylediğinden çok gerçek sistemde ne yaptığı önemlidir.
Kod yazıldı mı?
Build geçti mi?
Test geçti mi?
Runtime çalıştı mı?
Beklenen sonuç gerçekten oluştu mu?
Bu soruların cevabı gerçek başarıyı belirler.
## Sonuç
Qwen Code'dan en iyi sonucu almak için güçlü model kullanmak tek başına yeterli değildir.
Net hedef, doğru context, güncel araştırma, güvenli tool kullanımı, gerçek build/test/runtime doğrulaması ve evidence tabanlı çalışma birlikte kullanıldığında daha güvenilir bir coding agent deneyimi elde edilir.
