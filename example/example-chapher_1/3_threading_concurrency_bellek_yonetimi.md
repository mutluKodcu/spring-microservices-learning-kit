# Threading, Concurrency & Bellek Yönetimi

## 1. Java multithreading ve senkronizasyon nasıl yapılır?
- Cevap:
Java’da multithreading, birden fazla iş parçacığının (thread) aynı anda çalıştırılmasıdır. Senkronizasyon ise bu iş parçacıklarının paylaşılan kaynaklara erişimini düzenleyerek veri tutarlılığını sağlar.

- Detaylı Açıklama:
Thread yaratmak için Thread sınıfını extend etmek veya Runnable interface’ini implement etmek gerekir. Paylaşılan verilere erişim sırasında synchronized anahtar kelimesi veya Lock mekanizmaları kullanılır. Bu sayede yarış koşulları (race condition) ve tutarsızlık engellenir.

<!-- class Counter {
    private int count = 0;

    public synchronized void increment() {
        count++;
    }

    public int getCount() {
        return count;
    }
}

public class Main {
    public static void main(String[] args) throws InterruptedException {
        Counter counter = new Counter();
        Thread t1 = new Thread(() -> {
            for (int i = 0; i < 1000; i++) counter.increment();
        });
        Thread t2 = new Thread(() -> {
            for (int i = 0; i < 1000; i++) counter.increment();
        });
        t1.start();
        t2.start();
        t1.join();
        t2.join();
        System.out.println("Count: " + counter.getCount()); // Beklenen 2000
    }
} -->
- Proje Pratiği:
Concurrency hatalarını önlemek için senkronizasyon çok kritik. Ancak aşırı senkronizasyon performans sorunlarına yol açabilir, bu yüzden ihtiyaç kadar kullanılmalı.

# 2. Lock sınıfı ile synchronized blokların farkları nelerdir?
- Cevap:
synchronized JVM destekli ve blok/metod bazlı senkronizasyon sağlar; Lock ise java.util.concurrent.locks paketiyle gelen daha esnek ve gelişmiş kilitleme mekanizmasıdır.

- Detaylı Açıklama:

Lock kilidi manuel açıp kapatmayı gerektirir (lock() ve unlock()).
Lock ile zaman aşımı ve kesintiye duyarlı kilitleme (tryLock) gibi gelişmiş özellikler kullanılabilir.
synchronized otomatik olarak blok bitince kilidi bırakır.
Lock daha kontrollüdür, deadlock önleme ve performans için avantaj sağlar.

Lock lock = new ReentrantLock();

lock.lock();
try {
    // kritik bölüm
} finally {
    lock.unlock();
}
- Proje Pratiği:
Performans kritik ve karmaşık senkronizasyonlarda Lock tercih edilir. Basit durumlarda synchronized yeterlidir.

# 3. synchronized ile Lock sınıfı arasındaki fark nedir?
- Cevap:
Bu soru 2 ile benzer, özetle:

synchronized blok/metod tabanlı, otomatik kilit yönetimi sağlar.

Lock manuel kilit yönetimi, daha fazla esneklik ve fonksiyonellik sunar.

- Detaylı Açıklama:
synchronized JVM seviyesinde optimize edilirken, Lock kullanıcıya daha fazla kontrol verir (örneğin zaman aşımıyla kilit alma).

# 4. volatile ve AtomicInteger farkları nedir?
- Cevap:
volatile değişkenin değerinin her zaman ana hafızadan okunmasını garanti eder ama atomik işlemler sağlamaz. AtomicInteger ise atomik olarak artış, azalış gibi işlemler yapar.

- Detaylı Açıklama:

volatile sadece değişkenin görünürlüğünü garantiler, örn. boolean flag.

AtomicInteger ve diğer atomik sınıflar CAS (Compare-And-Swap) mekanizması kullanarak thread-safe sayısal işlemler sağlar.

volatile boolean flag = true;

AtomicInteger counter = new AtomicInteger(0);
counter.incrementAndGet();  // Atomik artış
- Proje Pratiği:
Sadece görünürlük gerektiğinde volatile, artan veya azalan sayılar için AtomicInteger tercih edilir.

# 5. ExecutorService nedir ve neden kullanılır?
- Cevap:
ExecutorService, Java’nın thread yönetimini soyutlayan ve iş parçacığı havuzu (thread pool) sağlayan bir framework’tür.

- Detaylı Açıklama:
Doğrudan Thread oluşturmak yerine, görevleri ExecutorServicee vererek performanslı, yönetilebilir ve ölçeklenebilir concurrency sağlanır. Thread havuzu sayesinde thread yaratma maliyetleri azalır.

<!-- ExecutorService executor = Executors.newFixedThreadPool(5);
executor.submit(() -> System.out.println("Task çalışıyor"));
executor.shutdown(); -->
- Proje Pratiği:
Yüksek performanslı uygulamalarda thread havuzu mutlaka kullanılmalı. Özellikle web sunucuları, mikroservisler ve batch işlemlerde tercih edilir.

# 6. Object Pool Pattern nedir? Connection Pool örneği veriniz.
- Cevap:
Object Pool Pattern, pahalı oluşturma maliyeti olan nesnelerin önceden yaratılıp havuzda tutulmasıdır. Kullanım sonrası nesneler havuza geri verilir.

- Detaylı Açıklama:
En yaygın örnekleri connection pool’udur. Veritabanı bağlantıları açmak pahalıdır, pool sayesinde mevcut bağlantılar tekrar kullanılır.

Connection Pool Örneği:

Spring Boot’ta HikariCP gibi popüler pool kullanılır:

<!-- spring.datasource.hikari.maximum-pool-size=10
spring.datasource.url=jdbc:mysql://localhost:3306/mydb
spring.datasource.username=user
spring.datasource.password=pass -->

- Proje Pratiği:
Performans ve kaynak yönetimi için connection pool kullanımı zorunludur. Ayrıca thread-safe havuzların doğru yönetilmesi gerekir.

# 7. Garbage Collector nasıl çalışır? WeakReference ve SoftReference nedir?
- Cevap:
Garbage Collector (GC), JVM’de kullanılmayan nesneleri otomatik temizleyerek bellek yönetimi sağlar.

- Detaylı Açıklama:
GC reachability analiz yapar; erişilemeyen nesneler toplanır.
WeakReference: Nesnenin sadece weak referansı varsa GC tarafından hemen toplanabilir.
SoftReference: Bellek düşükse toplanır, genelde cache için kullanılır.


<!-- WeakReference<MyObject> weakRef = new WeakReference<>(new MyObject());
SoftReference<MyObject> softRef = new SoftReference<>(new MyObject()); -->

- Proje Pratiği:
Cache, memory-sensitive uygulamalarda soft ve weak referanslar tercih edilir. Doğru referans tipinin seçilmesi bellek sızıntılarını önler.

# 8. Java’da Garbage Collector çeşitleri nelerdir?

- Cevap:
Serial GC: Tek iş parçacıklı, küçük uygulamalar için.
Parallel GC: Çok iş parçacıklı, yüksek throughput.

CMS (Concurrent Mark Sweep) GC: Düşük gecikmeli uygulamalar için (Java 8’e kadar).
G1 GC: Büyük heap ve düşük duraklama hedefler, Java 9+ standart.
ZGC ve Shenandoah: Java 11+ ultra düşük duraklama hedefli GC’ler.

- Proje Pratiği:
Uygulamanın türüne göre GC seçilir. Örneğin web uygulamalarında G1 veya ZGC tercih edilir.

# 9. CompletableFuture ile asenkron işlemler nasıl yönetilir?
- Cevap:
CompletableFuture, asenkron ve event-driven programlamada kullanılabilen Future’ın gelişmiş halidir.

- Detaylı Açıklama:
Bir işlemi arka planda başlatır ve tamamlandığında sonuçla işlem yapmayı sağlar. Zincirleme, hata yönetimi ve paralel çalıştırma gibi yetenekleri vardır.

CompletableFuture.supplyAsync(() -> {
    return "Sonuç";
}).thenAccept(result -> {
    System.out.println("İşlem sonucu: " + result);
});
- Proje Pratiği:
Asenkron I/O, web servis çağrıları, paralel veri işleme için uygundur. Callback hell’i önler.

# 10. Java’da Thread, Runnable, ExecutorService farkı nedir?
- Cevap:

Thread: Çalıştırılabilir iş parçacığı nesnesi.
Runnable: Çalıştırılabilir iş yükünü tanımlayan fonksiyonel interface.
ExecutorService: Thread havuzlarını ve task yönetimini soyutlar.
- Detaylı Açıklama:
Runnable iş yapısını belirtir, Thread bunu çalıştırır. ExecutorService thread oluşturma ve yönetimini kolaylaştırır.

<!-- Runnable task = () -> System.out.println("Çalışıyor");
Thread thread = new Thread(task);
thread.start();

// ExecutorService ile
ExecutorService executor = Executors.newFixedThreadPool(2);
executor.submit(task);
executor.shutdown(); -->

- Proje Pratiği:

Modern Java projelerinde doğrudan Thread yerine ExecutorService tercih edilir, yönetim kolaylığı ve performans için.

