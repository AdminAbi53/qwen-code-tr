# Qwen Code Türkçe - Katkı Fikirleri
Bu belge, Qwen Code Türkçe projesine katkıda bulunmak isteyen geliştiriciler için yapılabilecek çalışmaların örneklerini içerir.
Bu proje bağımsız bir Türkçe topluluk dokümantasyonu çalışmasıdır.
## Başlangıç Seviyesi Katkılar
Projeye katkı yapmak için ileri seviye geliştirici olmak gerekmez.
Yapılabilecek basit katkılar:
- yazım hatalarını düzeltmek
- anlatımı iyileştirmek
- bozuk bağlantıları düzeltmek
- eksik kaynak bağlantıları eklemek
- güncelliğini kaybetmiş bilgileri bildirmek
- Markdown biçimlendirmesini düzeltmek
## Dokümantasyon Katkıları
Yeni Türkçe rehberler hazırlanabilir.
Örnek konular:
- Linux kurulumu
- macOS kurulumu
- WSL kullanımı
- Docker kullanımı
- GitHub entegrasyonu
- farklı model sağlayıcıları
- gelişmiş MCP örnekleri
- agent kullanım senaryoları
- büyük repository kullanımı
- context yönetimi
## Gerçek Kullanım Örnekleri
Gerçek projeler üzerinde denenmiş örnekler özellikle değerlidir.
Örnek:
Qwen Code ile bir .NET projesindeki build hatasının bulunması ve düzeltilmesi.
Örnek:
Qwen Code ile bir Node.js projesinin analiz edilmesi.
Örnek:
Yerel model kullanılarak bir Python projesinde test oluşturulması.
## Windows Testleri
Windows kullanıcıları aşağıdaki alanlarda katkıda bulunabilir:
- PowerShell
- Windows Terminal
- PATH sorunları
- Node.js kurulumu
- Git kurulumu
- LM Studio
- Ollama
- yerel API bağlantıları
- firewall sorunları
## Linux Testleri
Linux kullanıcıları:
- dağıtım bazlı kurulum
- shell farklılıkları
- package manager
- permission
- local model server
konularında test edilmiş bilgiler ekleyebilir.
## macOS Testleri
macOS kullanıcıları:
- Homebrew
- Node.js
- Git
- Ollama
- Apple Silicon
- local model
konularında gerçek test sonuçları sağlayabilir.
## Yerel Model Testleri
Farklı modeller Qwen Code ile gerçek görevlerde test edilebilir.
Testlerde şu bilgiler yararlı olabilir:
- model adı
- quantization
- RAM
- VRAM
- context
- model server
- tool calling sonucu
- görev sonucu
## Model Test Şablonu
Örnek:
Model:
Model Server:
Donanım:
RAM:
VRAM:
Context:
Görev:
Tool Calling:
Build:
Test:
Sonuç:
Notlar:
## MCP Katkıları
Gerçek MCP entegrasyonları belgelenebilir.
Her örnekte mümkün olduğunda:
- MCP server adı
- resmi kaynak
- kurulum
- configuration
- sağlanan tools
- izinler
- güvenlik notları
- gerçek test
bulunmalıdır.
## Hata Çözme Katkıları
Gerçek bir hata çözüldüğünde hata çözme rehberine eklenebilir.
İyi hata kaydı:
Belirti -> Hata Mesajı -> Root Cause -> Çözüm -> Doğrulama
şeklinde hazırlanabilir.
## Sürüm Güncelleme Katkıları
Qwen Code yeni sürüm çıkardığında:
- breaking changes
- yeni komutlar
- kaldırılan komutlar
- yeni provider özellikleri
- MCP değişiklikleri
- memory değişiklikleri
incelenebilir.
## Kaynak Doğrulama
Teknik bilgi eklerken mümkün olduğunda resmi kaynak kullanın.
Öncelik:
1. resmi Qwen Code dokümantasyonu
2. resmi Qwen Code repository
3. resmi release notes
4. ilgili aracın resmi dokümantasyonu
5. güvenilir topluluk kaynakları
## Issue Açmak
Kod veya belge değiştirmeden de katkıda bulunabilirsiniz.
Issue açılabilecek konular:
- yanlış bilgi
- eski bilgi
- bozuk bağlantı
- eksik rehber
- anlaşılmayan bölüm
- yeni içerik önerisi
## Pull Request
Bir değişiklik hazırladıysanız Pull Request gönderebilirsiniz.
Pull Request açıklamasında:
- ne değiştirildi
- neden değiştirildi
- hangi kaynak kullanıldı
- gerçek ortamda test edilip edilmediği
belirtilebilir.
## Güvenlik
Katkı gönderirken gerçek:
- API key
- access token
- password
- private key
- cookie
- credential
paylaşmayın.
Yanlışlıkla secret commit edildiğinde ilgili secret derhal iptal edilmelidir.
## Lisans
Katkıda bulunduğunuz içeriğin bu repository'nin lisansı altında yayımlanmasına uygun olduğundan emin olun.
Başka projelerin dokümantasyonunu izinsiz şekilde kopyalamayın.
Teknik bilgileri kendi anlatımınızla açıklayın ve gerektiğinde kaynak gösterin.
## Yeni Başlayanlar İçin Önerilen Katkılar
İlk katkı için şu görevlerden biri seçilebilir:
- bir yazım hatasını düzelt
- bozuk link bul
- Windows üzerinde bir komutu doğrula
- README açıklamasını iyileştir
- hata çözme örneği ekle
- yeni bir resmi kaynak ekle
## Deneyimli Kullanıcılar İçin
Daha kapsamlı katkılar:
- gerçek MCP entegrasyonu
- farklı model benchmarkları
- provider karşılaştırması
- agent workflow örnekleri
- büyük proje testleri
- güvenlik rehberleri
- CI doğrulaması
- otomatik link kontrolü
## Gelecek İçerik Fikirleri
Topluluk tarafından geliştirilebilecek yeni belgeler:
- docs/linux-kurulum.md
- docs/macos-kurulum.md
- docs/wsl.md
- docs/docker.md
- docs/github-entegrasyonu.md
- docs/mcp-ornekleri.md
- docs/yerel-model-testleri.md
- docs/agent-workflow-ornekleri.md
- docs/buyuk-projeler.md
## Projenin Temel İlkesi
Katkının büyüklüğünden çok doğruluğu önemlidir.
İyi katkı:
Gerçek ihtiyaç -> Doğru kaynak -> Açık Türkçe anlatım -> Uygulanabilir örnek -> Doğrulama
zincirini mümkün olduğunca korumalıdır.
## Sonuç
Qwen Code Türkçe topluluk projesi, farklı kullanıcıların gerçek deneyimleri ve katkılarıyla daha yararlı hale gelebilir.
Küçük bir düzeltme bile projeye değerli bir katkıdır.
