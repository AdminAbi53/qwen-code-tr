# Qwen Code Türkçe - Hafıza, QWEN.md ve Proje Talimatları
Bu rehber, Qwen Code'un proje talimatlarını ve oturumlar arasında kullanılabilen hafıza özelliklerini nasıl yönettiğini açıklar.
Bu depo Qwen ekibinin resmi projesi değildir. Bağımsız bir Türkçe topluluk dokümantasyonu çalışmasıdır.
## 1. QWEN.md Nedir?
QWEN.md, Qwen Code'a proje veya kullanıcı seviyesinde kalıcı talimatlar vermek için kullanılan context dosyasıdır.
Her yeni oturumda aynı kuralları tekrar yazmak yerine önemli proje bilgileri QWEN.md içerisinde tutulabilir.
## 2. QWEN.md Ne İçerebilir?
Örnek bilgiler:
- proje amacı
- kullanılan teknolojiler
- build komutları
- test komutları
- kodlama standartları
- klasör yapısı
- değiştirilmemesi gereken alanlar
- doğrulama kuralları
- proje özelindeki çalışma yöntemleri
## 3. Proje Seviyesinde QWEN.md
Projenin kök klasöründe QWEN.md oluşturabilirsiniz.
Örnek:
C:\Projects\BenimProjem\QWEN.md
Bu dosya ilgili proje için context sağlar.
## 4. Global QWEN.md
Bütün projelerde geçerli olmasını istediğiniz genel kurallar kullanıcı seviyesindeki QWEN.md içerisinde tutulabilir.
Tipik konum:
~/.qwen/QWEN.md
Windows üzerinde ~ kullanıcının home klasörünü ifade eder.
## 5. Global ve Proje Kurallarını Ayırın
Global dosyada bütün projeler için geçerli çalışma tercihlerini tutun.
Proje dosyasında yalnız ilgili projeye özgü bilgileri saklayın.
Bu yaklaşım gereksiz context kullanımını azaltır.
## 6. QWEN.md Örneği
Örnek içerik:
# Proje
Bu proje .NET tabanlı bir Windows uygulamasıdır.
# Build
Release build:
dotnet build -c Release
# Test
dotnet test -c Release
# Kurallar
- Mevcut çalışan özellikleri bozma.
- Tahmine göre kod değiştirme.
- Önce gerçek hata çıktısını incele.
- Gereksiz dependency ekleme.
- Build başarısızsa görevi tamamlanmış sayma.
## 7. QWEN.md Oluşturmayı Otomatikleştirme
Qwen Code güncel sürümlerinde:
/init
komutu proje yapısını inceleyerek başlangıç QWEN.md dosyası oluşturmak için kullanılabilir.
Oluşturulan içeriği yine de inceleyin.
## 8. Hafızayı Görmek
Qwen Code içerisinde:
/memory
komutu hafıza yönetim panelini açabilir.
Buradan yüklenen proje ve kullanıcı context dosyaları ile otomatik hafıza bilgileri incelenebilir.
## 9. Context Yenileme
QWEN.md üzerinde değişiklik yaptıktan sonra context'i yeniden yüklemek gerekebilir.
Desteklenen sürümlerde:
/memory refresh
kullanılabilir.
## 10. Yüklenen Context'i Kontrol Etme
Desteklenen sürümlerde:
/memory show
ile birleştirilmiş instructional context görüntülenebilir.
Bu yöntem hangi talimatların gerçekten modele ulaştığını kontrol etmek için yararlıdır.
## 11. Hiyerarşik Context
Qwen Code context dosyalarını hiyerarşik olarak yükleyebilir.
Genel mantık:
Global Context -> Project Context -> Daha Spesifik Context
Bu sayede genel kurallar ile proje özelindeki kurallar birlikte kullanılabilir.
## 12. Birden Fazla QWEN.md
Büyük projelerde farklı dizinlerde daha özel context dosyaları kullanılabilir.
Örneğin:
Proje
QWEN.md
src
QWEN.md
frontend
QWEN.md
Ancak gereksiz sayıda dosya oluşturmak context karmaşasına neden olabilir.
## 13. Çelişkili Talimatlardan Kaçının
Bir QWEN.md:
Testleri mutlaka çalıştır.
derken başka bir context dosyası:
Test çalıştırma.
diyorsa model davranışı tutarsızlaşabilir.
Context dosyalarını zaman zaman kontrol edin.
## 14. Kesin Talimatlar Yazın
Belirsiz:
Kodu güzel yaz.
yerine:
TypeScript dosyalarında 2-space indentation kullan.
gibi doğrulanabilir kurallar daha faydalıdır.
## 15. Context Dosyasına Başka Dosya Ekleme
Qwen Code context sistemi Markdown dosyalarından başka içerikleri referanslamayı destekleyebilir.
Örnek:
@docs/architecture.md
Bu yöntem büyük proje bilgisini tek QWEN.md içerisine kopyalamadan modüler tutmaya yardımcı olabilir.
## 16. Otomatik Hafıza
Qwen Code'un güncel sürümlerinde konuşmalardan yararlı bilgileri otomatik olarak çıkarabilen hafıza sistemi bulunabilir.
Bu sistem:
- kullanıcı tercihleri
- verilen geri bildirimler
- proje bağlamı
- önemli dış referanslar
gibi bilgileri sonraki oturumlarda kullanmak üzere saklayabilir.
## 17. Otomatik Hafıza Nerede Saklanır?
Güncel Qwen Code dokümantasyonuna göre proje hafızaları kullanıcı Qwen dizini altında proje bazlı olarak saklanabilir.
Bu yapı farklı branch veya worktree'lerde aynı repository hafızasının paylaşılmasına yardımcı olabilir.
## 18. Bir Bilgiyi Hatırlatma
Desteklenen sürümlerde:
/remember <bilgi>
komutu kullanılabilir.
Örnek:
/remember Bu projede Release build tamamlanmadan görev PASS sayılmaz.
Bu yöntem önemli bir bilgiyi otomatik hafızaya doğrudan eklemek için kullanılabilir.
## 19. Hafızadan Bilgi Silme
Artık geçerli olmayan bir bilgiyi kaldırmak için desteklenen sürümlerde:
/forget <bilgi>
kullanılabilir.
Örnek:
/forget eski login bug workaround
## 20. Hafıza Temizliği
Qwen Code'un güncel hafıza sisteminde tekrar eden veya eski bilgileri düzenlemek için otomatik consolidation mekanizması bulunabilir.
Desteklenen sürümlerde:
/dream
komutu bu temizleme işlemini manuel olarak başlatabilir.
## 21. QWEN.md ile Auto-Memory Aynı Şey Değildir
QWEN.md:
Kullanıcının açıkça yazdığı kalıcı talimatlardır.
Auto-memory:
Qwen Code'un konuşmalardan yararlı gördüğü bilgileri otomatik çıkarmasıdır.
Kritik proje kuralları için yalnız auto-memory'ye güvenmek yerine QWEN.md kullanmak daha uygundur.
## 22. Proje Ayarları
Qwen Code proje seviyesinde:
.qwen/settings.json
dosyasını kullanabilir.
Bu dosya QWEN.md ile aynı amaçta değildir.
QWEN.md modele verilen proje context ve talimatları içindir.
settings.json ise Qwen Code davranış ve yapılandırma ayarları içindir.
## 23. Kullanıcı Ayarları
Global kullanıcı ayarları tipik olarak:
~/.qwen/settings.json
içerisinde tutulabilir.
Bunlar kullanıcının bütün Qwen Code oturumlarını etkileyebilir.
## 24. Windows Sistem Ayarları
Sistem yöneticisi seviyesindeki Qwen Code ayarları Windows üzerinde:
C:\ProgramData\qwen-code\
altında bulunabilir.
Sistem ayarları kullanıcı veya proje ayarlarını override edebileceğinden sorun giderirken configuration precedence önemlidir.
## 25. Configuration Önceliği
Qwen Code yapılandırmasında genel olarak farklı seviyeler bulunur:
Default -> System Defaults -> User -> Project -> System -> Environment Variables -> Command Line
Daha yüksek öncelikli yapılandırma daha düşük seviyedeki değeri override edebilir.
## 26. Environment Variable Kullanımı
settings.json içerisindeki bazı string değerler environment variable referansı kullanabilir.
Örnek yapı:
$MY_API_TOKEN
veya:
${MY_API_TOKEN}
Bu yöntem secret değerlerini doğrudan repository içerisindeki ayar dosyasına yazmamak için yararlı olabilir.
## 27. Secret Bilgileri QWEN.md İçerisine Yazmayın
QWEN.md repository ile commit edilebilir.
Bu nedenle:
- API key
- password
- access token
- private key
- database credential
gibi secret bilgileri QWEN.md içerisine koymayın.
## 28. Team Memory
Qwen Code'un güncel sürümlerinde ekip üyeleri arasında paylaşılabilen proje hafızası özellikleri bulunabilir.
Bu özellik kullanılıyorsa repository içerisinde paylaşılacak hafıza verilerini commit öncesinde incelemek önemlidir.
## 29. Context Boyutunu Kontrol Edin
Çok büyük QWEN.md dosyaları her oturumda gereksiz context tüketebilir.
Yalnız modelin kararlarını gerçekten etkileyen bilgileri ekleyin.
Uzun teknik belgeleri ayrı dosyalarda tutup gerektiğinde referanslamak daha uygun olabilir.
## 30. Context Compaction
Uzun oturumlarda context penceresi dolabilir.
Qwen Code context kullanımını azaltmak için conversation compaction özellikleri kullanabilir.
Desteklenen sürümlerde:
/compress
gibi komutlar kullanılabilir.
## 31. Context Kullanımını Görme
Güncel sürümlerde:
/context
context kullanımının genel durumunu gösterebilir.
Daha ayrıntılı görünüm destekleniyorsa:
/context detail
kullanılabilir.
## 32. QWEN.md İçin İyi İçerik
İyi örnek:
Bu proje Godot 4.x kullanır.
GDScript yerine mevcut C# mimarisini koru.
Her değişiklikten sonra ilgili testleri çalıştır.
Android export davranışını bozma.
## 33. QWEN.md İçin Kötü İçerik
Kötü örnek:
Her şeyi mükemmel yap.
Asla hata yapma.
Çok iyi kod yaz.
Bu tür ifadeler doğrulanabilir teknik davranış tanımlamaz.
## 34. Değişmeyen Kuralları Yazın
QWEN.md özellikle uzun süre geçerli olacak bilgiler için uygundur.
Örneğin:
- build komutu
- test sistemi
- mimari kısıtlar
- naming convention
- güvenlik kuralları
- deployment yöntemi
## 35. Geçici Görevleri QWEN.md'ye Yazmayın
Örnek:
Bugün login butonunu düzelt.
Bu bir proje hafızası değil, mevcut oturum görevidir.
Geçici işleri normal prompt olarak vermek daha uygundur.
## 36. Eski Bilgileri Temizleyin
Proje zamanla değişebilir.
Örneğin:
.NET 9 -> .NET 10
Webpack -> Vite
SQLite -> PostgreSQL
QWEN.md eski mimariyi anlatmaya devam ederse model yanlış karar verebilir.
## 37. Branch ve Worktree Kullanımı
Aynı repository üzerinde farklı branch veya worktree kullanırken ortak hafıza yararlı olabilir.
Ancak branch'e özel mimari değişiklikler varsa hafıza bilgisinin hâlâ geçerli olduğunu doğrulayın.
## 38. Hafıza Sorunu Giderme
Qwen Code kurallarınızı unutuyor görünüyorsa:
1. QWEN.md doğru yerde mi?
2. /memory içerisinde görünüyor mu?
3. Context yeniden yüklendi mi?
4. Birden fazla QWEN.md çelişiyor mu?
5. Talimat yeterince açık mı?
6. Proje doğru klasörden mi başlatıldı?
## 39. QWEN.md Başlangıç Şablonu
Örnek:
# Project
Projenin kısa açıklaması.
# Stack
Kullanılan teknolojiler.
# Build
Gerçek build komutu.
# Tests
Gerçek test komutu.
# Architecture
Kritik mimari bilgiler.
# Rules
Değiştirilmemesi gereken davranışlar.
# Validation
Görevin tamamlanmış sayılması için gerekli testler.
## 40. Başarı Kriteri
İyi bir proje context sistemi şu zinciri sağlamalıdır:
QWEN.md mevcut -> Qwen Code dosyayı yükledi -> Talimat context içerisinde görünüyor -> Model talimatı uyguluyor -> Proje değiştiğinde context güncelleniyor
## Kaynaklar
Qwen Code resmi dokümantasyonu:
https://qwenlm.github.io/qwen-code-docs/
Qwen Code resmi repository:
https://github.com/QwenLM/qwen-code
## Sonuç
QWEN.md ve Qwen Code hafıza sistemi, aynı proje üzerinde uzun süre çalışırken her oturumda bütün kuralları yeniden anlatma ihtiyacını azaltabilir.
En iyi sonuç için kritik ve kalıcı proje kurallarını QWEN.md içerisinde açık şekilde tutun, geçici görevleri normal prompt olarak verin ve proje değiştikçe eski context bilgilerini güncelleyin.
