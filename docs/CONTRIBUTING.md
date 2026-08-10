# Qwen Code Türkçe - Katkıda Bulunma Rehberi
Qwen Code Türkçe projesine katkıda bulunmak istediğiniz için teşekkür ederiz.
Bu proje, Qwen Code için Türkçe dokümantasyon, kurulum rehberleri, kullanım örnekleri ve sorun giderme kaynakları oluşturmayı amaçlayan bağımsız bir topluluk çalışmasıdır.
Bu depo Qwen ekibinin resmi projesi değildir.
## Nasıl Katkıda Bulunabilirsiniz?
Aşağıdaki alanlarda katkı sağlayabilirsiniz:
- Türkçe dokümantasyon yazımı
- Mevcut belgelerde yazım düzeltmeleri
- Teknik bilgilerin güncellenmesi
- Windows kurulum testleri
- Linux kurulum testleri
- macOS kurulum testleri
- LM Studio kullanım örnekleri
- Ollama kullanım örnekleri
- MCP kullanım örnekleri
- Qwen Code hata çözümleri
- Yerel model yapılandırmaları
- Agent ve subagent kullanım örnekleri
- Yeni başlayanlar için rehberler
- Gerçek kullanım senaryoları
## Issue Açma
Bir hata, eksik bilgi veya yeni dokümantasyon öneriniz varsa GitHub Issues bölümünden yeni bir issue açabilirsiniz.
Issue içerisinde mümkünse şu bilgileri belirtin:
Başlık:
Sorun veya öneri:
İlgili doküman:
Kullanılan işletim sistemi:
Qwen Code sürümü:
Varsa hata mesajı:
Önerilen çözüm:
API key, password, access token veya diğer gizli bilgileri issue içerisine eklemeyin.
## Dokümantasyon Düzeltmesi
Bir belgede yanlış veya güncelliğini kaybetmiş bilgi görürseniz düzeltme önerebilirsiniz.
Örneğin:
- eski komut
- değişmiş kurulum yöntemi
- yanlış bağlantı
- yazım hatası
- eksik açıklama
- artık desteklenmeyen özellik
Değişiklik yaparken mümkün olduğunda Qwen Code'un güncel resmi dokümantasyonunu kaynak olarak kullanın.
## Yeni Rehber Eklemek
Yeni rehberler mümkün olduğunca docs klasörü altında tutulmalıdır.
Örnek:
docs/kurulum.md
docs/kullanim.md
docs/mcp.md
docs/lm-studio.md
docs/hata-cozumleri.md
Yeni belge adları kısa, anlaşılır ve Türkçe olmalıdır.
## Yazım Dili
Ana dokümantasyon dili Türkçedir.
Teknik kavramların yaygın İngilizce karşılıkları gerektiğinde korunabilir.
Örnek:
- dependency
- build
- runtime
- API
- endpoint
- tool calling
- context
- agent
- subagent
- MCP
Ama açıklamalar mümkün olduğunca anlaşılır Türkçe ile yazılmalıdır.
## Kaynak Kullanımı
Başka projelerin dokümantasyonlarını doğrudan kopyalamayın.
Bilgileri araştırabilir ve teknik gerçekleri kaynak alabilirsiniz ancak metinleri özgün şekilde yazın.
Öncelikli kaynaklar:
- Qwen Code resmi repository
- Qwen Code resmi dokümantasyonu
- ilgili teknolojinin resmi dokümantasyonu
- güvenilir açık kaynak proje kaynakları
## Pull Request
Bir değişiklik hazırladıysanız Pull Request açabilirsiniz.
Pull Request açıklamasında şunları belirtmeniz faydalıdır:
- ne değiştirildi
- neden değiştirildi
- hangi belge etkilendi
- bilgi hangi kaynakla doğrulandı
- varsa test edilen ortam
Örnek başlık:
Update Turkish Windows installation guide
Örnek açıklama:
Qwen Code Windows kurulum rehberindeki eski Node.js açıklaması güncellendi ve kurulum doğrulama adımları genişletildi.
## Teknik Doğruluk
Bir komutun yalnızca internette bulunması doğru olduğu anlamına gelmez.
Mümkün olduğunda:
- resmi kaynağı kontrol edin
- güncel sürümü kontrol edin
- komutu gerçek ortamda test edin
- eski sürümlere ait bilgileri güncel bilgi gibi sunmayın
## Güvenlik
Aşağıdaki bilgileri hiçbir commit, issue veya pull request içerisinde paylaşmayın:
- API key
- access token
- password
- private key
- authentication cookie
- database password
- özel sunucu credential bilgileri
Yanlışlıkla secret paylaşırsanız ilgili anahtarı derhal iptal edin.
## Davranış
Katkıda bulunanlardan:
- saygılı iletişim
- yapıcı geri bildirim
- teknik tartışmalarda kişisel saldırılardan kaçınma
- yeni başlayan kullanıcılara yardımcı olma
beklenir.
## Lisans
Bu projeye gönderilen katkılar repository'nin Apache License 2.0 lisansı kapsamında yayımlanabilir.
Katkı göndererek eklediğiniz içeriği bu lisans kapsamında paylaşmaya yetkili olduğunuzu kabul etmiş olursunuz.
## Hedef
Amacımız yalnızca Qwen Code belgelerini Türkçeye çevirmek değildir.
Hedefimiz Türkçe konuşan kullanıcıların Qwen Code'u gerçekten kurabilmesini, kullanabilmesini, sorunlarını çözebilmesini ve gelişmiş özelliklerini öğrenebilmesini sağlayan sürdürülebilir bir topluluk kaynağı oluşturmaktır.
