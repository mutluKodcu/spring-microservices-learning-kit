# Java & Spring Soruları

## 🧠 Java Temelleri
- Overloading nedir?
- Override nedir?
- Inheritance (Kalıtım) nedir?
- Upcasting nedir?
- Downcasting nedir?
- Polimorfizm nedir?
- Static nedir?
- Final nedir?
- Super ve this arasındaki farklar nelerdir?
- Integer ve int arasındaki fark nedir?
- == ve equals arasındaki fark nedir?
- HashCode ile equals arasındaki fark nedir?
- Java'da new operatörü kullanılarak oluşturulan nesnede heap ve stack ilişkisi nasıldır?
- Java’da Pass by Reference mı, Pass by Value mı kullanılır?
- Encapsulation nedir?
- Java'da üç değerden en büyüğünü bulan tek satırlık kod nasıl yazılır?

## 📚 Koleksiyonlar & Veri Yapıları
- Java koleksiyonlarından LinkedList, HashSet, TreeSet arasındaki farklar nelerdir?
- HashMap ve TreeMap arasındaki farklar nelerdir?
- Java’da HashMap, TreeMap, LinkedHashMap farkları nelerdir?
- HashSet ve HashMap kullanırken hashCode() ve equals() metodlarının rolü nedir?
- Diziler ve koleksiyonlar arasındaki farklar nelerdir?
- Thread-Safe olmayan koleksiyon nasıl Thread-Safe yapılır?
- Autoboxing ve unboxing nasıl çalışır?

## 🔐 Veri Tipleri & İfadeler
- Java primitif veri tipleri (int, long, float, double) arasındaki farklar nelerdir?
- Primitif veri tipleri ile wrapper sınıflar arasındaki farklar nelerdir?
- char veri tipi ve Unicode nedir?
- null ve Optional arasındaki farklar nelerdir?
- String ve StringBuilder farkları nelerdir?
- float ve double hassasiyet farkları nelerdir?
- instanceof operatörü nasıl çalışır?
- BigInteger ve BigDecimal farkları nelerdir?
- int ve Integer farkı nedir?

## 🧵 Threading, Concurrency & Bellek Yönetimi
- Java multithreading ve senkronizasyon nasıl yapılır?
- Lock sınıfı ile synchronized blokların farkları nelerdir?
- synchronized ile Lock sınıfı arasındaki fark nedir?
- volatile ve AtomicInteger farkları nedir?
- ExecutorService nedir ve neden kullanılır?
- Object Pool Pattern nedir? Connection Pool örneği veriniz.
- Garbage Collector nasıl çalışır? WeakReference ve SoftReference nedir?
- Java’da Garbage Collector çeşitleri nelerdir?
- CompletableFuture ile asenkron işlemler nasıl yönetilir?
- Java’da Thread, Runnable, ExecutorService farkı nedir?

## 🔍 Gelişmiş Java Özellikleri - Advanced Java Features
- Java Streams API nasıl çalışır ve ne zaman kullanılır?
- Reflection API nedir ve nasıl kullanılır?
- Lambda ifadeleri nedir? Avantajları nelerdir?
- Java 8 default metodlar nedir?
- Optional sınıfı neden tercih edilir?
- Java’da Checked ve Unchecked Exception farkları nelerdir?
- try-catch blokları ve throws kullanımı nedir?
- Custom Exception nasıl oluşturulur ve ne zaman kullanılır?
- InputStream, OutputStream, Reader, Writer farkı nedir?
- Dosya işlemlerinde File, Path ve Files nasıl kullanılır?

## 🧩 Tasarım Kalıpları
- Singleton Design Pattern nedir? Thread-safe nasıl yapılır?
- Factory Pattern nedir? Abstract Factory ile farkları nelerdir?
- Observer Design Pattern nedir? Spring ile kullanımı nasıldır?
- Decorator Design Pattern nedir? Ne işe yarar?
- Adapter Design Pattern nedir? Ne zaman kullanılır?
- Design pattern'ler arasındaki temel farklar nelerdir?

## 📆 Tarih ve Saat API'leri
- LocalDate, LocalTime, LocalDateTime ve ZonedDateTime farkları
- DateTimeFormatter nasıl kullanılır?
- Spring Boot'ta @DateTimeFormat, @JsonFormat, @Temporal anotasyonları nasıl kullanılır?
- ZonedDateTime JSON formatlama örneği
- Clock sınıfı nasıl çalışır?

## 🧬 Spring Framework
- Dependency Injection ve IoC prensipleri
- Spring AOP nedir ve nerede kullanılır?
- Spring Security ile JWT entegrasyonu nasıl yapılır?
- Spring Security ile güvenlik açıklarına karşı önlem nasıl alınır?
- @Transactional nasıl çalışır? İç içe transaction örnekleri
- Spring Boot Actuator nedir, hangi metrikleri sağlar?
- Spring Data JPA nedir ve nasıl kullanılır?
- @Query, @Modifying, @Transactional anotasyonları ne işe yarar?
- Dinamik sorgular Spring Data ile nasıl yazılır?
- Spring Data'da connection pool yapılandırması nasıl yapılır?
- Hibernate avantajları ve Spring Boot ile entegrasyonu
- Hibernate cache nasıl kullanılır? Performansa etkisi nedir?
- Lazy loading ve eager loading farkları nelerdir?
- OneToMany ve ManyToOne ilişkileri nasıl kurulur?
- JPA ve Hibernate arasındaki farklar nelerdir?
- Hibernate @OptimisticLocking vs @PessimisticLocking farkı nedir?

## 🚀 Spring Boot Uygulama Geliştirme
- Spring Boot başlangıç anotasyonları nedir?
- application.properties ve application.yml dosyalarının rolü nedir?
- Spring Boot bağımlılık enjeksiyonu nasıl yapılır?
- Mikroservis mimarisi kurarken dikkat edilmesi gerekenler
- Web servisi için gerekli bağımlılıklar nelerdir?
- CORS yönetimi nasıl yapılır?
- Auto configuration nasıl çalışır? (@EnableAutoConfiguration, @ConfigurationProperties)

## ⏱ Zamanlanmış Görevler (@Scheduled)
- @Scheduled: fixedRate, fixedDelay farkları
- cron ifadesi ile zamanlama örnekleri
- timezone ayarı nasıl yapılır?
- Asenkron zamanlanmış görevler nasıl çalışır?
- Hatalı görev yönetimi nasıl yapılır?
- Görevleri duraklatma ve yeniden başlatma
- Görev çakışmalarını önleme yolları
- @Scheduled görevlerini sıralı çalıştırma yapısı

## 🧱 Mikroservis Mimarisi
- Mikroservis yapısını nasıl tasarlarsınız?
- API tasarımı, veri yönetimi ve servis iletişimi
- Hata yönetimi ve güvenlik stratejileri
- Event-Driven Architecture nedir? Kafka, RabbitMQ, ActiveMQ farkları
- Resilience4j ile Circuit Breaker kullanımı
- Reactive programming: Avantajları ve kullanım alanları
- Redis kullanım senaryoları ve entegrasyonu
- Gateway, Config Server, Discovery Service nasıl yapılandırılır?

## 🛠 Ekstra - Spring Kullanım Senaryoları
- Spring, bir interface’in iki implementasyonundan hangisini seçer?
- Polimorfizm ile Lock mekanizması nasıl tasarlanır?
- WebFlux hangi durumlarda tercih edilir?
- Spring Boot’ta performans iyileştirme stratejileri (caching, async, lazy loading)

## 🆕 Ekstra Modern ve İleri Seviye Sorular

### Java Gelişmiş Konular
- Java Memory Model (JMM) nedir? Hafıza tutarlılığı (memory consistency) nasıl sağlanır?
- CompletableFuture ve reactive programming farkları nelerdir? Ne zaman hangisi tercih edilir?
- Java 9 ile gelen Modüler Sistem (JPMS) nasıl çalışır ve avantajları nelerdir?
- Record tipi nedir? Ne zaman kullanılır?
- Sealed class nedir? Avantajları nelerdir?

### Spring Gelişmiş Konular
- Spring WebFlux ve Spring MVC arasındaki farklar nelerdir? Reactive programlama ne zaman tercih edilir?
- Spring Security’de OAuth2 ve OpenID Connect nasıl entegre edilir? Temel çalışma mantığı nedir?
- Spring Cloud Config nasıl çalışır? Merkezi konfigürasyon yönetimi nasıl yapılır?
- Spring Boot Actuator ile custom metrikler nasıl oluşturulur ve izlenir?
- Spring Batch nedir? Ne zaman kullanılır?

### Java 17 ve Sonrası Yenilikleri
- Java 17’nin getirdiği önemli yenilikler nelerdir? (Örnek: Sealed Classes, Pattern Matching for switch, Records)
- Sealed class nedir? Ne zaman ve nasıl kullanılır? Avantajları nelerdir?
- Record sınıflar nedir? Immutable nesneler için neden tercih edilir?
- Pattern Matching nedir? instanceof ile nasıl kullanılır?
- Switch ifadesinde pattern matching nasıl çalışır?
- Java 17’de eklenen yabancı fonksiyon ve bellek API’leri (Foreign Function & Memory API) nedir?
- Java 17 ile birlikte gelen yeni standart kütüphane değişiklikleri veya performans iyileştirmeleri nelerdir?
