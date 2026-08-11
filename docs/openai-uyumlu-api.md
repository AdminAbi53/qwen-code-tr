# Qwen Code Türkçe - OpenAI Uyumlu API Kullanımı
Bu rehber, Qwen Code'u OpenAI uyumlu API sunan farklı model sağlayıcıları ve yerel model sunucularıyla kullanmanın temel mantığını açıklamak için hazırlanmıştır.
Bu depo Qwen ekibinin resmi projesi değildir. Bağımsız bir Türkçe topluluk dokümantasyonu çalışmasıdır.
## 1. OpenAI Uyumlu API Nedir?
OpenAI uyumlu API, farklı yapay zeka servislerinin benzer API yapısını kullanarak istemcilerle iletişim kurmasını sağlayan bir uyumluluk yaklaşımıdır.
Bu sayede desteklenen istemciler yalnız tek bir sağlayıcıya bağlı kalmadan farklı model servislerine bağlanabilir.
## 2. Genel Mimari
Temel yapı:
Qwen Code -> OpenAI Uyumlu API -> Model Sağlayıcısı -> Model
Model sağlayıcısı internet üzerindeki bir servis veya bilgisayarınızda çalışan yerel bir model sunucusu olabilir.
## 3. Temel Yapılandırma
Bir OpenAI uyumlu bağlantıda genellikle üç temel bilgi gerekir:
Base URL
API Key
Model
Gerçek alan isimleri ve yapılandırma yöntemi kullanılan Qwen Code sürümüne göre değişebilir.
## 4. Base URL
Base URL model servisinin API adresidir.
Yerel servislerde örnek yapı:
http://localhost:PORT/v1
Uzak servislerde sağlayıcının verdiği HTTPS adresi kullanılır.
Base URL'yi tahmin etmeyin. Sağlayıcının güncel resmi dokümantasyonundan doğrulayın.
## 5. API Key
Bazı sağlayıcılar API anahtarı gerektirir.
API anahtarını:
- GitHub repository içerisinde paylaşmayın
- kaynak kod içerisine yazmayın
- ekran görüntülerinde göstermeyin
- public log dosyalarına eklemeyin
Mümkün olduğunda environment variable veya güvenli secret yönetimi kullanın.
## 6. Model Adı
Model adı sağlayıcının API tarafından tanınan gerçek model kimliği olmalıdır.
Arayüzde görünen pazarlama adı ile API model ID'si farklı olabilir.
Model bulunamadı hatası alırsanız sağlayıcının model listesini kontrol edin.
## 7. Yerel API Sunucuları
OpenAI uyumlu API yalnız internet servislerinde kullanılmaz.
Bazı yerel model araçları da uyumlu endpoint sağlayabilir.
Örnek kullanım alanları:
- LM Studio
- Ollama
- özel inference sunucuları
- self-hosted model servisleri
Her aracın endpoint ve özellik desteği farklı olabilir.
## 8. LM Studio Örneği
LM Studio yerel API sunucusu tipik olarak localhost üzerinden çalışabilir.
Örnek:
http://localhost:1234/v1
Gerçek port ve endpoint LM Studio yapılandırmasından kontrol edilmelidir.
Model listesini kontrol etmek için:
Invoke-RestMethod http://localhost:1234/v1/models
## 9. Ollama Örneği
Ollama'nın yerel servisi tipik olarak:
http://localhost:11434
adresinde çalışabilir.
OpenAI uyumlu endpoint desteği kullanılan Ollama sürümüne göre resmi dokümantasyondan doğrulanmalıdır.
## 10. Uzak Model Sağlayıcıları
Bazı bulut model sağlayıcıları OpenAI uyumlu API sunabilir.
Genel yapı:
Qwen Code -> HTTPS API -> Provider -> Model
Kullanmadan önce şu özellikleri kontrol edin:
- API compatibility
- model availability
- tool calling
- streaming
- structured output
- context length
- rate limits
- fiyatlandırma
## 11. API Uyumluluğu Her Zaman Tam Değildir
Bir sağlayıcının OpenAI compatible olduğunu söylemesi bütün özelliklerin birebir aynı olduğu anlamına gelmeyebilir.
Örneğin sağlayıcı:
chat completion destekleyebilir
ama:
tool calling
structured output
streaming
vision
gibi özelliklerin bazılarını desteklemeyebilir.
## 12. Tool Calling
Coding agent kullanımında tool calling önemli bir özelliktir.
Modelin yalnızca metin cevabı vermesi yeterli olmayabilir.
Agent:
- dosya okumak
- terminal çalıştırmak
- kod değiştirmek
- build yapmak
- test çalıştırmak
gibi işlemler için yapılandırılmış tool çağrıları üretmek zorunda olabilir.
## 13. Structured Output
Bazı agent sistemleri modelden belirli JSON veya schema yapısında çıktı bekleyebilir.
Model veya provider structured output konusunda yetersizse orchestration davranışı bozulabilir.
Bu nedenle yalnız sohbet testi yapmak yeterli değildir.
## 14. Context Length
Her modelin desteklediği context uzunluğu farklıdır.
Context sınırı aşılırsa:
context length exceeded
veya benzeri hata alınabilir.
Büyük projelerde model seçerken context kapasitesini kontrol edin.
## 15. Rate Limit
Bulut sağlayıcıları istek sınırı uygulayabilir.
Örnek hata:
429 Too Many Requests
Bu durumda:
- provider kotasını kontrol edin
- concurrency azaltın
- istek hızını düşürün
- hesabın limitlerini kontrol edin
## 16. Authentication Hatası
Örnek:
401 Unauthorized
Kontrol edin:
- API key doğru mu?
- environment variable doğru mu?
- key aktif mi?
- doğru provider kullanılıyor mu?
- authentication header doğru oluşturuluyor mu?
## 17. Forbidden Hatası
Örnek:
403 Forbidden
Muhtemel nedenler:
- model erişim izni yok
- hesap yetkisi yetersiz
- bölgesel kısıtlama
- provider politikası
- yanlış authentication
## 18. Endpoint Bulunamadı
Örnek:
404 Not Found
Kontrol edin:
- Base URL
- /v1 kullanımı
- endpoint yolu
- provider API sürümü
- yanlış port
- yanlış servis adresi
## 19. Connection Refused
Yerel sunucularda sık görülebilir.
Kontrol edin:
- model sunucusu çalışıyor mu?
- port doğru mu?
- localhost adresi doğru mu?
- firewall engelliyor mu?
- servis çöktü mü?
## 20. Timeout
Model cevap vermekte çok uzun sürerse timeout oluşabilir.
Muhtemel nedenler:
- model çok büyük
- provider yoğun
- internet yavaş
- context çok büyük
- inference yavaş
- timeout süresi yetersiz
Önce gerçek neden belirlenmelidir.
## 21. Environment Variable
Bazı istemciler provider bilgilerini environment variable üzerinden okuyabilir.
Kavramsal örnek:
OPENAI_BASE_URL
OPENAI_API_KEY
MODEL
Gerçek environment variable isimlerini Qwen Code'un güncel resmi dokümantasyonundan doğrulayın.
## 22. Public Repository Güvenliği
Public GitHub repository içerisinde gerçek API anahtarı paylaşmayın.
Yanlışlıkla anahtar commit edildiğinde yalnız dosyadan silmek yeterli değildir.
Anahtarı derhal iptal edin ve yenisini oluşturun.
Git geçmişinde kalmış olabileceğini unutmayın.
## 23. Provider Değiştirme
OpenAI uyumlu yapıların önemli avantajlarından biri farklı sağlayıcıları daha kolay deneyebilmektir.
Kavramsal yapı:
Provider A -> Model A
Provider B -> Model B
Local Server -> Local Model
Ancak provider değiştirildiğinde model davranışının aynı olacağı varsayılmamalıdır.
## 24. Model Capability Kontrolü
Coding agent için model seçerken şu yetenekleri kontrol edin:
- coding
- instruction following
- tool calling
- structured output
- context length
- reasoning
- tool result interpretation
- kullanılan dil desteği
Model yalnız benchmark skoruna göre seçilmemelidir.
## 25. Basit Bağlantı Testi
İlk test:
Sadece API_TEST_OK yaz.
Beklenen:
API_TEST_OK
Bu test yalnız model bağlantısını doğrular.
## 26. Gerçek Agent Testi
Bağlantı testinden sonra gerçek araç kullanımını test edin.
Örnek görev:
Bu proje klasörünü incele.
Dosyaları listele.
Kullanılan programlama dilini belirle.
Hiçbir dosyayı değiştirme.
Sonucu raporla.
Bu test proje context'inin işlenmesini kontrol etmeye yardımcı olur.
## 27. Tool Testi
Tool calling destekleniyorsa gerçek bir araç çağrısı doğrulanmalıdır.
Başarı zinciri:
Model Connected -> Tool Schema Received -> Tool Call Generated -> Tool Executed -> Result Returned -> Model Interpreted Result
Bu zincirin tamamı çalışmalıdır.
## 28. Provider Logları
Bağlantı problemi araştırırken mümkünse şu bilgileri kontrol edin:
- HTTP status code
- request endpoint
- model ID
- response error
- latency
- rate limit
- token kullanımı
- timeout
API anahtarını loglara yazdırmayın.
## 29. Fallback Model
Bazı sistemlerde ana model kullanılamadığında alternatif model kullanılabilir.
Örnek:
Primary Model başarısız -> Capability kontrolü -> Compatible Fallback Model
Ancak fallback modelin gerekli tool calling ve context yeteneklerine sahip olduğu doğrulanmalıdır.
## 30. Model Routing
Gelişmiş sistemlerde farklı görevler farklı modellere yönlendirilebilir.
Örnek:
Coding -> Coder Model
Vision -> Vision Model
Research -> General Model
Fast Classification -> Small Model
Bu özellik Qwen Code'un kullanılan sürümüne ve orchestration mimarisine bağlıdır.
## 31. Yerel ve Bulut Model Karşılaştırması
Yerel model avantajları:
- API maliyetini azaltabilir
- bazı verilerin cihazda kalmasını sağlayabilir
- internet olmadan bazı görevlerde kullanılabilir
Bulut model avantajları:
- güçlü modeller
- daha az yerel donanım gereksinimi
- yüksek inference performansı
- yönetilen altyapı
En uygun seçenek kullanım senaryosuna bağlıdır.
## 32. Sorun Giderme Sırası
Bağlantı çalışmıyorsa şu sırayı izleyin:
1. Model servisi çalışıyor mu?
2. Base URL doğru mu?
3. Endpoint erişilebilir mi?
4. Authentication doğru mu?
5. Model ID doğru mu?
6. Basit chat isteği çalışıyor mu?
7. Context destekleniyor mu?
8. Tool calling çalışıyor mu?
9. Structured output çalışıyor mu?
10. Gerçek Qwen Code görevi tamamlanıyor mu?
## 33. Başarı Kriteri
Sadece API'nin HTTP 200 döndürmesi tam entegrasyon anlamına gelmez.
Gerçek başarı:
API Reachable -> Authentication PASS -> Model Found -> Chat PASS -> Context PASS -> Tool Calling PASS -> Tool Execution PASS -> Real Project Task PASS
## Kaynaklar
Qwen Code resmi repository:
https://github.com/QwenLM/qwen-code
Qwen Code resmi dokümantasyonu:
https://qwenlm.github.io/qwen-code-docs/
LM Studio:
https://lmstudio.ai/
Ollama:
https://ollama.com/
## Sonuç
OpenAI uyumlu API desteği, Qwen Code'un farklı model sağlayıcıları ve yerel model sunucularıyla kullanılabilmesini kolaylaştırabilir.
Ancak gerçek uyumluluk yalnız endpoint bağlantısıyla ölçülmemelidir.
Coding agent kullanımında modelin tool calling, structured output, context ve gerçek araç yürütme yetenekleri de mutlaka doğrulanmalıdır.
