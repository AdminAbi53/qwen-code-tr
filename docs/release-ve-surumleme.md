# Qwen Code Türkçe - Release ve Sürümleme Rehberi
Bu rehber, Qwen Code Türkçe repository'sinde sürüm oluşturma, release notları hazırlama ve değişiklikleri düzenli takip etme yaklaşımını açıklar.
Bu proje bağımsız bir Türkçe topluluk dokümantasyonu çalışmasıdır.
## 1. Neden Release Oluşturulur?
Release, repository'nin belirli bir noktadaki durumunu işaretlemek için kullanılır.
Dokümantasyon projelerinde release şu amaçlarla yararlı olabilir:
- önemli içerik paketlerini işaretlemek
- hangi rehberlerin hangi tarihte hazır olduğunu göstermek
- değişiklikleri sürüm bazında takip etmek
- kullanıcıların stabil bir içerik durumunu görmesini sağlamak
## 2. Semantic Versioning Mantığı
Yaygın sürüm biçimi:
MAJOR.MINOR.PATCH
Örnek:
0.1.0
0.2.0
1.0.0
Dokümantasyon projesinde kesin kurallar proje ihtiyacına göre belirlenebilir.
## 3. 0.x Sürümleri
Proje henüz erken geliştirme aşamasındaysa:
0.1.0
0.2.0
0.3.0
gibi sürümler kullanılabilir.
Bu, projenin gelişmeye devam ettiğini gösterir.
## 4. İlk Release
Bu repository için uygun ilk release:
v0.1.0
olabilir.
Bu sürüm mevcut temel Türkçe dokümantasyon paketini temsil edebilir.
## 5. Release İçeriği
v0.1.0 içerisinde örnek olarak:
- README
- Windows kurulum rehberi
- temel kullanım
- LM Studio
- Ollama
- OpenAI uyumlu API
- MCP
- agent ve subagent
- hata çözme
- model seçimi
- Windows ipuçları
- prompt örnekleri
- güvenlik
- katkı rehberi
bulunabilir.
## 6. Release Başlığı
Örnek:
Qwen Code Türkçe v0.1.0 - İlk Dokümantasyon Sürümü
## 7. Release Açıklaması
Release notunda:
- sürüm amacı
- yeni içerikler
- önemli notlar
- bilinen eksikler
- sonraki hedefler
yazılabilir.
## 8. Örnek Release Notu
Qwen Code Türkçe v0.1.0
Bu sürüm projenin ilk genel kullanıma açık Türkçe dokümantasyon paketidir.
Eklenen başlıca içerikler:
- Windows kurulum rehberi
- temel kullanım
- LM Studio
- Ollama
- OpenAI uyumlu API
- MCP
- agent ve subagent rehberi
- hata çözme
- model seçimi
- Windows ipuçları
- prompt örnekleri
- güvenlik ve katkı rehberleri
Bu proje bağımsız bir Türkçe topluluk çalışmasıdır ve resmi Qwen projesi değildir.
## 9. CHANGELOG ile Release Arasındaki Fark
CHANGELOG.md repository içindeki sürüm geçmişini tutar.
GitHub Release ise belirli sürümü platform üzerinde yayınlar.
İkisi birlikte kullanılabilir.
## 10. Tag Nedir?
Git tag, repository tarihindeki belirli bir commit'i işaretler.
Örnek:
v0.1.0
Release genellikle bir tag ile ilişkilendirilir.
## 11. Tag İsimlendirme
Yaygın biçim:
v0.1.0
v0.2.0
v1.0.0
Tutarlı bir format kullanmak daha düzenlidir.
## 12. Minor Sürüm
Yeni önemli rehber veya kapsam eklendiğinde minor sürüm artırılabilir.
Örnek:
v0.1.0 -> v0.2.0
Örneğin:
- Linux rehberi
- macOS rehberi
- gelişmiş MCP örnekleri
gibi büyük içerik eklemeleri minor sürüm olabilir.
## 13. Patch Sürüm
Küçük düzeltmeler:
- yazım hatası
- bozuk link
- küçük teknik düzeltme
gibi durumlarda patch sürüm kullanılabilir.
Örnek:
v0.1.0 -> v0.1.1
## 14. Major Sürüm
Proje yeterince olgunlaştığında:
v1.0.0
kullanılabilir.
Bu noktada ana dokümantasyon yapısının stabil olduğu düşünülebilir.
## 15. Release Öncesi Kontrol
Release oluşturmadan önce:
- README güncel mi?
- linkler çalışıyor mu?
- CHANGELOG güncel mi?
- yeni belgeler README'de listelenmiş mi?
- yanlış veya eski bilgi var mı?
- secret var mı?
- Markdown görünümü düzgün mü?
kontrol edilmelidir.
## 16. Broken Link Kontrolü
Özellikle:
Qwen Code resmi repository
Qwen Code resmi docs
LM Studio
Ollama
Node.js
Git
bağlantılarını kontrol edin.
## 17. Markdown Preview
Her önemli dosyada GitHub Preview kullanarak:
- başlıklar
- listeler
- linkler
- kod blokları
kontrol edilmelidir.
## 18. Release Sonrası
Release yayınlandıktan sonra:
- yeni issue'lar
- kullanıcı geri bildirimleri
- upstream Qwen Code değişiklikleri
takip edilebilir.
## 19. Release Değiştirilebilir mi?
GitHub üzerinde release açıklamaları daha sonra güncellenebilir.
Ancak mevcut tag'in temsil ettiği kod/dokümantasyon tarihi korunmalıdır.
## 20. Eski Release Silmek
Eski release'leri gereksiz yere silmek önerilmez.
Sürüm geçmişi projenin gelişimini gösterir.
## 21. Pre-release
Henüz test edilen veya tamamlanmamış sürümler GitHub üzerinde pre-release olarak işaretlenebilir.
Örnek:
v0.2.0-beta
Bu yapı proje büyüdüğünde yararlı olabilir.
## 22. Draft Release
Release yayımlanmadan önce taslak olarak hazırlanabilir.
Bu sayede açıklama ve sürüm içeriği kontrol edilebilir.
## 23. Release Asset
Kod projelerinde binary dosyalar release asset olarak eklenebilir.
Bu repository ağırlıklı olarak dokümantasyon içerdiği için release asset zorunlu değildir.
## 24. Kaynak Arşivleri
GitHub tag oluşturulduğunda source code arşivlerini otomatik sunabilir.
Dokümantasyon repository'si için bu genellikle yeterlidir.
## 25. Release Notlarında Doğruluk
Gerçekte eklenmemiş bir özelliği release notuna yazmayın.
Sadece repository içerisinde gerçekten mevcut olan içerikleri listeleyin.
## 26. Yapay Aktivite Oluşturmayın
Sırf repository aktif görünsün diye anlamsız release, commit veya tag üretmek yerine gerçek içerik güncellemeleri yapın.
## 27. Bakım Sıklığı
Release sıklığı sabit olmak zorunda değildir.
Yeni anlamlı içerik oluştuğunda release hazırlanabilir.
## 28. Upstream Sürümler
Qwen Code kendi upstream sürümlerini yayınlayabilir.
Bu repository'nin sürümü Qwen Code sürümüyle aynı olmak zorunda değildir.
Örneğin:
Qwen Code vX
Qwen Code Türkçe docs v0.2.0
birbirinden bağımsız olabilir.
## 29. Upstream Uyumluluk Notu
Belirli rehberler yalnız belirli Qwen Code sürümleriyle doğrulandıysa release notuna bu bilgi eklenebilir.
## 30. Sürüm Tarihi
CHANGELOG içerisinde sürüm tarihi tutulması faydalıdır.
Örnek:
## [0.1.0] - 2026-08-11
## 31. GitHub Release Oluşturma Akışı
Genel akış:
Repository -> Releases -> Draft a new release -> Tag seç veya oluştur -> Başlık -> Açıklama -> Publish release
GitHub arayüzü zaman içinde değişebilir.
## 32. v0.1.0 İçin Önerilen Açıklama
Qwen Code Türkçe'nın ilk dokümantasyon sürümü.
Bu sürüm Windows kurulumu, temel kullanım, yerel model entegrasyonları, MCP, agent/subagent, sorun giderme, model seçimi, güvenlik ve katkı rehberlerini içerir.
Proje bağımsız bir Türkçe topluluk çalışmasıdır ve resmi Qwen projesi değildir.
## 33. Sonraki Sürüm Hedefi
v0.2.0 için örnek hedefler:
- Linux kurulumu
- macOS kurulumu
- WSL
- Docker
- GitHub entegrasyonu
- gerçek MCP örnekleri
- gerçek model testleri
## 34. Release Kalitesi
Release sayısından çok içerik kalitesi önemlidir.
İyi release:
Anlamlı değişiklik -> Güncel CHANGELOG -> Kontrol edilmiş belgeler -> Açık release notu -> Doğru tag
## 35. Sonuç
Release ve sürümleme sistemi Qwen Code Türkçe projesinin gelişimini düzenli ve şeffaf biçimde takip etmeyi kolaylaştırır.
İlk kapsamlı dokümantasyon paketi için v0.1.0 uygun bir başlangıç sürümü olabilir.
