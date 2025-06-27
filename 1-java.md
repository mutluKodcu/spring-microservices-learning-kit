# 1. Java

## Thread ve Concurrency
- **Thread**: Java'da bir programın aynı anda birden çok iş yapmasını sağlar.
- **synchronized**: Paylaşılan veriye erişim sırasında diğer threadlerin müdahalesini engeller.
- **volatile**: Tüm thread'ler tarafından güncel okunmayı sağlar.
- **Locks**: Daha esnek kilitleme (ReentrantLock, ReadWriteLock).
- **ExecutorService**: Thread havuzu ile yönetim.
- **ForkJoinPool**: İşleri bölerek paralel çalıştırma.

## Koleksiyonlar
- **HashMap, ConcurrentHashMap, CopyOnWriteArrayList, WeakHashMap**

## Design Patterns
- Singleton, Builder, Decorator, Factory, Strategy

## Stream API & Lambda
- Fonksiyonel programlama, map-filter-reduce

## Exception & Immutability
- try-catch, checked/unchecked
- Immutable objeler = thread-safe