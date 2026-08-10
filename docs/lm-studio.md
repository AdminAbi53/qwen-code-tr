# Qwen Code Türkçe — LM Studio ile Yerel Model Kullanımı

Bu rehber, Qwen Code'u LM Studio üzerinden çalışan yerel yapay zekâ modelleriyle kullanmak isteyen Türkçe konuşan kullanıcılar için hazırlanmıştır.

> [!IMPORTANT]
> Bu depo Qwen ekibinin resmi projesi değildir. Bağımsız bir Türkçe topluluk dokümantasyonu çalışmasıdır.

---

## 1. LM Studio Nedir?

LM Studio, bilgisayar üzerinde yerel yapay zekâ modelleri çalıştırmayı kolaylaştıran masaüstü uygulamalarından biridir.

LM Studio ile:

- yerel LLM modelleri indirilebilir,
- modeller bilgisayarda çalıştırılabilir,
- OpenAI uyumlu API sunucusu açılabilir,
- farklı model boyutları denenebilir,
- internet tabanlı API servislerine ihtiyaç duymadan yerel geliştirme ortamı kurulabilir.

Qwen Code, kullanılan sürüm ve yapılandırmaya bağlı olarak OpenAI uyumlu API endpoint'leri üzerinden LM Studio ile birlikte kullanılabilir.

---

## 2. Genel Mimari

Temel yapı şöyledir:

```text
Qwen Code
    |
    v
OpenAI Uyumlu API
    |
    v
LM Studio Local Server
    |
    v
Yerel Yapay Zekâ Modeli
```

Bu yapı sayesinde Qwen Code'un model istekleri yerel bilgisayarda çalışan modele yönlendirilebilir.

---

## 3. LM Studio Kurulumu

LM Studio'yu resmi web sitesinden indirin:

```text
https://lmstudio.ai/
```

Kurulum tamamlandıktan sonra LM Studio'yu başlatın.

---

## 4. Model Seçimi

LM Studio içerisinde kullanılacak modeli seçerken aşağıdaki özellikleri dikkate alın:

- model boyutu,
- RAM kullanımı,
- VRAM kullanımı,
- context uzunluğu,
- kodlama yeteneği,
- tool calling desteği,
- structured output desteği,
- modelin quantization seviyesi.

Kodlama görevlerinde coding odaklı modeller tercih edilebilir.

Örneğin:

```text
Qwen Coder modelleri
Code odaklı diğer açık modeller
Tool calling destekleyen modeller
Uzun context destekleyen modeller
```

Model seçimi bilgisayarın donanımına uygun yapılmalıdır.

---

## 5. Modeli Yükleme

LM Studio içerisinde:

```text
Models
```

bölümünden modeli indirin.

İndirme tamamlandıktan sonra modeli yükleyin.

Model yüklenmeden API sunucusu istekleri yanıtlayamaz.

---

## 6. Local Server Başlatma

LM Studio içerisinde geliştirici veya Local Server bölümünü açın.

OpenAI uyumlu API sunucusunu başlatın.

Tipik endpoint:

```text
http://localhost:1234/v1
```

Port yapılandırmaya göre değişebilir.

Bu nedenle LM Studio ekranında görünen gerçek adresi kullanın.

---

## 7. Sunucunun Çalıştığını Kontrol Etme

Tarayıcı veya terminal üzerinden API'nin çalışıp çalışmadığını kontrol edebilirsiniz.

Örneğin PowerShell:

```powershell
Invoke-RestMethod http://localhost:1234/v1/models
```

Sunucu çalışıyorsa model bilgileri veya API yanıtı alınmalıdır.

Bağlantı hatası alırsanız:

- LM Studio açık mı?
- model yüklenmiş mi?
- Local Server çalışıyor mu?
- port doğru mu?
- firewall bağlantıyı engelliyor mu?

kontrol edin.

---

## 8. Model Listesini Kontrol Etme

OpenAI uyumlu API kullanılıyorsa model listesini görmek için:

```powershell
Invoke-RestMethod http://localhost:1234/v1/models
```

Çıktıda gerçek model kimliği görülebilir.

Qwen Code yapılandırmasında model adı gerektiğinde bu değerin kullanılması gerekebilir.

---

## 9. API Base URL

Qwen Code'un OpenAI uyumlu provider yapılandırması desteklediği sürümlerde base URL genellikle LM Studio'nun API endpoint'ine yönlendirilir.

Örnek:

```text
http://localhost:1234/v1
```

Bu adres yalnız örnektir.

LM Studio farklı port kullanıyorsa gerçek portu yazın.

---

## 10. API Key

Yerel LM Studio sunucusunda bazı yapılandırmalarda gerçek API anahtarı gerekmeyebilir.

Ancak istemci bir API key alanı bekliyorsa test amaçlı bir değer gerekebilir.

Örneğin:

```text
lm-studio
```

Gerçek yapılandırma kullanılan Qwen Code ve LM Studio sürümüne göre kontrol edilmelidir.

Public repository içerisinde gerçek özel API anahtarları paylaşmayın.

---

## 11. Qwen Code Yapılandırması

Qwen Code sürümüne göre provider ayarları değişebilir.

Bu nedenle önce resmi Qwen Code dokümantasyonundaki güncel model/provider yapılandırmasını kontrol edin.

Genel mantık:

```text
Provider
    |
    +-- Base URL
    |
    +-- API Key
    |
    +-- Model
```

LM Studio için:

```text
Base URL
http://localhost:1234/v1
```

Model:

```text
LM Studio /v1/models çıktısındaki gerçek model kimliği
```

şeklinde yapılandırılır.

---

## 12. Ortam Değişkeni Kullanımı

Bazı istemciler OpenAI uyumlu yapılandırmayı environment variable üzerinden okuyabilir.

Genel örnek:

```powershell
$env:OPENAI_BASE_URL="http://localhost:1234/v1"
$env:OPENAI_API_KEY="lm-studio"
```

Model değişkeni gerekiyorsa kullanılan Qwen Code sürümünün dokümantasyonuna göre ayarlanmalıdır.

Bu değişken adlarının her sürümde aynı olduğu varsayılmamalıdır.

---

## 13. Qwen Code'u Başlatma

LM Studio sunucusu çalışırken proje klasörüne gidin:

```powershell
cd C:\Projeler\BenimUygulamam
```

Qwen Code'u başlatın:

```powershell
qwen
```

Model yapılandırması doğruysa Qwen Code yerel LM Studio modeline istek gönderebilir.

---

## 14. Basit Bağlantı Testi

İlk test çok basit olmalıdır.

Örneğin:

```text
Sadece şu cevabı ver:

LM_STUDIO_TEST_OK
```

Beklenen çıktı:

```text
LM_STUDIO_TEST_OK
```

Bu test bağlantının temel olarak çalıştığını gösterir.

---

## 15. Gerçek Kodlama Testi

Bağlantı testinden sonra gerçek bir kodlama görevi verin.

Örneğin:

```text
Bu klasörü incele.

Kullanılan programlama dilini belirle.

Henüz hiçbir dosyayı değiştirme.

Sadece proje yapısını özetle.
```

Bu test modelin proje bağlamıyla çalışabildiğini kontrol eder.

---

## 16. Tool Calling

Bir modelin yalnızca metin üretmesi, Qwen Code'un bütün agent özelliklerini desteklediği anlamına gelmez.

Gelişmiş kullanım için modelin aşağıdaki özellikleri önemli olabilir:

- tool calling,
- structured output,
- instruction following,
- uzun context,
- kod analizi,
- çok adımlı reasoning.

Model tool calling desteklemiyorsa bazı agent görevleri sınırlı çalışabilir.

---

## 17. Structured Output

Bazı agent sistemleri modelden serbest metin yerine yapılandırılmış JSON çıktısı bekler.

Örneğin:

```json
{
  "status": "success",
  "action": "analyze_project",
  "files": [
    "src/app.cs",
    "src/main.cs"
  ]
}
```

Kullanılan model structured output konusunda zayıfsa agent orchestration davranışı da zayıflayabilir.

---

## 18. Context Uzunluğu

Context değeri ne kadar yüksek olursa model aynı anda daha fazla proje bilgisi görebilir.

Ancak yüksek context:

- daha fazla RAM,
- daha fazla VRAM,
- daha uzun inference süresi

gerektirebilir.

Her zaman mümkün olan maksimum değeri kullanmak en iyi seçenek değildir.

Model ve donanıma uygun context seçilmelidir.

---

## 19. VRAM ve RAM

Yerel modellerin performansı büyük ölçüde donanıma bağlıdır.

Önemli kaynaklar:

```text
GPU VRAM
System RAM
CPU
Disk hızı
Model quantization
Context uzunluğu
```

Yetersiz VRAM durumunda modelin bir kısmı RAM/CPU tarafına taşınabilir.

Bu durum performansı önemli ölçüde düşürebilir.

---

## 20. Quantization

Aynı model farklı quantization seçenekleriyle bulunabilir.

Örneğin:

```text
Q4
Q5
Q6
Q8
```

Daha düşük quantization genellikle:

- daha az RAM/VRAM kullanır,
- daha hızlı olabilir,
- kaliteyi bir miktar düşürebilir.

Daha yüksek quantization:

- daha fazla kaynak kullanır,
- daha yüksek doğruluk sağlayabilir.

Donanıma göre denge kurulmalıdır.

---

## 21. Model Cevap Vermiyor

Kontrol sırası:

```text
LM Studio açık mı?
        ↓
Model yüklü mü?
        ↓
Local Server çalışıyor mu?
        ↓
Endpoint doğru mu?
        ↓
Port doğru mu?
        ↓
Model adı doğru mu?
        ↓
Qwen Code provider ayarı doğru mu?
        ↓
Model isteğe cevap verebiliyor mu?
```

---

## 22. 404 Hatası

Örneğin:

```text
404 Not Found
```

alıyorsanız:

- yanlış base URL,
- yanlış endpoint,
- yanlış API path

kullanılıyor olabilir.

OpenAI uyumlu endpoint tipik olarak:

```text
/v1
```

içerir.

---

## 23. Connection Refused

Örneğin:

```text
Connection refused
```

durumunda:

- LM Studio Local Server kapalı olabilir,
- yanlış port kullanılıyor olabilir,
- firewall engelliyor olabilir,
- server yalnız farklı interface üzerinde dinliyor olabilir.

---

## 24. Model Bulunamadı

Örneğin:

```text
model not found
```

hatasında:

```powershell
Invoke-RestMethod http://localhost:1234/v1/models
```

ile gerçek model kimliğini kontrol edin.

Yapılandırmaya görünen model adını değil API'nin döndürdüğü model kimliğini yazmanız gerekebilir.

---

## 25. Context Overflow

Çok büyük proje veya uzun konuşmalarda context sınırı aşılabilir.

Belirtiler:

- request failure,
- context length exceeded,
- çok yavaş cevap,
- modelin önceki bilgileri kaybetmesi.

Çözüm seçenekleri:

- gereksiz context'i azaltmak,
- görevi bölmek,
- daha uzun context destekleyen model kullanmak,
- agent'ın yalnız ilgili dosyaları göndermesini sağlamak.

---

## 26. Yavaş Çalışma

Yerel model çok yavaşsa:

- daha küçük model,
- daha düşük quantization,
- daha düşük context,
- daha fazla GPU offload,
- arka plandaki ağır uygulamaları kapatma

denenebilir.

Modelin boyutu donanımdan büyükse çok ciddi performans kaybı yaşanabilir.

---

## 27. Birden Fazla Model

LM Studio üzerinde farklı görevler için farklı modeller kullanılabilir.

Örneğin:

```text
Coding Agent
    ↓
Coder Model

Vision Agent
    ↓
Vision Model

General Agent
    ↓
General Reasoning Model
```

Bunu Qwen Code'un doğrudan destekleyip desteklemediği kullanılan sürüm ve agent mimarisine bağlıdır.

---

## 28. Yerel Model Kullanmanın Avantajları

- bazı veriler bilgisayardan çıkmayabilir,
- API maliyeti azaltılabilir,
- farklı modeller denenebilir,
- geliştirme ortamı özelleştirilebilir,
- internet bağlantısı olmayan bazı senaryolarda çalışma mümkün olabilir.

---

## 29. Yerel Model Kullanmanın Dezavantajları

- güçlü donanım gerekebilir,
- büyük modeller yavaş olabilir,
- model kalitesi ticari modellerden düşük olabilir,
- tool calling kalitesi modele göre değişir,
- context yönetimi daha zor olabilir,
- kurulum ve optimizasyon kullanıcıya kalabilir.

---

## 30. Güvenlik

Yerel model kullanılması bütün güvenlik risklerini otomatik olarak ortadan kaldırmaz.

Qwen Code terminal ve araç erişimine sahipse:

- dosya silebilir,
- kod değiştirebilir,
- shell komutları çalıştırabilir,
- dış servislere bağlanabilir.

Bu nedenle önemli projelerde Git ve yedek kullanın.

---

## 31. Önerilen Test Sırası

```text
LM Studio kur
      ↓
Model indir
      ↓
Model yükle
      ↓
Local Server başlat
      ↓
/v1/models kontrol et
      ↓
Qwen Code provider ayarla
      ↓
Basit prompt testi
      ↓
Proje analiz testi
      ↓
Tool calling testi
      ↓
Gerçek kodlama görevi
```

---

## 32. Başarı Kriteri

Sadece LM Studio'nun:

```text
Server Running
```

göstermesi entegrasyonun tamamen çalıştığını kanıtlamaz.

Gerçek başarı:

```text
LM Studio Server
        +
Model Loaded
        +
API Reachable
        +
Qwen Code Connected
        +
Model Response
        +
Project Context
        +
Tool Execution
        +
Expected Result
        =
Working Local Qwen Code Environment
```

---

## Kaynaklar

LM Studio resmi sitesi:

```text
https://lmstudio.ai/
```

LM Studio geliştirici dokümantasyonu:

```text
https://lmstudio.ai/docs/
```

Qwen Code resmi repository:

```text
https://github.com/QwenLM/qwen-code
```

Qwen Code resmi dokümantasyonu:

```text
https://qwenlm.github.io/qwen-code-docs/
```

---

## Sonraki Rehberler

Bu proje aşağıdaki Türkçe rehberlerle genişletilecektir:

- Qwen Code hata giderme
- Ollama entegrasyonu
- OpenAI uyumlu API sağlayıcıları
- agent ve subagent sistemleri
- çoklu ajan çalışma mantığı
- MCP örnek projeleri
- Windows optimizasyonu
- yerel model performans ayarları
