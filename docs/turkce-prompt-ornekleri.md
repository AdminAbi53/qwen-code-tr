# Qwen Code Türkçe - Hazır Prompt Örnekleri
Bu belge, Qwen Code kullanan Türkçe geliştiriciler için doğrudan kullanılabilecek görev örneklerini toplar.
Bu depo Qwen ekibinin resmi projesi değildir. Bağımsız bir Türkçe topluluk dokümantasyonu çalışmasıdır.
## 1. Projeyi Analiz Et
Bu projeyi baştan sona incele.
Kullanılan teknolojileri, klasör yapısını, ana giriş noktalarını, servisleri, veri akışını, dependency'leri ve test sistemini belirle.
Henüz hiçbir dosyayı değiştirme.
Sonunda bana projenin mimarisini ve dikkat edilmesi gereken teknik noktaları özetle.
## 2. Hata Bul ve Düzelt
Bu projede oluşan hatayı çöz.
Önce gerçek hata çıktısını incele.
Tahmine göre dosya değiştirme.
İlgili kod akışını takip et.
Root cause'u belirle.
En küçük güvenli düzeltmeyi uygula.
Build ve test çalıştır.
Hata devam ediyorsa görevi tamamlanmış sayma.
## 3. Build Hatasını Çöz
Projeyi gerçek ortamda build et.
Build başarısızsa ilk gerçek hata kaynağını belirle.
Eksik dependency, yanlış SDK, toolchain veya source problemi varsa çöz.
Build başarılı olana kadar aynı görevi takip et.
Sonunda kullanılan build komutunu ve sonucu raporla.
## 4. Testleri Düzelt
Bu projenin testlerini çalıştır.
Başarısız testleri grupla.
Zincirleme hatalar varsa ana root cause'u önce çöz.
Test kodunu yalnız gerçek davranış yanlışsa değiştir.
Uygulamadaki bug'ı testleri geçmek için gizleme.
Bütün ilgili testler başarıyla tamamlandığında sonucu raporla.
## 5. Yeni Özellik Ekle
Bu projeye şu özelliği ekle:
[İSTENEN ÖZELLİĞİ BURAYA YAZ]
Önce mevcut mimariyi incele.
Yeni özelliğin hangi katmana eklenmesi gerektiğini belirle.
Mevcut çalışan özellikleri bozma.
Gereksiz dependency ekleme.
Implementasyondan sonra build, test ve gerçek kullanım doğrulaması yap.
## 6. Performans Sorununu Bul
Bu uygulamadaki performans problemini araştır.
Önce ölçüm yapmadan optimizasyon uygulama.
CPU, RAM, disk, ağ ve varsa GPU kullanımını incele.
Darboğazı kanıtla.
Sonra en uygun optimizasyonu uygula.
Öncesi ve sonrası sonucu karşılaştır.
## 7. Refactoring Yap
Bu modülü refactor et.
Amaç:
- tekrar eden kodları azaltmak
- okunabilirliği artırmak
- sorumlulukları ayırmak
- bakım maliyetini azaltmak
Mevcut dış davranışı değiştirme.
Public API'leri gereksiz yere değiştirme.
Refactoring sonrasında bütün ilgili testleri tekrar çalıştır.
## 8. Güvenlik İncelemesi
Bu projeyi güvenlik açısından incele.
Özellikle:
- secret kullanımı
- authentication
- authorization
- input validation
- dependency güvenliği
- file access
- network access
- command execution
alanlarını kontrol et.
Bulduğun riskleri önem derecesine göre sırala.
Doğrulanmamış güvenlik açığı iddiası üretme.
## 9. Dependency Analizi
Projede kullanılan dependency'leri incele.
Gereksiz, eski veya artık kullanılmayan paketleri belirle.
Yeni sürüme geçiş gerekiyorsa breaking change risklerini kontrol et.
Sadece sürüm numarası yüksek diye dependency güncelleme.
Güncelleme sonrası build ve test yap.
## 10. Güncel Resmi Kaynak Araştırması
Bu göreve başlamadan önce kullanılan teknoloji hakkında güncel resmi dokümantasyonu araştır.
Öncelik sırası:
1. resmi dokümantasyon
2. resmi repository
3. resmi release notes
4. güvenilir issue ve maintainer açıklamaları
Araştırma sonucuna göre en uygun yöntemi seç.
Deprecated yöntem kullanma.
## 11. Eksik Araç Varsa Kur
Görevi tamamlamak için gerekli bir tool, SDK, compiler veya dependency eksikse bunu sadece raporlayıp durma.
Önce eksikliği doğrula.
Resmi kaynağını araştır.
Güvenli kurulum yöntemini belirle.
Kur.
Kurulumu gerçek komutla doğrula.
Sonra ana göreve kaldığın yerden devam et.
## 12. Agent Döngüye Girerse
Aynı komut, aynı dosya araması veya aynı strateji yeni kanıt üretmeden tekrar ediliyorsa mevcut yöntemi bırak.
Son başarılı checkpoint'i belirle.
Başarısız varsayımları listele.
Yeni bir root-cause hipotezi oluştur.
Farklı bir yöntemle doğrula.
Yeni evidence üretmeden aynı semantic stratejiyi tekrar etme.
## 13. Projeyi Production Seviyesine Getir
Bu projeyi production kullanıma hazırlamak için incele.
Şunları kontrol et:
- build
- test
- runtime
- configuration
- error handling
- logging
- security
- performance
- dependency
- persistence
- restart davranışı
- documentation
Eksikleri önem sırasına göre gider.
Sadece testlerin yeşil olmasıyla görevi tamamlanmış sayma.
Gerçek kullanıcı senaryosunu çalıştır ve sonucu doğrula.
## 14. Kod Yazmadan Önce Planla
Bu görevi hemen kodlamaya başlama.
Önce:
- hedefi belirle
- acceptance criteria oluştur
- ilgili dosyaları bul
- dependency'leri incele
- olası riskleri belirle
- uygulanacak adımları sırala
Plan netleştikten sonra implementasyona geç.
## 15. Minimum Güvenli Değişiklik
Bu sorunu çözmek için gerekli minimum güvenli değişikliği yap.
İlgisiz dosyalara dokunma.
Mevcut davranışı gereksiz yere değiştirme.
Yeni mimari yalnız gerçekten gerekiyorsa ekle.
Düzeltme sonrası regression kontrolü yap.
## 16. Gerçek Doğrulama
Bir işlemi yalnız:
PASS
SUCCESS
DONE
READY
metni üretildiği için tamamlanmış kabul etme.
Gerçek başarı için mümkün olduğunda:
- gerçek source değişikliği
- gerçek build
- gerçek test
- gerçek runtime
- beklenen artifact
- kullanıcıya gözlemlenebilir doğru sonuç
kanıtı üret.
## 17. Türkçe Açıklama İsteği
Teknik işlemleri gerçekleştirirken bana kısa ve anlaşılır Türkçe durum bilgisi ver.
Sadece:
PowerShell çalıştı
veya:
Komut tamamlandı
deme.
Şunları açıkla:
- neyi kontrol ettin
- ne buldun
- neden o yöntemi seçtin
- sıradaki adım ne
Teknik detayları gerektiğinde ayrıca göster.
## 18. Büyük Projeyi Parçalara Böl
Bu büyük görevi bağımlılıklarına göre alt görevlere böl.
Birbirinden bağımsız işler varsa paralel yürütülebilecek şekilde grupla.
Her alt görev için:
- hedef
- gerekli capability
- acceptance criteria
- beklenen artifact
tanımla.
Sonuçları finalde tekrar birleştir.
## 19. Yeni Agent Oluştur
Şu uzmanlıkta yeni agent oluştur:
[UZMANLIK]
Önce bu uzmanlık için gerekli gerçek capability'leri araştır.
Agent'ı yalnız prompt olarak oluşturma.
Gerekli araçları ve environment'ı doğrula.
Gerçek uzmanlık testleri çalıştır.
Independent validator ile kontrol et.
Restart sonrası tekrar kullanılabildiğini doğrula.
Ancak bütün testler geçtiğinde Ready yap.
## 20. Genel Güçlü Görev Şablonu
GÖREV:
[Yapılmasını istediğiniz işi yazın]
HEDEF:
[Ortaya çıkması gereken sonucu yazın]
MEVCUT DURUM:
[Şu anki sistemi açıklayın]
SORUN:
[Varsa problemi yazın]
KURALLAR:
- Önce araştır ve analiz et.
- Tahmine göre değişiklik yapma.
- Mevcut çalışan özellikleri bozma.
- Gereksiz dependency ekleme.
- Eksik tool varsa resmi kaynaktan edin ve doğrula.
- Aynı başarısız yöntemi tekrar etme.
- Gerçek evidence üret.
DOĞRULAMA:
- Build
- Test
- Runtime
- Acceptance criteria
- Regression
TAMAMLANMA KRİTERİ:
Görevi yalnız istenen gerçek sonuç çalışıyor ve doğrulanmışsa tamamlanmış kabul et.
