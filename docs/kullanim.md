# Qwen Code Türkçe — Kullanım Rehberi

Bu rehber, Qwen Code'u günlük yazılım geliştirme çalışmalarında daha verimli ve güvenli kullanmak isteyen Türkçe konuşan kullanıcılar için hazırlanmıştır.

> [!IMPORTANT]
> Bu depo Qwen ekibinin resmi projesi değildir. Bağımsız bir Türkçe topluluk dokümantasyonu çalışmasıdır.

---

## 1. Qwen Code'u Bir Projede Başlatma

Öncelikle PowerShell veya Windows Terminal ile proje klasörüne geçin.

Örnek:

```powershell
cd C:\Projeler\BenimUygulamam
```

Ardından Qwen Code'u başlatın:

```powershell
qwen
```

Qwen Code artık bulunduğunuz proje klasörünü çalışma alanı olarak kullanabilir.

---

## 2. İlk Görev: Önce Projeyi Anlatmasını İsteyin

Özellikle mevcut ve büyük projelerde doğrudan kod değiştirtmek yerine önce projeyi analiz ettirmek daha güvenlidir.

Örnek:

```text
Bu projeyi ayrıntılı olarak incele.

Önce:
- klasör yapısını,
- kullanılan programlama dillerini,
- framework ve kütüphaneleri,
- uygulamanın başlangıç noktasını,
- önemli servisleri,
- veri akışını,
- test sistemini

belirle.

Henüz hiçbir dosyayı değiştirme.

İnceleme bittikten sonra bana projenin mimarisini özetle.
```

---

## 3. Doğal Dille Görev Verme

Qwen Code'a normal konuşma diliyle görev verebilirsiniz.

Örnek:

```text
Bu uygulamadaki giriş ekranını incele ve kullanıcı giriş yaptıktan sonra neden ana sayfaya yönlendirilmediğini bul.
```

Daha kapsamlı örnek:

```text
Kullanıcı giriş sisteminde bir hata var.

Önce mevcut authentication akışını incele.
Problemin gerçek nedenini belirle.
Tahmine göre dosya değiştirme.

Sorunu bulduktan sonra gerekli kod değişikliklerini yap.
Projeyi derle.
İlgili testleri çalıştır.
Başarısız test varsa nedenini araştır ve düzelt.

Sonunda değiştirdiğin dosyaları ve yaptığın işlemleri özetle.
```

---

## 4. İyi Bir Görev Nasıl Yazılır?

İyi bir görev genellikle dört temel bölümden oluşur:

```text
HEDEF
+
MEVCUT PROBLEM
+
KISITLAMALAR
+
BAŞARI KRİTERİ
```

Örnek:

```text
HEDEF:
Uygulamaya karanlık tema ekle.

MEVCUT DURUM:
Uygulama yalnızca açık tema kullanıyor.

KISITLAMA:
Mevcut business logic ve API servislerini değiştirme.

BAŞARI KRİTERİ:
Kullanıcı Ayarlar bölümünden açık/koyu tema arasında geçiş yapabilmeli ve tercih uygulama yeniden açıldığında korunmalı.
```

---

## 5. Hata Araştırma

Hata mesajını mümkün olduğunca eksiksiz verin.

```text
Uygulamayı çalıştırırken aşağıdaki hata oluşuyor:

[HATA MESAJINI BURAYA YAPIŞTIR]

Önce hata mesajını analiz et.
İlgili kaynak dosyaları ve bağımlılıkları kontrol et.
Root cause'u belirle.

Tahmine dayalı değişiklik yapma.

Sorunu düzelttikten sonra aynı senaryoyu yeniden test et.
```

---

## 6. Kod Analizi

```text
Bu projedeki kullanıcı doğrulama sistemini incele.

İlgili bütün dosyaları bul ve bana:

- giriş işleminin nereden başladığını,
- kullanıcı bilgilerinin nerede doğrulandığını,
- token'ın nerede üretildiğini,
- token'ın nerede saklandığını,
- logout işleminin nasıl gerçekleştiğini

açıkla.

Henüz kod değiştirme.
```

---

## 7. Yeni Özellik Ekletme

```text
Bu projeye merkezi bir logging servisi ekle.

Gereksinimler:

- hata kayıtlarını desteklesin,
- warning ve info seviyeleri olsun,
- log dosyalarını tarih bazlı saklasın,
- mevcut mimariye uygun olsun,
- mevcut logging sistemi varsa duplicate sistem oluşturma,
- uygulamanın mevcut davranışını bozma.

Implementasyondan sonra gerçek kullanım testi yap.
```

---

## 8. Refactoring

```text
Bu modülü refactor et.

Amaç:

- tekrar eden kodları azaltmak,
- okunabilirliği artırmak,
- sorumlulukları ayırmak.

Kurallar:

- mevcut dış davranışı değiştirme,
- public API'leri gereksiz yere değiştirme,
- mevcut testleri bozma,
- refactoring sonrasında testleri yeniden çalıştır.
```

---

## 9. Test Yazdırma

```text
Bu servisin mevcut davranışını analiz et ve kritik davranışları kapsayan testler oluştur.

Şunları kapsa:

- normal kullanım,
- boş değerler,
- geçersiz giriş,
- hata durumları,
- sınır değerler.

Testleri gerçekten çalıştır.
Yalnızca test dosyası oluşturmakla görevi tamamlanmış sayma.
```

---

## 10. Derleme ve Doğrulama

Kodun yazılmış olması görevin tamamlandığı anlamına gelmez.

```text
Değişikliklerden sonra projeyi gerçek ortamda derle.

Derleme hatası varsa düzelt.

İlgili testleri çalıştır.

Test başarısızsa başarısızlığın nedenini araştır.

Görevi yalnızca:

- build başarılı,
- ilgili testler başarılı,
- istenen özellik doğrulanmış

olduğunda tamamlanmış kabul et.
```

---

## 11. Git ile Değişiklikleri Kontrol Etme

Durumu kontrol etmek için:

```powershell
git status
```

Değişiklikleri görmek için:

```powershell
git diff
```

Değişiklikler doğruysa:

```powershell
git add .
git commit -m "Implement requested changes"
```

---

## 12. Büyük Görevleri Aşamalara Bölme

```text
Bu projeye kullanıcı hesap sistemi ekle.

Önce mevcut mimariyi incele.

Daha sonra görevi uygulanabilir aşamalara böl:

1. veri modeli,
2. authentication servisi,
3. API,
4. kullanıcı arayüzü,
5. hata yönetimi,
6. testler,
7. güvenlik kontrolleri.

Planı oluşturduktan sonra bağımlılık sırasına göre uygula.

Her aşamadan sonra doğrulama yap.
```

---

## 13. Mevcut Özellikleri Korumak

```text
Bu özelliği eklerken mevcut çalışan özellikleri bozma.

Değişiklikten önce ilgili mevcut davranışları belirle.

Değişiklikten sonra regression testi yap.

Yeni özellik çalışırken eski özelliklerin de çalıştığını doğrula.
```

---

## 14. Araştırma Gerektiren Görevler

```text
Bu implementasyona başlamadan önce kullandığımız framework'ün güncel resmi dokümantasyonunu kontrol et.

Deprecated yöntem kullanma.

Araştırma sonucuna ve mevcut proje mimarisine göre uygulanabilecek en uygun yöntemi belirle.

Daha sonra implementasyona geç.
```

---

## 15. Bağımlılık Eklerken

```text
Bu özellik için önce mevcut bağımlılıkları incele.

Mevcut kütüphanelerle güvenli şekilde yapılabiliyorsa yeni dependency ekleme.

Yeni dependency gerçekten gerekiyorsa:

- aktif olarak geliştirildiğini,
- lisansını,
- proje ile uyumluluğunu,
- güvenlik durumunu

kontrol et.

Sonra ekle.
```

---

## 16. Güvenli Terminal Kullanımı

Terminal erişimi güçlüdür. Özellikle aşağıdaki işlemlerde dikkatli olun:

- dosya ve klasör silme,
- disk işlemleri,
- registry değişiklikleri,
- yönetici yetkili işlemler,
- paket kurma veya kaldırma,
- firewall değişiklikleri,
- kullanıcı hesapları,
- servis yapılandırmaları.

Örnek güvenlik talimatı:

```text
Mevcut kullanıcı verilerini, veritabanlarını ve production yapılandırmalarını silme veya sıfırlama.

Geri dönüşü zor bir işlem gerekiyorsa önce güvenli alternatifleri değerlendir.
```

---

## 17. API Anahtarları ve Gizli Bilgiler

Public repository içerisine aşağıdaki bilgileri koymayın:

- API key
- access token
- password
- private key
- database password
- secret
- authentication cookie

`.gitignore` örneği:

```gitignore
.env
.env.*
secrets.json
credentials.json
*.key
```

---

## 18. Türkçe Prompt Örnekleri

### Proje Analizi

```text
Bu projeyi baştan sona incele.

Kullanılan teknolojileri, mimariyi, servisleri, bağımlılıkları ve veri akışını belirle.

Potansiyel teknik problemleri de tespit et.

Henüz hiçbir dosyayı değiştirme.
```

### Bug Çözme

```text
Bu hatanın gerçek nedenini bul.

Tahmin ederek değişiklik yapma.

İlgili kod akışını takip et.
Root cause'u belirle.
En küçük güvenli düzeltmeyi uygula.
Build ve test yap.
```

### Yeni Özellik

```text
Bu projeye bildirim sistemi ekle.

Önce mevcut mimariyi incele ve bildirim sisteminin nereye entegre edilmesi gerektiğini belirle.

Mevcut özellikleri bozmadan implementasyonu tamamla.

Sonunda gerçek kullanım senaryosuyla test et.
```

### Performans

```text
Uygulamadaki performans problemini araştır.

Önce ölçüm yapmadan optimizasyon uygulama.

Darboğazı belirle.
Sonra optimizasyon yap.
Öncesi ve sonrası sonucu karşılaştır.
```

---

## 19. Güçlü Görev Şablonu

Karmaşık işler için:

```text
GÖREV:
[Yapılmasını istediğiniz işi yazın]

HEDEF:
[Ortaya çıkması gereken sonucu yazın]

MEVCUT DURUM:
[Şu anda sistemin durumunu açıklayın]

SORUN:
[Varsa mevcut problemi açıklayın]

KURALLAR:
- Önce mevcut sistemi incele.
- Tahmine göre değişiklik yapma.
- Mevcut çalışan özellikleri bozma.
- Gereksiz dependency ekleme.
- Kritik verileri silme.
- Gerçek hata nedenini belirle.

DOĞRULAMA:
- Projeyi derle.
- İlgili testleri çalıştır.
- İstenen davranışı gerçek senaryoda doğrula.
- Regression kontrolü yap.

TAMAMLANMA KRİTERİ:
Görevi yalnızca istenen özellik gerçekten çalışıyor ve doğrulanmışsa tamamlanmış kabul et.
```

---

## 20. Yapay Zekâ Çıktısını Kontrol Etme

Bir ajan yalnızca:

```text
Tamamlandı
PASS
Success
Fixed
```

yazdığı için görevin gerçekten tamamlandığını varsaymayın.

Mümkün olduğunda doğrulama zinciri:

```text
Kaynak kod değişikliği
        ↓
Başarılı build
        ↓
Başarılı test
        ↓
Runtime doğrulaması
        ↓
Beklenen çıktının kontrolü
```

---

## 21. Önerilen Günlük Kullanım Akışı

```text
Görevi tanımla
      ↓
Projeyi analiz ettir
      ↓
Gerekirse güncel bilgiyi araştır
      ↓
Plan oluştur
      ↓
Kod değişikliklerini uygula
      ↓
Build
      ↓
Test
      ↓
Runtime doğrulaması
      ↓
git diff
      ↓
Sonucu incele
      ↓
Commit
```

---

## Sonuç

Qwen Code'dan alınan sonuç; görevin ne kadar açık tanımlandığına, modele sağlanan proje bağlamına ve yapılan değişikliklerin gerçekten doğrulanmasına bağlıdır.

Temel prensip:

**Kod üretmek görevin sonu değildir. Çalışan ve doğrulanmış sonuç görevin sonudur.**

Bu Türkçe dokümantasyon ilerleyen bölümlerde şu konularla genişletilecektir:

- LM Studio
- Yerel yapay zekâ modelleri
- OpenAI uyumlu API sağlayıcıları
- MCP kurulumu
- MCP sunucuları
- Agent ve subagent sistemleri
- Çoklu ajan mimarileri
- Qwen Code hata giderme
- Gelişmiş proje yönetimi
- Windows üzerinde yerel model kullanımı
- Türkçe kullanım örnekleri
