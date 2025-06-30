# Spring Microservices Learning Kit

## Java & Java Core & Advanced

Threading, Concurrency, Locks, ExecutorService
Collections, Stream API, Lambda expressions
Exception Handling, Immutability
Design Patterns (Singleton, Factory, Builder, etc.)

### Thread ve Concurrency

Thread: Java'da bir programın aynı anda birden çok iş yapmasını sağlar.
synchronized: Paylaşılan veriye erişim sırasında diğer threadlerin müdahalesini engeller.
volatile: Tüm thread'ler tarafından güncel okunmayı sağlar.
Locks: Daha esnek kilitleme (ReentrantLock, ReadWriteLock).

### ExecutorService: Thread havuzu ile yönetim.
#### ForkJoinPool: İşleri bölerek paralel çalıştırma.

### Koleksiyonlar
#### HashMap, ConcurrentHashMap, CopyOnWriteArrayList, WeakHashMap

## Design Patterns
### Singleton, Builder, Decorator, Factory, Strategy

```
| Pattern   | Gerçek Anlamı                                                 |
| --------- | ------------------------------------------------------------- |
| Singleton | Tek bir nesne yeter, çünkü merkezi yapı (örn. config, logger) |
| Builder   | Parametre çoksa nesne oluşturmak karışır → parçalara ayır     |
| Factory   | Hangi nesneyi oluşturacağına çalışma anında karar ver         |
| Strategy  | Farklı algoritmaları (örn. ödeme tipi) çalışırken seç         |
| Decorator | Mevcut nesneye yeni yetenek ekle, ama değiştirme              |

```

## Stream API & Lambda
### Fonksiyonel programlama, map-filter-reduce

#### Exception & Immutability
#### try-catch, checked/unchecked
#### Immutable objeler = thread-safe
