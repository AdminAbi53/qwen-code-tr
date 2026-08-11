# Qwen Code Türkçe - Yerel Model Seçim Rehberi
Bu rehber, Qwen Code ile kullanılacak yerel yapay zeka modelini seçerken dikkat edilmesi gereken temel noktaları açıklar.
Bu depo Qwen ekibinin resmi projesi değildir. Bağımsız bir Türkçe topluluk dokümantasyonu çalışmasıdır.
## 1. En Büyük Model Her Zaman En İyi Model Değildir
Yerel model seçiminde yalnız model boyutuna bakmak doğru değildir.
Daha büyük bir model daha güçlü olabilir ancak bilgisayarın RAM ve VRAM kapasitesini aşıyorsa çok yavaş çalışabilir.
Model seçerken kalite ile donanım gereksinimi arasında denge kurulmalıdır.
## 2. Coding Model Nedir?
Coding modelleri özellikle yazılım geliştirme görevleri için eğitilmiş veya optimize edilmiş modellerdir.
Bu modeller genellikle:
- kod üretme
- kod tamamlama
- hata analizi
- refactoring
- test oluşturma
- farklı programlama dillerini anlama
gibi görevlerde genel amaçlı modellere göre daha uygun olabilir.
## 3. Qwen Code İçin Önemli Model Yetenekleri
Bir coding agent ortamında modelin yalnız iyi kod yazması yeterli değildir.
Önemli yetenekler:
- instruction following
- coding
- tool calling
- structured output
- uzun context
- hata analizi
- tool sonucunu yorumlama
- çok adımlı görev takibi
- Türkçe talimatları anlayabilme
## 4. Tool Calling
Qwen Code gibi agent araçlarında modelin gerçek araç çağrıları üretmesi gerekebilir.
Örneğin:
Dosya oku
Terminal çalıştır
Dosya değiştir
Build yap
Test çalıştır
Bu nedenle tool calling desteği önemli olabilir.
Normal sohbet testinde başarılı olan bir model tool kullanımında başarısız olabilir.
## 5. Structured Output
Bazı agent akışlarında modelden belirli JSON yapıları veya schema uyumlu cevaplar beklenebilir.
Model structured output üretmekte zorlanıyorsa:
- tool çağrıları bozulabilir
- agent planı yanlış parse edilebilir
- orchestration akışı kesilebilir
Bu nedenle model seçiminde structured output kabiliyeti de değerlendirilmelidir.
## 6. Context Uzunluğu
Context, modelin aynı anda görebildiği bilgi miktarını ifade eder.
Büyük yazılım projelerinde yüksek context yararlı olabilir.
Ancak daha yüksek context:
- daha fazla RAM
- daha fazla VRAM
- daha uzun inference süresi
gerektirebilir.
Maksimum desteklenen context değerini her zaman kullanmak gerekli değildir.
## 7. VRAM
GPU belleği yerel model performansında önemli faktörlerden biridir.
Model tamamen veya büyük ölçüde VRAM içerisinde çalışabiliyorsa inference genellikle daha hızlı olur.
Model VRAM kapasitesini aşıyorsa bazı katmanlar sistem RAM veya CPU tarafında çalışabilir.
Bu durumda performans düşebilir.
## 8. Sistem RAM
Sistem RAM miktarı özellikle modelin tamamı VRAM içerisine sığmadığında önem kazanır.
Ayrıca:
- model dosyaları
- context
- işletim sistemi
- Qwen Code
- IDE
- diğer uygulamalar
aynı RAM'i kullanabilir.
Bu nedenle bilgisayarın toplam RAM miktarını model boyutunun tamamına ayırmak mümkün değildir.
## 9. Quantization Nedir?
Quantization modelin daha düşük hassasiyetle saklanarak daha az RAM ve VRAM kullanmasını sağlayan yöntemdir.
Yaygın örnekler:
Q4
Q5
Q6
Q8
Daha düşük quantization genellikle daha az kaynak kullanır.
Ancak model kalitesinde bir miktar düşüş olabilir.
## 10. Quantization Seçimi
Genel yaklaşım:
Daha az VRAM -> daha düşük quantization
Daha fazla VRAM -> daha yüksek kalite seçeneği
Ancak tek doğru değer yoktur.
Modelin gerçek görevlerdeki başarısı test edilmelidir.
## 11. CPU Offload
Model tamamen GPU'ya sığmıyorsa bazı işlemler CPU üzerinde yürütülebilir.
Bu yönteme CPU offload denebilir.
Avantajı:
Daha büyük model çalıştırılabilir.
Dezavantajı:
Inference ciddi şekilde yavaşlayabilir.
## 12. Tokens Per Second
Yerel model performansı genellikle saniyede üretilen token miktarıyla ölçülebilir.
Ancak yalnız yüksek token/s değeri kaliteli coding agent anlamına gelmez.
Bir model hızlı olup:
- yanlış tool çağırabilir
- talimatları unutabilir
- kod hataları üretebilir
- uzun görevlerde başarısız olabilir
Bu nedenle hız ve kalite birlikte değerlendirilmelidir.
## 13. İlk Token Süresi
Büyük context kullanıldığında modelin ilk cevabı üretmesi daha uzun sürebilir.
Buna prompt processing veya time-to-first-token etkisi denebilir.
Büyük repository analizlerinde bu süre normal sohbetten daha yüksek olabilir.
## 14. Küçük Model Ne Zaman Kullanılır?
Küçük modeller şu görevlerde yararlı olabilir:
- hızlı sınıflandırma
- basit kod soruları
- küçük dosya düzenlemeleri
- kısa tool kararları
- basit otomasyon
Avantajları:
- daha az VRAM
- daha hızlı cevap
- daha düşük kaynak tüketimi
## 15. Büyük Model Ne Zaman Kullanılır?
Daha büyük modeller şu görevlerde avantaj sağlayabilir:
- karmaşık mimari analiz
- büyük repository
- çok dosyalı değişiklik
- zor hata analizi
- uzun reasoning gerektiren görevler
- kapsamlı refactoring
Ancak donanım model için yeterli olmalıdır.
## 16. Birden Fazla Model Kullanımı
Gelişmiş agent sistemlerinde her görevin aynı modele verilmesi gerekli değildir.
Örnek:
Fast Agent -> Küçük Model
Coding Agent -> Coder Model
Architecture Agent -> Büyük Reasoning Model
Vision Agent -> Vision Model
Bu yaklaşım kaynakların daha verimli kullanılmasını sağlayabilir.
Gerçek destek kullanılan Qwen Code sürümüne ve agent mimarisine bağlıdır.
## 17. Vision Model
Bir görev:
- ekran görüntüsü
- UI
- diagram
- fotoğraf
- görsel hata
analizi gerektiriyorsa vision destekleyen model gerekebilir.
Normal text-only coding modeli görsel dosyanın içeriğini anlayamayabilir.
## 18. Uzun Context Her Zaman Daha İyi Değildir
Çok fazla gereksiz context modele verilirse:
- cevap yavaşlayabilir
- önemli bilgiler kaybolabilir
- modelin dikkati dağılabilir
- kaynak kullanımı artabilir
Bu nedenle yalnız gerekli proje context'ini modele vermek daha verimli olabilir.
## 19. Model Benchmark Sonuçları
Benchmark sonuçları model karşılaştırmasında yararlı olabilir.
Ancak gerçek Qwen Code kullanımını tam olarak temsil etmeyebilir.
Bir model benchmark'ta yüksek skor alıp:
- tool calling
- Windows kullanımı
- belirli framework
- Türkçe talimat
konularında daha zayıf olabilir.
## 20. Gerçek Test Yapın
Model seçiminin en güvenilir yolu gerçek görevlerle test etmektir.
Örnek test seti:
1. Proje klasörünü analiz et
2. Belirli bir bug'ı bul
3. Küçük kod değişikliği yap
4. Build çalıştır
5. Test çalıştır
6. Tool çağrısı yap
7. Hata aldıktan sonra recovery uygula
8. Uzun görevde hedefi koru
## 21. Model Karşılaştırma Testi
İki modeli karşılaştırırken aynı görevleri kullanın.
Ölçülebilecek değerler:
- görevi tamamlama
- doğru tool kullanımı
- toplam süre
- hata sayısı
- tekrar sayısı
- gerekli kullanıcı müdahalesi
- build sonucu
- test sonucu
- kaynak kullanımı
## 22. Sadece Cevap Kalitesini Ölçmeyin
Coding agent için gerçek başarı:
Güzel açıklama
değil:
Çalışan ve doğrulanmış sonuç
olmalıdır.
Model çok iyi açıklama yapıp gerçek projeyi tamamlayamıyorsa agent kullanımında yetersiz olabilir.
## 23. Türkçe Anlama
Türkçe görev verecekseniz modelin Türkçe talimatları doğru anlayıp anlamadığını test edin.
Örnek:
Bu projeyi incele.
Henüz hiçbir dosyayı değiştirme.
Sadece kullanılan teknolojileri ve mimariyi açıkla.
Model bu sınırlamaya rağmen dosya değiştiriyorsa instruction following problemi olabilir.
## 24. Kodlama Dili Desteği
Kullanacağınız programlama dili model seçiminde önemlidir.
Test edilebilecek diller:
- Python
- C#
- Java
- Kotlin
- C
- C++
- Rust
- Go
- JavaScript
- TypeScript
Modelin sizin gerçek projelerinizde kullandığınız dillerdeki başarısını ölçün.
## 25. Framework Bilgisi
Model programlama dilini bilse bile belirli framework konusunda zayıf olabilir.
Örnek:
.NET
WPF
MAUI
Unity
Godot
Spring
Android
React
Next.js
Flutter
Framework görevlerinde gerçek proje testi yapılmalıdır.
## 26. Güncel Bilgi
Yerel modelin eğitim verisi güncel olmayabilir.
Yeni framework veya sürümlerde model yanlış veya eski bilgi verebilir.
Bu durumda:
Model + Güncel Resmi Dokümantasyon + Research Tool
kombinasyonu daha güvenilir olabilir.
## 27. Hallucination
Model var olmayan:
- API
- method
- package
- command
- configuration
üretebilir.
Bu nedenle teknik iddialar mümkün olduğunda:
- compiler
- runtime
- official docs
- package manager
- source code
ile doğrulanmalıdır.
## 28. Model Döngüsü
Bazı modeller agent görevlerinde aynı tool veya stratejiyi tekrar tekrar kullanabilir.
Belirtiler:
- aynı komut
- aynı dosya araması
- aynı hata açıklaması
- yeni evidence yok
Bu davranış model kalitesi veya orchestration problemi olabilir.
## 29. Model Timeout
Çok büyük model veya context nedeniyle model cevap süresi timeout sınırını aşabilir.
Çözüm seçenekleri:
- daha küçük model
- context azaltma
- timeout ayarını uygun şekilde artırma
- daha hızlı quantization
- daha fazla GPU offload
## 30. Model Server Sağlığı
Qwen Code problemi olduğunu düşünmeden önce model sunucusunu ayrı test edin.
LM Studio:
Invoke-RestMethod http://localhost:1234/v1/models
Ollama:
Invoke-RestMethod http://localhost:11434/api/tags
API katmanı çalışmıyorsa Qwen Code modelden cevap alamaz.
## 31. Model Değiştirdikten Sonra
Yeni model kullanıldığında eski model için hazırlanan ayarların tamamının uygun olduğu varsayılmamalıdır.
Kontrol edin:
- model ID
- context
- tool calling
- structured output
- temperature
- provider
- endpoint
- timeout
## 32. İlk Model Seçim Akışı
Pratik yaklaşım:
Donanımı belirle -> Kullanım amacını belirle -> Coding model adaylarını seç -> Uygun quantization seç -> Context belirle -> API bağlantısını test et -> Tool calling test et -> Gerçek proje görevi çalıştır -> Sonucu karşılaştır
## 33. Başarı Kriteri
Bir model Qwen Code için ancak şu zincirde yeterli kabul edilebilir:
Model yükleniyor -> API cevap veriyor -> Türkçe talimat anlaşılıyor -> Kod analizi doğru -> Tool calling çalışıyor -> Gerçek tool çalışıyor -> Build/test tamamlanıyor -> Uzun görev hedefi korunuyor
## Sonuç
Qwen Code için en iyi yerel model tek bir model adıyla belirlenemez.
Doğru seçim:
Donanım + Model Yeteneği + Tool Calling + Context + Kullanılan Programlama Dilleri + Gerçek Görev Performansı
birlikte değerlendirilerek yapılmalıdır.
