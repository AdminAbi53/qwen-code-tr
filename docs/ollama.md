# Qwen Code Türkçe - Ollama ile Yerel Model Kullanımı
Bu rehber, Qwen Code'u Ollama üzerinden çalışan yerel yapay zeka modelleriyle kullanmak isteyen Türkçe kullanıcılar için hazırlanmıştır.
Bu depo Qwen ekibinin resmi projesi değildir. Bağımsız bir Türkçe topluluk dokümantasyonu çalışmasıdır.
## 1. Ollama Nedir?
Ollama, yerel yapay zeka modellerini bilgisayarda çalıştırmayı kolaylaştıran araçlardan biridir.
Ollama ile:
- yerel modeller indirilebilir
- modeller terminal üzerinden çalıştırılabilir
- yerel API sunucusu kullanılabilir
- farklı açık modeller kolayca denenebilir
Qwen Code'un kullanılan sürümü OpenAI uyumlu veya desteklenen yerel provider yapılandırmasına izin veriyorsa Ollama ile birlikte kullanılabilir.
## 2. Genel Mimari
Temel yapı:
Qwen Code -> Yerel API -> Ollama -> Yerel Model
Bu yapı sayesinde model istekleri yerel bilgisayarda çalışan modele gönderilebilir.
## 3. Ollama Kurulumu
Ollama'yı resmi sitesinden indirin:
https://ollama.com/
Kurulum tamamlandıktan sonra terminal açın.
Kurulumu kontrol etmek için:
ollama --version
Komut sürüm bilgisi döndürüyorsa temel kurulum çalışıyor demektir.
## 4. Model İndirme
Bir model indirmek için genel kullanım:
ollama pull MODEL_ADI
Örnek:
ollama pull qwen2.5-coder
Model adları ve kullanılabilir sürümler zaman içinde değişebilir.
Güncel model listesini Ollama'nın resmi model kütüphanesinden kontrol edin.
## 5. Model Çalıştırma
Bir modeli terminalden başlatmak için:
ollama run MODEL_ADI
Örnek:
ollama run qwen2.5-coder
Model yüklendikten sonra terminal üzerinden doğrudan sohbet edilebilir.
## 6. Kurulu Modelleri Görme
Kurulu modeller:
ollama list
Bu komut sistemde bulunan model isimlerini ve sürümlerini gösterir.
## 7. Model Bilgisini Görme
Bir modelin ayrıntılarını görmek için:
ollama show MODEL_ADI
Bu bilgiler model yapılandırmasını ve bazı teknik özellikleri incelemek için kullanılabilir.
## 8. Ollama API
Ollama yerel API sunucusu sağlayabilir.
Tipik adres:
http://localhost:11434
API'nin çalışıp çalışmadığını kontrol etmek için tarayıcı veya terminal kullanılabilir.
Model listesi için örnek API endpoint:
http://localhost:11434/api/tags
PowerShell ile:
Invoke-RestMethod http://localhost:11434/api/tags
Yanıt geliyorsa Ollama API çalışıyor demektir.
## 9. OpenAI Uyumlu API
Ollama sürümüne bağlı olarak OpenAI uyumlu endpoint desteği bulunabilir.
Tipik yapı:
http://localhost:11434/v1
Kullandığınız sürümde desteklenen endpoint'leri Ollama resmi dokümantasyonundan doğrulayın.
## 10. Qwen Code ile Bağlantı
Qwen Code'un provider yapılandırmasında yerel bir OpenAI uyumlu endpoint destekleniyorsa genel mantık:
Base URL -> Ollama endpoint
Model -> Ollama model adı
API Key -> gerekli ise istemcinin beklediği yerel değer
Gerçek yapılandırma alanları Qwen Code sürümüne göre değişebilir.
Bu nedenle güncel Qwen Code provider dokümantasyonu esas alınmalıdır.
## 11. Model Adı
Qwen Code yapılandırmasında doğru model adını kullanmak önemlidir.
Kurulu modelleri görmek için:
ollama list
Burada görünen gerçek model adını kullanın.
Yanlış model adı:
model not found
benzeri hatalara yol açabilir.
## 12. Basit Test
Ollama modelinin çalıştığını doğrulamak için:
ollama run MODEL_ADI
Ardından:
Sadece OLLAMA_TEST_OK yaz.
Beklenen:
OLLAMA_TEST_OK
Bu test yalnız temel model cevabını doğrular.
## 13. API Testi
PowerShell üzerinden:
Invoke-RestMethod http://localhost:11434/api/tags
ile model listesini kontrol edin.
OpenAI uyumlu endpoint kullanıyorsanız ilgili endpoint'i ayrıca doğrulayın.
## 14. Qwen Code Gerçek Testi
Qwen Code bağlantısı yapılandırıldıktan sonra küçük bir proje klasöründe başlatın:
qwen
İlk görev:
Bu klasörü incele.
Kullanılan programlama dilini belirle.
Henüz hiçbir dosyayı değiştirme.
Sadece proje yapısını özetle.
Bu test Qwen Code'un model ile proje bağlamında çalışabildiğini doğrulamaya yardımcı olur.
## 15. Tool Calling
Yerel modelin normal sohbet edebilmesi agent görevleri için her zaman yeterli değildir.
Önemli özellikler:
- tool calling
- structured output
- instruction following
- kod analizi
- uzun context
- tool sonucunu yorumlama
Kullandığınız model bu alanlarda zayıfsa Qwen Code'un gelişmiş agent davranışı da sınırlı olabilir.
## 16. Context
Context değeri arttıkça model aynı anda daha fazla proje bilgisini görebilir.
Ancak yüksek context:
- daha fazla RAM
- daha fazla VRAM
- daha fazla işlem süresi
gerektirebilir.
Her zaman maksimum context kullanmak doğru değildir.
## 17. Donanım
Yerel model performansını etkileyen başlıca kaynaklar:
- GPU
- VRAM
- RAM
- CPU
- model boyutu
- quantization
- context uzunluğu
Model donanımdan büyükse performans ciddi şekilde düşebilir.
## 18. Model Çok Yavaş
Deneyebileceğiniz yöntemler:
- daha küçük model kullanmak
- daha düşük quantization kullanmak
- context azaltmak
- GPU kullanımını artırmak
- başka ağır programları kapatmak
- görevi daha küçük parçalara bölmek
## 19. Connection Refused
Örnek:
Connection refused
Kontrol edin:
- Ollama çalışıyor mu?
- port doğru mu?
- API endpoint doğru mu?
- firewall engelliyor mu?
- servis durmuş mu?
Kontrol:
Invoke-RestMethod http://localhost:11434/api/tags
## 20. Model Bulunamadı
Örnek:
model not found
Kontrol:
ollama list
Qwen Code yapılandırmasındaki model adı ile Ollama'daki gerçek model adını karşılaştırın.
## 21. Modeli Silme
Bir modeli kaldırmak için:
ollama rm MODEL_ADI
Silmeden önce doğru model adını kullandığınızdan emin olun.
## 22. Model Güncelleme
Modelin güncel sürümünü almak için:
ollama pull MODEL_ADI
kullanılabilir.
Yeni model sürümleri davranış veya performans farklılıkları oluşturabilir.
## 23. Ollama ve LM Studio Farkı
Her iki araç da yerel model çalıştırmak için kullanılabilir.
LM Studio:
- masaüstü arayüz odaklıdır
- model yönetimi görsel olarak yapılabilir
- yerel API sunucusu sağlayabilir
Ollama:
- terminal ve servis kullanımı daha öndedir
- model indirme ve çalıştırma komutlarla yapılabilir
- otomasyon ortamlarında pratik olabilir
Hangisinin daha uygun olduğu kullanıcı tercihine ve çalışma ortamına bağlıdır.
## 24. Güvenlik
Yerel model kullanmak Qwen Code'un sistem erişimi risklerini ortadan kaldırmaz.
Agent terminal veya dosya araçlarına sahipse:
- dosya değiştirebilir
- dosya silebilir
- komut çalıştırabilir
- repository değiştirebilir
Bu nedenle önemli projelerde Git kullanın ve değişiklikleri kontrol edin.
## 25. Sorun Giderme Sırası
Ollama bağlantısında sorun varsa şu sırayı izleyin:
1. ollama --version
2. ollama list
3. model gerçekten kurulu mu?
4. model terminalde cevap veriyor mu?
5. API endpoint çalışıyor mu?
6. Qwen Code base URL doğru mu?
7. model adı doğru mu?
8. Qwen Code modelden cevap alıyor mu?
9. tool calling çalışıyor mu?
10. gerçek proje görevi tamamlanıyor mu?
## 26. Başarı Kriteri
Sadece:
Ollama çalışıyor
veya:
Model cevap verdi
entegrasyonun tamamen hazır olduğu anlamına gelmez.
Gerçek başarı:
Ollama çalışıyor -> Model yüklü -> API erişilebilir -> Qwen Code bağlandı -> Model cevap verdi -> Proje context'i işlendi -> Tool calling çalıştı -> Gerçek görev tamamlandı
## Kaynaklar
Ollama resmi sitesi:
https://ollama.com/
Ollama resmi dokümantasyonu:
https://docs.ollama.com/
Qwen Code resmi repository:
https://github.com/QwenLM/qwen-code
Qwen Code resmi dokümantasyonu:
https://qwenlm.github.io/qwen-code-docs/
## Sonuç
Ollama, Qwen Code ile yerel yapay zeka modeli kullanmak isteyen geliştiriciler için pratik seçeneklerden biridir.
Ancak iyi sonuç almak için yalnız modeli çalıştırmak yeterli değildir.
Model kalitesi, tool calling desteği, context kapasitesi ve Qwen Code provider yapılandırması birlikte değerlendirilmelidir.
