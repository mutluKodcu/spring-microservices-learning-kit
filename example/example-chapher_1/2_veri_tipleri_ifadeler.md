# 🔐 Veri Tipleri & İfadeler
## 1. Java primitif veri tipleri (int, long, float, double) arasındaki farklar nelerdir?
- Cevap:

int: 32 bit tamsayı. Tam sayı değerleri için en yaygın kullanılan tip.
long: 64 bit tamsayı. int’in kapasitesinden daha büyük tam sayılar için kullanılır.
float: 32 bit kayan noktalı sayı. Tek duyarlıklı (single precision) ondalıklı sayılar için.
double: 64 bit kayan noktalı sayı. Çift duyarlıklı (double precision) ondalıklı sayılar için, daha hassas.

- Detaylı Açıklama:
Tamsayılar bellekte tam olarak saklanır ve kesin sonuç verir. Ondalıklı sayılar ise IEEE 754 standardına göre saklanır ve hesaplamada yuvarlama hataları olabilir.
Float genelde daha az yer kaplar ama hassasiyeti düşüktür. Double, finans ve bilimsel hesaplamalarda tercih edilir.

int i = 1000;
long l = 1_000_000_000_000L;
float f = 3.14f;
double d = 3.141592653589793;

- Proje Pratiği:
Performans ve hafıza kısıtlaması varsa uygun tip seçilmeli. Özellikle finans ve bilimsel hesaplamalarda double ve BigDecimal tercih edilmeli.

## 2. Primitif veri tipleri ile wrapper sınıflar arasındaki farklar nelerdir?
- Cevap:
Primitif tipler (int, long vb.) doğrudan değer tutar ve hafızada daha az yer kaplar. Wrapper sınıflar (Integer, Long vb.) ise nesne (object) olarak sarılmış primitiflerdir.

- Detaylı Açıklama:
Wrapper sınıflar, koleksiyonlarda ve generic yapılarla kullanılabilir çünkü Java sadece referans tipleri kabul eder. Ayrıca wrapper sınıflar, null değeri alabilir, primitifler alamaz. Wrapper sınıflarda metotlar ve sabitler (örneğin Integer.MAX_VALUE) bulunur.

int primitive = 5;
Integer wrapper = Integer.valueOf(5); // veya Integer wrapper = 5; // autoboxing
- Proje Pratiği:
Koleksiyon kullanımı, veri tabanı işlemleri ve reflection gibi durumlarda wrapper kullanılır. Performans kritik alanlarda primitif tipler tercih edilir.

## 3. char veri tipi ve Unicode nedir?
- Cevap:
char 16 bitlik bir primitif veri tipi olup tek bir Unicode karakterini tutar. Unicode, dünya dillerindeki tüm karakterleri temsil eden evrensel bir karakter kodlama standardıdır.

- Detaylı Açıklama:
Java char UTF-16 kodlama kullanır ve 0 ile 65535 arasındaki karakterleri tutar. Ancak Unicode'un tamamı 1 char ile temsil edilmez, bazı karakterler (örneğin emoji) iki char (surrogate pair) gerektirir.

char letter = 'A';
char unicodeChar = '\u0041'; // Unicode escape sequence
- Proje Pratiği:
Metin işleme ve uluslararasılaştırma projelerinde Unicode bilgisi kritiktir. String manipülasyonlarında surrogate pair ve kod noktaları dikkatle yönetilmelidir.

## 4. null ve Optional arasındaki farklar nelerdir?
- Cevap:
null referansın hiçbir nesneye işaret etmediğini belirtir. Optional ise null değerler için daha güvenli bir sarmalayıcıdır, olası null değerlerin daha kontrollü yönetilmesini sağlar.

- Detaylı Açıklama:
null kullanımı NullPointerException (NPE) riskini artırır. Optional, bu riski azaltmak için null olabilecek değerleri açıkça belirtir ve metodlarla (isPresent(), orElse(), ifPresent()) kontrollü erişim sağlar.

Optional<String> optionalName = Optional.ofNullable(null);
optionalName.ifPresent(name -> System.out.println(name));
- Proje Pratiği:
API tasarımında null dönüşlerinden kaçınmak için Optional tercih edilir. Ancak performans gerektiren kritik kodlarda aşırı kullanımı önerilmez.

## 5. String ve StringBuilder farkları nelerdir?
- Cevap:
String nesneleri immutable (değiştirilemez) iken, StringBuilder mutable (değiştirilebilir) string yapısıdır.

- Detaylı Açıklama:
String üzerinde yapılan her değişiklik yeni bir nesne oluşturur, bu nedenle performans maliyeti vardır. StringBuilder ise aynı nesne üzerinde değişiklik yapar, büyük metin işleme ve döngülerde daha performanslıdır.
  
String s = "Hello";
s = s + " World"; // Yeni String oluşur

StringBuilder sb = new StringBuilder("Hello");
sb.append(" World"); // Aynı nesne üzerinde değişiklik
- Proje Pratiği:
Performansın kritik olduğu durumlarda özellikle döngü içinde string manipülasyonlarında StringBuilder veya StringBuffer (thread-safe) tercih edilmelidir.

## 6. float ve double hassasiyet farkları nelerdir?
- Cevap:
float yaklaşık 7 basamak hassasiyete, double yaklaşık 15-16 basamak hassasiyete sahiptir.

- Detaylı Açıklama:
Double, daha yüksek doğruluk ve aralık sunar. Bu nedenle finans, bilimsel hesaplamalar ve hassas ölçümlerde double tercih edilir. Float, hafıza ve performans açısından avantaj sağlar fakat daha az hassastır.

  
float f = 0.1234567f;  // 7 basamak hassasiyet
double d = 0.1234567890123456; // 15-16 basamak
- Proje Pratiği:
Para işlemlerinde kesinlik gerektiğinde BigDecimal tercih edilmelidir. float/double sayısal hata toleransları iyi anlaşılmalı.

## 7. instanceof operatörü nasıl çalışır?
- Cevap:
instanceof operatörü, bir nesnenin belirli bir sınıfın ya da onun alt sınıfının örneği olup olmadığını kontrol eder.

- Detaylı Açıklama:
null referanslar için instanceof false döner. Sınıf hiyerarşisi içinde tür güvenliği sağlar. Java 14+ ile pattern matching özelliğiyle kullanımı kolaylaşmıştır.
  
<!-- if (obj instanceof String) {
    String s = (String) obj;
    System.out.println(s.length());
}
Java 16+ örneği:

  
if (obj instanceof String s) {
    System.out.println(s.length());
} -->
- Proje Pratiği:
Type checking gerekliyse ve polymorphism yeterli değilse kullanılır. Modern Java sürümlerinde pattern matching ile okunabilirlik artırılır.

## 8. BigInteger ve BigDecimal farkları nelerdir?
- Cevap:

BigInteger: Sınırsız büyüklükte tam sayıları temsil eder.

BigDecimal: Kesin ondalık sayılar için kullanılır, özellikle finansal uygulamalarda hassas para hesapları için uygundur.

- Detaylı Açıklama:
Primitive ve wrapper tiplerin sınırlarını aşan sayısal işlemler için kullanılır. BigDecimal, kayan noktalı sayılar yerine kesin ondalık hesaplama sağlar ve yuvarlama modları sunar.

<!-- BigInteger bigInt = new BigInteger("12345678901234567890");
BigDecimal bigDec = new BigDecimal("12345.6789"); -->
- Proje Pratiği:
Finans, kriptografi ve bilimsel hesaplamalarda kesinlik ve büyük sayı gereksinimi varsa tercih edilir.

## 9. int ve Integer farkı nedir?
- Cevap:
int primitif veri tipidir, bellekte doğrudan değer tutar; Integer ise int’in nesne (wrapper) halidir.

- Detaylı Açıklama:
Integer nesne olduğu için null olabilir ve koleksiyonlarda kullanılabilir. int null alamaz ve daha performanslıdır. Autoboxing/unboxing ile dönüşümleri kolaylaştırılmıştır.

<!-- int prim = 10;
Integer wrap = 10; // autoboxing -->

- Proje Pratiği:
Koleksiyonlarda Integer kullanılır. Performans kritik alanlarda int tercih edilir.