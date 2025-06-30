# 📚 Koleksiyonlar & Veri Yapıları

## 1. Java koleksiyonlarından LinkedList, HashSet, TreeSet arasındaki farklar nelerdir?
- Cevap:  

LinkedList: Elemanların çift bağlı liste yapısında tutulduğu, sıralı bir koleksiyondur. Eleman ekleme ve çıkarma işlemleri hızlıdır (özellikle listenin başı ve sonu), ancak rasgele erişim (index ile) yavaştır. İterasyon sırasını korur.

HashSet: Benzersiz elemanlar tutan, sırasız bir koleksiyondur. Elemanların sırası garanti edilmez. Hash tabanlı olduğu için ekleme, çıkarma ve arama işlemleri ortalama O(1) zaman karmaşıklığına sahiptir.

TreeSet: Elemanları sıralı ve benzersiz tutar. Red-Black Tree veri yapısını kullanır. Arama, ekleme ve çıkarma işlemleri O(log n) zaman alır. Doğal sıralama ya da Comparator ile sıralama sağlar.

- Detaylı Açıklama:
Kullanım amacına göre seçim yapılmalıdır. Eğer sıralı ve benzersiz elemanlar gerekiyorsa TreeSet, hızlı erişim ve sırasız benzersiz eleman gerekiyorsa HashSet, sıralı ve indeksli liste gerekiyorsa LinkedList ya da ArrayList tercih edilir. LinkedList özellikle insert/delete işlemlerinin sık olduğu durumlarda avantajlıdır.

```
// LinkedList örneği
LinkedList<String> linkedList = new LinkedList<>();
linkedList.add("A");
linkedList.addFirst("B"); // Başına ekleme hızlı

// HashSet örneği
HashSet<String> hashSet = new HashSet<>();
hashSet.add("A");
hashSet.add("B");

// TreeSet örneği
TreeSet<String> treeSet = new TreeSet<>();
treeSet.add("B");
treeSet.add("A"); // Otomatik sıralı
```
- Proje Pratiği:
Veri yapısı seçimi, performans ve işlevsellik açısından kritik. Örneğin, kullanıcı aktif liste tutarken LinkedList, benzersiz yetenek seti için HashSet, sıralı raporlama için TreeSet kullanılır.

## 2. HashMap ve TreeMap arasındaki farklar nelerdir?
- Cevap:  

HashMap: Hash tabanlı, anahtar-değer çiftlerini depolar. Sıra garantisi yoktur. Ortalama O(1) performanslı ekleme, silme ve arama sağlar.

TreeMap: Kırmızı-siyah ağaç yapısı kullanır ve anahtarları doğal sıralar ya da belirtilen Comparator'a göre sıralar. Operasyonlar O(log n) zaman karmaşıklığındadır.

- Detaylı Açıklama:
HashMap hızlıdır ama sıralama gerektirmeyen durumlarda uygundur. TreeMap sıralı erişim gerektiren durumlarda kullanılır. Null anahtar HashMap’te desteklenir ancak TreeMap’te desteklenmez.
```
HashMap<Integer, String> hashMap = new HashMap<>();
hashMap.put(2, "Two");
hashMap.put(1, "One");

TreeMap<Integer, String> treeMap = new TreeMap<>();
treeMap.put(2, "Two");
treeMap.put(1, "One"); // Sıralı tutar (1,2)
```

- Proje Pratiği:
Örneğin, önbellek uygulamalarında hızlı erişim için HashMap, raporlama ve sıralı arama için TreeMap kullanılır.

## 3. Java’da HashMap, TreeMap, LinkedHashMap farkları nelerdir?
- Cevap:  

HashMap: Sırasız, hızlı anahtar-değer yapısı.

TreeMap: Anahtarları sıralı tutar, arama O(log n).

LinkedHashMap: HashMap performansına benzer, ancak ek olarak ekleme sırasını korur (dahili çift bağlı liste kullanır). Bu sayede iterasyon sırası garantilidir.

- Detaylı Açıklama:
LinkedHashMap, önbellek implementasyonlarında (LRU cache) sıklıkla tercih edilir. TreeMap ise sıralı veri gerektiren durumlar için ideal. HashMap ise genel amaçlı ve performans odaklıdır.

```
LinkedHashMap<Integer, String> linkedHashMap = new LinkedHashMap<>();
linkedHashMap.put(3, "Three");
linkedHashMap.put(1, "One");
linkedHashMap.put(2, "Two"); // Iterasyon sırası 3,1,2
```

- Proje Pratiği:
Sisteminizde iterasyon sırası önemli ise LinkedHashMap kullanın. Performans kritik ve sıralama gerekmiyorsa HashMap tercih edin. Sıralama ve range query ihtiyaçları için TreeMap uygundur.

## 4. HashSet ve HashMap kullanırken hashCode() ve equals() metodlarının rolü nedir?
- Cevap:  
hashCode() nesnenin bir sayısal temsilini döner ve hash tabanlı koleksiyonlarda nesnenin yerini bulmak için kullanılır. equals() ise iki nesnenin içerik olarak eşit olup olmadığını kontrol eder.

- Detaylı Açıklama:
HashSet ve HashMap, hashCode() kullanarak nesnenin yerini belirler. Ancak farklı nesneler aynı hash kodunu üretebilir (collision). Bu durumda equals() metodu çağrılır. Eğer equals() false dönerse yeni nesne farklı kabul edilir. hashCode ve equals uyumlu olmalıdır; eşit nesneler aynı hash kodunu döndürmeli.

```
class Person {
    private int id;
    private String name;
    // Constructor, getter, setter

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (!(o instanceof Person)) return false;
        Person p = (Person) o;
        return id == p.id;
    }

    @Override
    public int hashCode() {
        return Objects.hash(id);
    }
}
```
- Proje Pratiği:
Custom objelerin HashSet ya da HashMap içinde doğru çalışması için equals ve hashCode metotlarının düzgün override edilmesi zorunludur. Aksi halde veri kaybı ya da hatalı arama olur.

## 5. Diziler ve koleksiyonlar arasındaki farklar nelerdir?
- Cevap:  
Diziler sabit uzunluktadır ve homojen (aynı tipte) veri tutar. Koleksiyonlar dinamik boyutlu ve heterojen olabilir (generics sayesinde tip güvenli). Koleksiyonlar ekleme, çıkarma, arama gibi zengin metodlar sunar.

- Detaylı Açıklama:
Diziler ilkel tipleri de doğrudan tutabilir, koleksiyonlar ise sadece referans tiplerle çalışır (primitive için wrapper kullanılır). Koleksiyonlar thread-safe ya da değil olarak seçilebilir. Koleksiyonlar Java Collections Framework’ün esnek yapısının parçasıdır.

int[] arr = new int[5]; // Sabit boyut

List<Integer> list = new ArrayList<>(); // Dinamik boyut, zengin metodlar
list.add(10);
- Proje Pratiği:
Sabit ve performans kritik durumlarda dizi, esnek ve genişletilebilir durumlarda koleksiyonlar tercih edilir.

## 6. Thread-Safe olmayan koleksiyon nasıl Thread-Safe yapılır?
- Cevap:  
Thread-safe olmayan koleksiyonlar, Collections.synchronizedXXX metotları ile sarmalanabilir veya java.util.concurrent paketindeki eşzamanlı (concurrent) koleksiyonlar kullanılabilir.

- Detaylı Açıklama:

Collections.synchronizedList(new ArrayList<>()) gibi metodlarla mevcut koleksiyon thread-safe hale getirilir.

Daha modern ve performanslı yöntem ise ConcurrentHashMap, CopyOnWriteArrayList gibi concurrent koleksiyonları kullanmaktır.

List<String> syncList = Collections.synchronizedList(new ArrayList<>());

// Concurrent koleksiyon örneği
ConcurrentHashMap<String, String> concurrentMap = new ConcurrentHashMap<>();
- Proje Pratiği:
Multithreaded uygulamalarda thread-safe koleksiyonlar olmazsa veri tutarsızlığı olur. Yüksek performans ve ölçeklenebilirlik için concurrent koleksiyonlar tercih edilir.

## 7. Autoboxing ve unboxing nasıl çalışır?
- Cevap:  
Autoboxing, primitive tiplerin otomatik olarak wrapper sınıf nesnelerine dönüştürülmesidir. Unboxing ise wrapper nesnelerinin primitive tiplere dönüştürülmesidir. Bu dönüşümler Java derleyicisi tarafından otomatik yapılır.

- Detaylı Açıklama:
Bu özellik Java 5 ile geldi. Örneğin, int bir değer Integer nesnesine otomatik dönüştürülür ve tersi. Ancak, otomatik dönüşümler boxing/unboxing sırasında performans kaybı ve NullPointerException riskleri oluşturabilir.

Integer boxed = 5; // Autoboxing
int primitive = boxed; // Unboxing
- Proje Pratiği:
Koleksiyonlarda ve generic yapılarda primitive tipler kullanılamadığı için autoboxing sık kullanılır. Performans kritik bölümlerde boxing/unboxing işlemlerine dikkat edilmeli.
