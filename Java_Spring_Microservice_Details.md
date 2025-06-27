
# 1. Java

### Thread ve Concurrency
- **Thread**: Java'da bir programın aynı anda birden çok iş yapmasını sağlar. Her bir iş "thread" olarak adlandırılır.
- **synchronized**: Paylaşılan veriye erişim sırasında diğer threadlerin müdahalesini engellemek için kullanılır. Kilit mekanizmasıdır.
- **volatile**: Değişkenin değerinin tüm thread'ler tarafından en güncel haliyle okunmasını sağlar. CPU cache gibi optimizasyonların veri tutarsızlığına yol açmasını engeller.
- **Locks (ReentrantLock, ReadWriteLock)**: Daha esnek kilitleme mekanizmalarıdır. `synchronized`'a göre daha fazla kontrol sağlar.
- **ExecutorService**: Thread yönetimini soyutlayan yapı. Thread havuzu oluşturup, işlerin paralel ve kontrollü çalışmasını sağlar.
- **ForkJoinPool**: Büyük işleri parçalara bölerek (fork) ve sonuçları birleştirerek (join) işleyen paralel işlem havuzu.

### Koleksiyonlar
- **HashMap**: Anahtar-değer çiftlerini tutar, hızlı erişim sağlar. Thread-safe değildir.
- **ConcurrentHashMap**: Thread-safe HashMap versiyonudur, yüksek performans için segmentlere ayrılmıştır.
- **CopyOnWriteArrayList**: Thread-safe liste, yazma işlemleri sırasında kopyalama yapar. Okuma işlemleri için uygundur.
- **WeakHashMap**: Anahtarları zayıf referansla tutar, garbage collector'a yakalanabilir, cache senaryolarında kullanılır.

### Design Patterns
- **Singleton**: Bir sınıfın yalnızca bir örneğinin olmasını sağlar.
- **Builder**: Karmaşık nesnelerin adım adım inşasını kolaylaştırır.
- **Decorator**: Nesnelere çalışma zamanında yeni işlevsellik ekler.
- **Factory**: Nesne yaratma işlemlerini merkezi bir fabrika sınıfına devreder.
- **Strategy**: Algoritmaları değiştirilebilir hale getirir, aynı işlemi farklı şekillerde yapmaya izin verir.

### Stream API ve Lambda
- **Stream API**: Koleksiyon verilerinin işlenmesini fonksiyonel stil ile sağlar (map, filter, reduce).
- **Lambda**: Anonim fonksiyonlar, fonksiyonel programlamaya izin verir.

### Exception Handling ve Immutability
- **Exception Handling**: Hataların yakalanması ve yönetilmesi (try-catch-finally, checked ve unchecked exceptions).
- **Immutability**: Nesnelerin değiştirilemez olması, thread-safe ve hata azaltıcı.


# 2. Spring Framework & Spring Boot

### Dependency Injection (DI) ve Bean Yaşam Döngüsü
- DI, nesnelerin bağımlılıklarının dışarıdan sağlanmasıdır (loosely coupled).
- **Bean scope**: singleton, prototype, request, session.
- **Lazy initialization**: Bean'in ihtiyaç duyulduğunda yaratılması.
- **Qualifier**: Aynı türden birden fazla bean varsa hangisinin kullanılacağını belirtir.

### Spring Boot Otomatik Konfigürasyon ve Profil Yönetimi
- Spring Boot, uygulama ortamına göre otomatik ayarları yapar.
- Profil yönetimi ile farklı ortamlar için (dev, test, prod) farklı konfigürasyonlar kullanılabilir.

### Transaction Management ve Veri Erişim
- **@Transactional** anotasyonu ile işlemler atomik hale getirilir.
- JPA (Java Persistence API) ile veritabanı erişimi kolaylaştırılır.

### Spring Security
- **Authentication**: Kullanıcı doğrulama işlemleri.
- **Authorization**: Yetki kontrolü.
- **JWT**: JSON Web Token ile stateless güvenlik.
- **OAuth2**: Yetkilendirme protokolü.
- **CSRF**: Cross-site request forgery koruması.
- **Password hashing**: Parolaların güvenli şekilde saklanması (bcrypt, PBKDF2).

### Spring Actuator
- Uygulamanın durumu ve metriklerinin izlenmesini sağlar.
- Özel endpointler oluşturma, log seviyelerini değiştirme imkanı verir.

### Exception Handling (ControllerAdvice)
- Merkezi ve tutarlı hata yönetimi sağlar.


# 3. Microservice Mimarisi

### API Gateway ve Service Discovery
- API Gateway: Tüm microservice çağrılarının merkezi noktası.
- Service Discovery (Eureka, Consul): Servislerin otomatik kayıt ve keşfi.

### Config Server ve Merkezi Konfigürasyon Yönetimi
- Tüm microservislerin konfigürasyonlarının merkezi ve dinamik yönetimi.

### Circuit Breaker (Hystrix, Resilience4j)
- Servis çağrılarında hata ve gecikmeleri yönetmek için devre kesici mekanizma.

### Event-driven Architecture
- Mesaj kuyrukları ve yayın-abone sistemi (Kafka, RabbitMQ).

### Distributed Tracing ve Monitoring
- Zipkin, Jaeger gibi araçlarla servis çağrılarının takibi.

### Design Patterns
- **Bulkhead**: Sistem kaynaklarını izole ederek hata yayılmasını önler.
- **Sidecar**: Servis dışı ama yanında çalışan yardımcı servis.
- **Saga**: Uzun süreli işlem yönetimi ve veri tutarlılığı.
- **CQRS**: Okuma ve yazma işlemlerinin ayrılması.

### Rate Limiting ve Güvenlik
- API çağrılarının sınırlandırılması, kötü niyetli trafik önleme.

# 4. Genel Yazılım Mühendisliği ve Tasarım Prensipleri

### SOLID Prensipleri
- Yazılım tasarımında temel beş prensip (Single Responsibility, Open/Closed, Liskov Substitution, Interface Segregation, Dependency Inversion).

### Clean Code ve Testability
- Okunabilir, sürdürülebilir ve test edilebilir kod yazma.

### Exception Handling Stratejileri
- Hata yönetimi planlama, loglama, geri bildirim.

### Immutable Object Kullanımı
- Değişmez nesneler ile güvenli ve hatasız kod.

### Asenkron Programlama ve Callback Zincirleme
- CompletableFuture ile asenkron görevlerin zincirlenmesi ve yönetimi.


# Öneriler

- ** concurrency ve design pattern **  
 Thread yönetimi, kilitleme mekanizmaları ve tasarım kalıpları

- **Spring Security detaylı öğrenilmeli.**  
 Authentication, Authorization, JWT, OAuth2 gibi kavramlar ile CSRF koruması ve parola hashleme yöntemleri

- **Microservice altyapısı ve patternleri mutlaka kavra.**  
 Service discovery, circuit breaker, event-driven yapılar ve saga gibi patternler

- **Stream API ve Java 8+ **  
 Fonksiyonel programlama, koleksiyon işlemleri için Stream API

- **Spring Boot Actuator ve merkezi konfigürasyon konularını unutma.**  
 Monitoring ve konfigürasyon yönetimi


# Detaylar

### 1. Concurrency (Eşzamanlılık)
- Bir programın aynı anda birden fazla işi (thread) yapabilme yeteneğidir.
- Java’da thread oluşturma, thread’ler arası iletişim, senkronizasyon (synchronized, locks), thread-safe koleksiyonlar gibi konuları kapsar.
- Doğru yönetilmediğinde “deadlock” (kilitlenme), “race condition” (yarış durumu) gibi problemler yaşanabilir.
- Java’da concurrency için `ExecutorService`, `ForkJoinPool`, `CompletableFuture` gibi API’ler bulunur.

### 2. Design Patterns (Tasarım Kalıpları)
- Yazılım geliştirirken tekrar eden problemler için kanıtlanmış çözüm yöntemleridir.
- Örneğin, Singleton kalıbı “bir sınıfın tek örneğinin olmasını sağlamak” için kullanılır.
- Diğer önemli kalıplar: Factory (nesne oluşturma), Strategy (algoritma seçimi), Decorator (dinamik özellik ekleme), Builder (karmaşık nesne inşası).

### 3. Spring Security
- Java uygulamalarında kimlik doğrulama ve yetkilendirme sağlayan güvenlik çatısıdır.
- **Authentication**: Kullanıcının kim olduğunu doğrulama.
- **Authorization**: Kullanıcının hangi kaynaklara erişim hakkının olduğunu belirleme.
- **JWT (JSON Web Token)**: Stateles güvenlik için kullanılan token tabanlı doğrulama yöntemi.
- **OAuth2**: Üçüncü taraf uygulamalar için yetkilendirme protokolü.
- **CSRF (Cross-Site Request Forgery)**: Web saldırılarına karşı koruma mekanizması.
- **Password hashing**: Parolaların güvenli şekilde saklanması için hash algoritmaları (bcrypt, PBKDF2).

### 4. Microservice Altyapısı ve Patternleri
- Uygulamanın küçük, bağımsız ve yönetilebilir parçalara (servislere) ayrıldığı mimari tarz.
- **Service Discovery**: Servislerin dinamik olarak bulunması ve iletişim kurması (ör. Eureka, Consul).
- **Circuit Breaker**: Servisler arası iletişimde hata veya gecikme olduğunda sistemi koruyan devre kesici (Hystrix, Resilience4j).
- **Event-driven architecture**: Mesajlaşma temelli asenkron iletişim (Kafka, RabbitMQ).
- **Saga Pattern**: Dağıtık işlemlerde veri tutarlılığını sağlamak için kullanılan uzun süreli işlem koordinasyonu.
- **CQRS (Command Query Responsibility Segregation)**: Okuma ve yazma işlemlerinin ayrı yönetilmesi.
- **Bulkhead Pattern**: Hataların yayılmasını engellemek için sistem kaynaklarını izole etme.
- **Sidecar Pattern**: Ana servise destek veren yardımcı servislerin yan yana konuşlandırılması.

### 5. Stream API ve Java 8+ Özellikleri
- **Stream API**: Koleksiyonlar üzerinde fonksiyonel programlama yaparak, map, filter, reduce gibi işlemleri kolaylaştırır.
- **Lambda ifadeleri**: Fonksiyonel programlama için kısa ve anonim fonksiyon tanımlama yöntemi.
- Java 8 ile gelen bu özellikler kodun daha okunabilir, kısa ve performanslı olmasını sağlar.

### 6. Spring Boot Actuator ve Merkezi Konfigürasyon
- **Spring Boot Actuator**: Uygulamanın sağlık durumu, metrikleri, log seviyesi gibi operasyonel verilerini sunar.
- **Merkezi Konfigürasyon Yönetimi (Config Server)**: Tüm microservice’lerin konfigürasyonlarını tek bir yerden yönetme imkanı.
- Bu sayede uygulama yönetimi, hata takibi ve bakım işlemleri kolaylaşır.
