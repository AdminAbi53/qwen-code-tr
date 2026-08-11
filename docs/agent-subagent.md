# Qwen Code Türkçe - Agent ve Subagent Kullanım Rehberi
Bu rehber, Qwen Code içerisinde agent ve subagent mantığını Türkçe olarak açıklamak için hazırlanmıştır.
Bu depo Qwen ekibinin resmi projesi değildir. Bağımsız bir Türkçe topluluk dokümantasyonu çalışmasıdır.
## 1. Agent Nedir?
Agent, yalnızca metin üreten bir sohbet modelinden farklı olarak bir hedefi gerçekleştirmek için plan oluşturabilen, araç kullanabilen, dosyaları inceleyebilen, gerektiğinde kod değiştirebilen ve sonuçları değerlendirebilen yapay zeka çalışma birimidir.
Basit yapı:
Kullanıcı -> Agent -> Analiz -> Tool Kullanımı -> Sonuç
Bir coding agent örneğin:
- proje klasörünü inceleyebilir
- kaynak kodu okuyabilir
- hata nedenini araştırabilir
- dosya oluşturabilir
- kod değiştirebilir
- terminal komutları çalıştırabilir
- build çalıştırabilir
- testleri çalıştırabilir
- sonuçları değerlendirebilir
Gerçek yetenekler kullanılan Qwen Code sürümüne, modele, araçlara ve izinlere bağlıdır.
## 2. Subagent Nedir?
Subagent, ana agent tarafından belirli bir alt görev için görevlendirilen daha dar kapsamlı bir agent'tır.
Örnek:
Ana Agent -> Projeyi tamamla
Alt görevler:
Research Subagent -> Güncel bilgiyi araştır
Coding Subagent -> Kod değişikliğini uygula
Testing Subagent -> Testleri çalıştır
Review Subagent -> Sonucu kontrol et
Bu yapı büyük görevlerin daha küçük uzmanlık alanlarına bölünmesini sağlar.
## 3. Neden Subagent Kullanılır?
Tek bir agent bütün görevi kendi context'i içerisinde yürüttüğünde:
- context büyüyebilir
- farklı uzmanlıklar birbirine karışabilir
- uzun görevlerde odak kaybı olabilir
- aynı agent çok fazla farklı araç kullanabilir
- paralel yapılabilecek işler sıralı hale gelebilir
Subagent yaklaşımı görevleri birbirinden ayırmaya yardımcı olabilir.
## 4. Ana Agent'ın Görevi
Ana agent genel hedefi koruyan koordinatördür.
Ana agent şu işleri yapabilir:
- kullanıcı isteğini anlamak
- hedef belirlemek
- görevi alt görevlere bölmek
- uygun subagent seçmek
- görevleri dağıtmak
- sonuçları toplamak
- sonuçlar arasında çelişki varsa değerlendirmek
- eksik işleri yeniden görevlendirmek
- son sonucu kullanıcıya sunmak
İyi bir multi-agent sisteminde kullanıcı her alt agent'ı kendisi yönetmek zorunda kalmamalıdır.
## 5. Specialist Agent
Specialist agent belirli bir alanda uzmanlaşmış agent'tır.
Örnekler:
Python Agent
.NET Agent
Java Agent
Research Agent
Testing Agent
Security Agent
Documentation Agent
Database Agent
UI Agent
Bir görev geldiğinde ana agent uygun specialist agent'ı seçebilir.
## 6. Agent Capability
Her agent'ın sahip olduğu yetenekler farklı olabilir.
Örnek capability kayıtları:
Programming Language: Python
Framework: FastAPI
Tool: pytest
Task Type: Testing
Platform: Windows
Bir orchestration sistemi agent seçimini yalnız isme göre değil capability bilgisine göre yapmalıdır.
## 7. Agent Registry
Agent Registry sistemde bulunan agent'ların kayıtlarını tutan yapıdır.
Bir Agent Registry kaydı kavramsal olarak şunları içerebilir:
Agent ID
Agent Name
Capabilities
Tools
Status
Supported Languages
Supported Frameworks
Validation State
Resource Requirements
Registry sayesinde ana agent hangi uzmanların mevcut olduğunu öğrenebilir.
## 8. Agent Status
Bir agent'ın kayıtlı olması onun gerçekten kullanıma hazır olduğu anlamına gelmez.
Örnek durumlar:
Candidate
NeedsValidation
Ready
Degraded
Failed
Ready durumundaki agent gerçek uzmanlık testlerinden geçmiş olmalıdır.
## 9. Agent Oluşturma
Yeni agent oluşturulurken yalnız isim ve prompt oluşturmak yeterli değildir.
İyi bir agent oluşturma akışı:
İhtiyaç belirle -> Uzmanlık kapsamını çıkar -> Gerekli araçları belirle -> Agent oluştur -> Gerçek uzmanlık testleri -> Hata testleri -> Validator -> Restart testi -> Ready
## 10. Agent Certification
Agent gerçekten uzman mı sorusunun cevabı testlerle doğrulanmalıdır.
Örnek Python Agent certification:
- Python environment discovery
- script oluşturma
- syntax kontrolü
- package kullanımı
- unit test
- hata tespiti
- hata düzeltme
- gerçek runtime
- validator
- restart persistence
Sadece:
Hello World
testi yeterli değildir.
## 11. Task Decomposition
Büyük bir görev daha küçük görevlere ayrılabilir.
Örnek:
Hedef:
Web uygulaması oluştur
Alt görevler:
1. Gereksinimleri analiz et
2. Güncel teknolojileri araştır
3. Backend oluştur
4. Frontend oluştur
5. Database oluştur
6. Testleri oluştur
7. Güvenlik kontrolü
8. Runtime doğrulaması
9. Final validation
Bu görevlerden bazıları birbirinden bağımsız olabilir.
## 12. Dependency Graph
Her alt görev aynı anda başlayamaz.
Örnek:
Research tamamlanmalı -> Architecture başlayabilir
Architecture tamamlanmalı -> Backend ve Frontend başlayabilir
Backend ve Frontend tamamlanmalı -> Integration başlayabilir
Integration tamamlanmalı -> Final Test başlayabilir
Bu yapı dependency graph veya task DAG olarak düşünülebilir.
## 13. Paralel Agent Çalışması
Birbirinden bağımsız görevler paralel yürütülebilir.
Örnek:
Ana Agent
-> Research Agent
-> UI Agent
-> Database Research Agent
Bu üç görev birbirinden bağımsızsa aynı çalışma döneminde ilerleyebilir.
Daha sonra sonuçlar ana agent tarafından birleştirilebilir.
## 14. Logical Parallelism ve Physical Parallelism
Çok sayıda agent'ın görevlendirilmesi bütün modellerin aynı anda GPU üzerinde çalışması anlamına gelmez.
Logical Parallelism:
Birden fazla agent aynı projenin aktif takımında bulunabilir.
Physical Parallelism:
Bilgisayar kaynaklarına göre aynı anda gerçekten kaç process veya inference çalıştırılabileceğini ifade eder.
Resource scheduler bu iki kavramı birbirinden ayırmalıdır.
## 15. Model Concurrency
Yerel model sunucularında aynı anda çalıştırılabilecek model isteği sayısı sınırlı olabilir.
Örneğin model sunucusu tek inference desteklerken:
Research Agent web araması yapabilir
File Agent dosya okuyabilir
Compiler Agent build çalıştırabilir
Model isteyen istekler ise sıraya alınabilir.
Bu nedenle model concurrency ile agent concurrency aynı şey değildir.
## 16. AgentRun
Bir agent'ın yalnız log içerisinde adının geçmesi onun gerçekten çalıştığını kanıtlamaz.
Gerçek bir agent çalıştırması için kavramsal olarak bir AgentRun kaydı tutulabilir:
AgentRunId
AgentId
TaskId
Start Time
End Time
Status
Input
Tools
Artifacts
Evidence
Result
Bu bilgiler multi-agent sistemlerinin gerçekten çalışıp çalışmadığını gözlemlemeyi kolaylaştırır.
## 17. Fan-Out
Fan-Out, bir görevin birden fazla bağımsız alt göreve dağıtılmasıdır.
Örnek:
Ana Agent
-> Research Agent
-> Backend Agent
-> Frontend Agent
-> Security Agent
Her agent kendi alt görevi üzerinde çalışır.
## 18. Fan-In
Fan-In, farklı agent sonuçlarının tekrar ana agent veya integration agent tarafından birleştirilmesidir.
Örnek:
Research Result
Backend Result
Frontend Result
Security Result
-> Master Analysis
-> Integrated Result
Fan-In yalnız sonuç metinlerini bir araya getirmek değildir.
Artifact ve gerçek evidence de değerlendirilmelidir.
## 19. Agent Handoff
Bir agent görevin başka bir uzmanlık gerektirdiğini fark edebilir.
Örnek:
Python Agent -> PostgreSQL bilgisi gerekiyor
Bu durumda:
Python Agent -> Capability Request -> Ana Agent -> Database Agent
şeklinde handoff yapılabilir.
Global görev yönetimi ana agent'ta kalmalıdır.
## 20. Shared Evidence
Agent'ların birbirine yalnız uzun metin raporları göndermesi yerine ortak evidence sistemi kullanılabilir.
Örnek evidence:
- build sonucu
- test sonucu
- kaynak linki
- dosya hash'i
- runtime sonucu
- benchmark
- hata mesajı
- artifact
Bu sayede agent sonuçları gerçek kanıtlarla desteklenebilir.
## 21. Artifact
Artifact, bir agent çalışmasının ürettiği somut çıktıdır.
Örnek:
source file
build output
APK
EXE
DOCX
PDF
test report
screenshot
JSON result
Artifact üretildiğinde ana agent bunu görevin acceptance kriterleriyle karşılaştırabilir.
## 22. Validator Agent
Validator Agent başka agent'ların yaptığı işi bağımsız olarak kontrol eder.
Örnek:
Coding Agent:
Uygulamayı tamamladım.
Validator Agent:
Build çalıştır
Test çalıştır
Runtime kontrol et
Dosyaları incele
Beklenen davranışı doğrula
Validator yalnız diğer agent'ın raporunu tekrar etmemelidir.
## 23. Reflection Agent
Reflection Agent başarısız bir yöntemin neden başarısız olduğunu analiz etmek için kullanılabilir.
Örnek:
Aynı hata üç kez oluştu
-> Reflection Agent
-> Başarısız varsayımları belirle
-> Tekrar edilmemesi gereken yöntemi belirle
-> Alternatif stratejiler öner
Reflection gerçek ilerlemenin yerine geçmemelidir.
## 24. Research Agent
Research Agent güncel teknik bilgi gereken görevlerde internet veya ilgili kaynaklardan bilgi toplamak için kullanılabilir.
İyi bir Research Agent:
- resmi dokümantasyonu önceliklendirir
- version bilgisini kontrol eder
- birden fazla kaynak karşılaştırır
- kaynak adreslerini saklar
- bulguları ana agent'a sunar
Research Agent'ın model hafızasından cevap üretmesi gerçek web araştırması değildir.
## 25. Research Before Execution
Güncel teknoloji görevlerinde şu yaklaşım güçlüdür:
Kullanıcı Görevi -> Research -> Master Analysis -> Plan -> Execution
Bu yaklaşım eski veya yanlış teknik varsayımlarla işleme başlanmasını azaltabilir.
## 26. Agent Context
Her subagent'a bütün proje geçmişini göndermek gerekli değildir.
Örneğin:
Research Agent:
sorun ve araştırma soruları
Coding Agent:
ilgili dosyalar ve acceptance criteria
Validator Agent:
beklenen davranış ve artifact
Bu yaklaşım Minimum Sufficient Context olarak düşünülebilir.
## 27. Context Isolation
Subagent'ların ayrı context kullanması ana agent'ın konuşmasının gereksiz bilgilerle dolmasını azaltabilir.
Özellikle büyük projelerde:
Ana Context
-> Project Goal
Subagent Context
-> Sadece kendi görev alanı
yaklaşımı kullanılabilir.
## 28. Workspace Isolation
Birden fazla coding agent aynı repository üzerinde çalışırken çakışmalar yaşanabilir.
Örneğin iki agent aynı dosyayı aynı anda değiştirirse değişiklikler birbirini bozabilir.
Bunu önlemek için:
- ayrı workspace
- Git worktree
- write lock
- file lease
- controlled merge
gibi yöntemler kullanılabilir.
## 29. Write Conflict
İki agent aynı kaynağı değiştirmek istiyorsa:
Agent A -> File X
Agent B -> File X
İki agent'ın kontrolsüz olarak aynı anda yazması doğru değildir.
Scheduler veya integration sistemi conflict'i yönetmelidir.
## 30. Resource Governor
Multi-agent çalışma CPU, RAM, GPU ve disk kullanımını artırabilir.
Resource Governor kavramsal olarak:
CPU usage
RAM usage
VRAM usage
Model requests
Tool requests
Build processes
takip ederek fiziksel concurrency'yi yönetebilir.
Ama logical agent takım büyüklüğünü gereksiz yere sınırlamamalıdır.
## 31. Agent Failure
Bir subagent başarısız olduğunda parent task'ın hemen başarısız olması gerekmeyebilir.
Örnek recovery:
Agent Failed -> Failure Classification -> Alternative Agent -> New Strategy -> Retry -> Validator
Gerçek dış engel yoksa teknik problem çözülmeye çalışılabilir.
## 32. Circuit Breaker
Bir agent veya tool sürekli aynı şekilde hata veriyorsa geçici olarak kullanım dışı bırakılabilir.
Örnek:
Python Agent
5 benzer failure
-> Circuit Open
-> Alternative Capability
Bu sayede sistem aynı bozuk yolu tekrar tekrar kullanmaz.
## 33. No Progress
Agent'ın çalışıyor görünmesi ilerleme olduğu anlamına gelmez.
Gerçek ilerleme örnekleri:
- yeni artifact
- yeni test sonucu
- yeni kaynak
- build state değişikliği
- hata root cause'unun doğrulanması
- acceptance kriterinin tamamlanması
Sadece tool çağrısı yapmak progress değildir.
## 34. Infinite Loop
Agent sistemlerinde önemli risklerden biri aynı işlemin tekrar tekrar yapılmasıdır.
Loop belirtileri:
- aynı tool
- aynı dosya araması
- aynı hata
- aynı strateji
- yeni evidence yok
Loop tespit edildiğinde aynı yöntemin tekrar edilmesi yerine strategy değiştirilmelidir.
## 35. HumanRequired
Bazı durumlarda gerçekten kullanıcı müdahalesi gerekir.
Örnek:
- kullanıcı tercihi
- MFA
- CAPTCHA
- ödeme
- fiziksel cihaz müdahalesi
- geri dönüşü olmayan önemli karar
Ancak:
compiler eksik
dependency eksik
build hatası
tool eksik
teknik bug
gibi durumlar mümkün olduğunda agent sistemi tarafından çözülmelidir.
## 36. Agent Memory
Agent sistemlerinde farklı memory türleri kullanılabilir.
Örnek:
Conversation Memory
Project Memory
Experience Memory
Research Memory
Verified Solution Memory
Procedural Memory
DoNotRetry Memory
Bu kayıtlar gelecekte aynı problemlerin daha hızlı çözülmesine yardımcı olabilir.
## 37. Verified Solution
Bir çözüm bir kez işe yaradı diye sonsuza kadar doğru kabul edilmemelidir.
Verified Solution kaydı:
- hangi ortamda çalıştı
- hangi sürümde çalıştı
- hangi testle doğrulandı
- ne zaman doğrulandı
bilgilerini taşıyabilir.
## 38. Memory Freshness
Framework veya dependency sürümleri değiştiğinde eski çözüm geçersiz hale gelebilir.
Bu nedenle memory kullanmadan önce:
Version Match
Environment Match
Freshness
kontrol edilmelidir.
## 39. Learning
Agent sisteminin öğrenmesi model ağırlıklarının değiştirilmesi anlamına gelmek zorunda değildir.
Öğrenme:
- daha iyi agent routing
- daha iyi task decomposition
- verified solution saklama
- DoNotRetry kuralları
- kullanıcı tercihlerini hatırlama
- daha iyi procedures
şeklinde gerçekleşebilir.
## 40. Agent'ın Kendi Sonucuna Güvenmemek
Bir agent:
PASS
SUCCESS
DONE
READY
dediği için görevin gerçekten tamamlandığı kabul edilmemelidir.
Gerçek doğrulama:
Agent Result + Artifact + Test + Runtime + Independent Validation
üzerinden yapılmalıdır.
## 41. Multi-Agent Görev Örneği
Kullanıcı:
Bu projeyi incele, sorunlarını bul, düzelt ve production seviyesine getir.
İyi bir orchestration örneği:
Master Agent
-> Research Agent: güncel teknoloji araştırması
-> Architecture Agent: mimari inceleme
-> Security Agent: güvenlik inceleme
-> Performance Agent: performans analizi
-> Coding Agents: düzeltmeler
-> Integration Agent: değişiklik birleştirme
-> Testing Agent: testler
-> Validator Agent: final doğrulama
Ana Agent bütün sonuçları koordine eder.
## 42. Başarı Kriteri
Gerçek multi-agent sistem için yalnız agent isimlerinin görünmesi yeterli değildir.
Başarı:
Gerçek AgentRun kayıtları + Gerçek görev dağılımı + Gerçek paralel çalışma + Gerçek artifacts + Fan-In + Independent Validation
ile doğrulanmalıdır.
## Sonuç
Agent ve subagent mimarileri büyük yazılım görevlerinin uzmanlık alanlarına ayrılmasını ve daha kontrollü yürütülmesini sağlayabilir.
Ancak çok sayıda agent oluşturmak tek başına iyi bir sistem oluşturmaz.
Asıl önemli olan doğru görevin doğru uzmana verilmesi, gerçek ilerlemenin evidence ile ölçülmesi, hatalarda farklı stratejilerin kullanılabilmesi ve final sonucun bağımsız şekilde doğrulanmasıdır.
