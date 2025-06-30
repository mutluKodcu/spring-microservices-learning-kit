# Java Temelleri - Mülakat Soruları & Cevaplar

---

## 1. Overloading nedir?

**- Cevap:**  
Overloading, aynı sınıf içinde aynı isimle birden fazla metodun yazılmasıdır; ancak bu metodlar farklı parametre imzalarına sahiptir (farklı parametre sayısı, tipi veya sırası). Bu, metotların farklı türde veya sayıda girdilerle çalışmasına izin verir. Dönüş tipi overloading için tek başına yeterli değildir.

**- Detaylı Açıklama:**  
Overloading, kod okunabilirliğini ve esnekliği artırır. Örneğin, aynı işlemi farklı veri türleriyle yapmak istediğinizde farklı isimler vermek yerine tek isimle ama farklı parametrelerle metodları yazarız. Derleyici çağrı anında en uygun metodu seçer (compile-time polimorfizm).

Java’da overload ederken dikkat edilmesi gereken, metodların işlevlerinin anlamlı ve benzer olmasıdır; aksi halde kafa karışıklığı olur. Ayrıca, dönüş tipi değişikliği overload yaratmaz, parametre imzası şarttır.

**Java 17+ Örnek:**


<!-- public class Calculator {
    public int add(int a, int b) {
        return a + b;
    }

    public double add(double a, double b) {
        return a + b;
    }

    public int add(int a, int b, int c) {
        return a + b + c;
    }
} -->
- Proje Pratiği:

Utility sınıflarda ve API tasarımında yaygın kullanılır. Örneğin String.format, Logger gibi sınıflarda farklı parametre kombinasyonları için overload metotlar bulunur. Kodun okunabilir ve bakımı kolay olması için metodların isim ve işlev tutarlılığına dikkat edilir.

2. Override nedir?
- Cevap:
Override, alt sınıfın, üst sınıftan miras aldığı bir metodun işlevini değiştirmesidir. Alt sınıf kendi ihtiyaçlarına göre metodu yeniden tanımlar.

- Detaylı Açıklama:
Override, dinamik polimorfizmin temelidir. Üst sınıf referansı alt sınıf nesnesini tutabilir, metod çağrıldığında alt sınıfın implementasyonu çalışır. Bu sayede genişletilebilir ve esnek sistemler kurulur.

Override edilen metodun imzası ve dönüş tipi üst sınıf ile aynı olmalıdır. @Override anotasyonu kullanmak derleyicinin hataları yakalaması açısından kritik.


<!-- class Animal {
    public void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    public void sound() {
        System.out.println("Dog barks");
    }
}  -->

- Proje Pratiği:
Frameworklerde callback ve event mekanizmalarında, servis katmanlarında yaygın. Örneğin Spring’in lifecycle callback metodları. Ayrıca template pattern gibi design patternlerde temel yapı. Override edilen metodlar üst sınıf kontratına uygun davranmalıdır.

3. Inheritance (Kalıtım) nedir?
- Cevap:
Kalıtım, bir sınıfın başka bir sınıfın özelliklerini (alanlar, metodlar) devralmasıdır. Böylece kod tekrarı önlenir ve hiyerarşik modelleme yapılır.

- Detaylı Açıklama:
Kalıtım “is-a” ilişkisini sağlar. Örneğin Araba bir Taşıttır. Java’da sadece tek kalıtım desteklenir ancak çoklu interface uygulanabilir. Karmaşık kalıtım yapıları yerine kompozisyon tercih edilmelidir.

Kalıtımda super ile üst sınıf üyelerine erişilir. Override ile davranış değiştirilebilir.


<!-- class Vehicle {
    public void start() {
        System.out.println("Vehicle started");
    }
}

class Car extends Vehicle {
    public void openTrunk() {
        System.out.println("Trunk opened");
    }
} -->

- Proje Pratiği:
Domain modellemede kullanılır. Ancak servis katmanında interface ve kompozisyon daha çok tercih edilir. Hibernate gibi ORM araçlarında inheritance stratejileri (single table, joined table) performans ve sorgu açısından önemlidir.

## 4. Upcasting nedir?
- Cevap:
Upcasting, alt sınıf referansının üst sınıf tipine dönüştürülmesidir. Bu dönüşüm her zaman güvenlidir ve explicit cast gerekmez.

- Detaylı Açıklama:
Upcasting ile alt sınıf nesnesini üst sınıf referansıyla tutarız. Bu, polymorphism’i kullanmamızı sağlar. Ancak üst sınıf referansı alt sınıf özel metodlarına erişemez.

Örnek: Animal a = new Dog(); burada Dog nesnesi Animal tipinde tutuluyor.


Dog dog = new Dog();
Animal animal = dog;  // Upcasting (implicit)
animal.sound();      // Dog override metod çalışır

- Proje Pratiği:
Servisler, frameworkler genelde üst sınıf veya interface tiplerinde parametre alır. Böylece farklı alt sınıf implementasyonları kolayca değiştirilebilir.

## 5. Downcasting nedir?
- Cevap:
Üst sınıf referansının alt sınıf tipine dönüştürülmesine downcasting denir. Bu işlem runtime’da tip kontrolü yapılmadan yapılırsa ClassCastException oluşabilir.

- Detaylı Açıklama:
Downcasting risklidir; önce instanceof ile nesnenin uygun sınıfa ait olup olmadığı kontrol edilmelidir. Alt sınıfa özgü metodlara erişmek için kullanılır.

<!-- Animal animal = new Dog();
if (animal instanceof Dog) {
    Dog dog = (Dog) animal; // Downcasting
    dog.bark();
} -->
- Proje Pratiği:
İyi tasarımlarda downcasting minimize edilir, interface ve polymorphism tercih edilir. Ancak frameworklerde veya legacy kodlarda gerekebilir.

## 6. Polimorfizm nedir?
- Cevap:
Polimorfizm, aynı isimde farklı davranışlara sahip metodların çalışabilmesidir. Java’da compile-time (overloading) ve runtime (overriding) polimorfizm vardır.

- Detaylı Açıklama:
Runtime polimorfizm, üst sınıf referansının alt sınıf nesnesini tutup metod çağırmasıdır. Bu, dinamik davranış değişimini sağlar. Overloading ise metodların parametre imzalarına göre derleyici tarafından seçilmesidir.


<!-- class Animal {
    public void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    @Override
    public void sound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal animal = new Dog();
        animal.sound(); // Dog barks
    }
} -->
- Proje Pratiği:
Servis mimarilerinde esneklik sağlar. Interface ve abstract class tasarımlarının temelidir. Spring gibi frameworklerde bean yönetiminde ve proxy oluşturulmasında kullanılır.

## 7. Static nedir?
- Cevap:
static anahtar kelimesi, sınıfa ait (instance değil) üyeleri belirtir. Static metodlar ve değişkenler sınıf düzeyinde olur.

- Detaylı Açıklama:
Static üyeler, nesne oluşturulmadan erişilebilir. Static metodlar instance değişkenlerine doğrudan erişemez. Utility metotlar ve ortak veri için kullanılır. static bloklar sınıf yüklendiğinde bir kere çalışır.


<!-- public class Utils {
    public static int square(int x) {
        return x * x;
    }
} -->

int result = Utils.square(5);
- Proje Pratiği:
Helper sınıflarda, singleton implementasyonlarında, constant değerlerde kullanılır. Thread-safe olması için dikkat edilmelidir.

## 8. Final nedir?
- Cevap:
final anahtar kelimesi değiştirilemeyen sabitler, override edilemeyen metodlar veya genişletilemeyen sınıflar için kullanılır.

- Detaylı Açıklama:
Final değişken atandıktan sonra değiştirilemez. Final metodlar override edilemez. Final sınıflar extend edilemez. Immutable sınıflar oluştururken final kullanımı yaygındır.

<!-- public final class Constants {
    public static final double PI = 3.1415;
} -->
- Proje Pratiği:
Immutable nesneler yaratmak, API stabilitesi sağlamak ve kod güvenliği için kullanılır. Özellikle thread-safe yapıların temelidir.

## 9. Super ve this arasındaki farklar nelerdir?
- Cevap:
this içinde bulunduğunuz nesneyi, super ise üst sınıf nesnesini ifade eder. this yapıcılar veya metodlar arasında referans verirken, super üst sınıf metod ve yapıcılarını çağırmak için kullanılır.

- Detaylı Açıklama:
this overload metodları veya yapıcıları çağırmak için kullanılırken, super override edilen metodları veya üst sınıf yapıcılarını çağırır. super olmadan override edilen metodlara erişilemez.
<!-- 
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    void sound() {
        super.sound();
        System.out.println("Dog barks");
    }
} -->
- Proje Pratiği:
Kalıtımda davranış genişletirken kullanılır. Yapıcı zincirlemelerinde ve metot override’da önemli.

## 10. Integer ve int arasındaki fark nedir?
- Cevap:
int ilkel (primitive) veri tipidir, Integer ise int’in nesne (wrapper) karşılığıdır.

- Detaylı Açıklama:
int performanslıdır, null değer alamaz. Integer ise nesne olduğu için null olabilir, koleksiyonlarda ve generics ile kullanılabilir. Autoboxing/unboxing mekanizması sayesinde arada dönüşüm kolaydır.

Java 17+ Örnek:

int primitive = 5;
Integer wrapper = Integer.valueOf(5); // veya Integer wrapper = 5; autoboxing
- Proje Pratiği:
Koleksiyonlar ve API parametrelerinde Integer kullanılır. Performans kritik kodlarda int tercih edilir. Null kontrolü gereken yerlerde Integer kullanmak zorunludur.

## 11. == ve equals arasındaki fark nedir?
- Cevap:
== referansların aynı nesneye işaret edip etmediğini kontrol ederken, equals() nesnelerin içerik olarak eşit olup olmadığını kontrol eder.

- Detaylı Açıklama:
== ilkel tiplerde değer karşılaştırması yapar, nesnelerde ise referans karşılaştırması. equals() metodunu sınıflar override ederek içerik karşılaştırması için kullanılır. String, Wrapper sınıfları equals() metodunu içerik için override etmiştir.

Java 17+ Örnek:

String a = new String("test");
String b = new String("test");

System.out.println(a == b);       // false, farklı referanslar
System.out.println(a.equals(b));  // true, içerik aynı
- Proje Pratiği:
Nesne karşılaştırmalarında equals() kullanmak doğru yaklaşımdır. Koleksiyonların (Set, Map) düzgün çalışması için equals ve hashCode metodlarının override edilmesi şarttır.

## 12. HashCode ile equals arasındaki fark nedir?
- Cevap:
equals() nesnelerin eşitliğini tanımlar, hashCode() ise nesnenin hash kodunu (sayısal temsil) döner. hashCode() ve equals() birlikte kullanılır.

- Detaylı Açıklama:
Hash tabanlı koleksiyonlarda (HashMap, HashSet) hashCode() nesnenin konumunu belirler, equals() ise eşitlik kontrolünü yapar. Eğer iki nesne equals() ile eşitse, hashCode() değerleri de aynı olmalıdır. Aksi halde koleksiyonların davranışı bozulur.

Java 17+ Örnek:

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
- Proje Pratiği:
Model sınıflarında equals ve hashCode’un doğru implementasyonu şarttır. IDE veya Lombok @EqualsAndHashCode ile kolayca oluşturulabilir.

## 13. Java'da new operatörü kullanılarak oluşturulan nesnede heap ve stack ilişkisi nasıldır?
- Cevap:
new ile oluşturulan nesne heap bellekte yer alır, nesnenin referansı ise stack üzerinde tutulur.

- Detaylı Açıklama:
Metod içindeki lokal değişkenler stack’te, nesneler heap’te saklanır. Stack yönetimi hızlıdır, metod bitince temizlenir. Heap GC tarafından yönetilir. Referans değişkenleri stack’te tutar, nesnenin gerçek verisi heap’te bulunur.

public void foo() {
    String s = new String("hello"); // "hello" heap'te, s stack'te referans
}
- Proje Pratiği:
Bellek yönetimini anlamak performans ve hata ayıklamada kritiktir. Özellikle büyük veri yapılarında heap kullanımı dikkatle yapılmalı, gereksiz referanslar temizlenmelidir.

## 14. Java’da Pass by Reference mı, Pass by Value mı kullanılır?
- Cevap:
Java’da tüm parametreler pass-by-value (değer ile) geçirilir. Ancak nesne referansları değer olarak kopyalanır.

- Detaylı Açıklama:
Primitive tipler doğrudan değer olarak kopyalanır. Nesne tiplerinde ise referansın kopyası metotlara iletilir. Bu nedenle metodun içinde nesnenin içeriği değiştirilebilir ama referansın kendisi değiştirilemez.


<!-- public void changeValue(int a) {
    a = 5; // Orijinal değişken etkilenmez
}

public void changeObject(Person p) {
    p.setName("New Name"); // Nesne içeriği değişir
} -->
- Proje Pratiği:
Referans tipi değişkenlerde değişiklik yaparken yan etkiler olabileceği için dikkat gerekir. Immutable objeler kullanmak yan etkileri engeller.

## 15. Encapsulation nedir?
- Cevap:
Encapsulation, veri ve metodların tek bir sınıf içinde toplanması ve verilerin dışarıdan doğrudan erişiminin kısıtlanmasıdır.

- Detaylı Açıklama:
Veri gizliliği için alanlar private yapılır, public getter/setter metodlarıyla kontrollü erişim sağlanır. Böylece nesne durumu dış müdahalelerden korunur ve kontrollü yönetilir.

<!-- public class Person {
    private String name;
    public String getName() { return name; }
    public void setName(String name) { this.name = name; }
} -->
- Proje Pratiği:
Encapsulation, nesne yönelimli tasarımın temelidir. Kodun sürdürülebilirliği ve güvenliği için önemlidir. Spring Bean’lerde de kapsülleme standarttır.

## 16. Java'da üç değerden en büyüğünü bulan tek satırlık kod nasıl yazılır?
- Cevap:
Java 8 ve sonrası için Math.max metodunu zincirleyerek veya Stream API ile yapılabilir.

- Detaylı Açıklama:
Math.max(a, Math.max(b, c)) klasik çözüm. Stream API ile IntStream.of(a, b, c).max().getAsInt() de kullanılabilir. Bu, esnek ve okunaklıdır.

int max = Math.max(a, Math.max(b, c));

// veya

int max = IntStream.of(a, b, c).max().orElseThrow();
- Proje Pratiği:
Küçük hesaplamalarda basit ve okunaklı çözümler tercih edilir. Stream API daha geniş koleksiyonlar için uygundur.

## Stream API kullanmadan, sadece temel if-else yapısıyla üç değerden en büyüğünü bulmak için basit ve anlaşılır bir yöntem şöyle olur:

<!-- int max(int a, int b, int c) {
    int max = a;
    if (b > max) {
        max = b;
    }
    if (c > max) {
        max = c;
    }
    return max;
} -->
Açıklama:

İlk önce a'yı maksimum kabul ediyoruz.

Sonra b ile karşılaştırıp büyükse max'ı güncelliyoruz.

Sonra c ile karşılaştırıp yine büyükse max'ı güncelliyoruz.

Sonuçta max değişkeni en büyük değeri tutuyor.

Proje pratiğinde nasıl kullanılır?
Basit karşılaştırmalar için bu yapı, performans açısından çok iyi ve bağımsızdır. Örneğin bir servis metodunda üç farklı ölçüm sonucundan en büyüğünü bulmak gerektiğinde veya UI’da en büyük değeri göstermek için tercih edilir.