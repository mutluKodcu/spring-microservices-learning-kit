# Advanced Java Features

## 1. Java Streams API nasıl çalışır ve ne zaman kullanılır?
- Cevap:
Streams API, Java 8 ile gelen ve koleksiyon verilerini fonksiyonel tarzda işlemek için kullanılan bir yapıdır. Veriyi filtreleme, dönüştürme, toplama gibi işlemleri zincirleme ve paralel olarak yapılmasını sağlar.

- Detaylı Açıklama:
Stream, veriyi değiştirmez; ara işlemler (filter, map) lazy olarak değerlendirilir, terminal işlem (collect, forEach) çalıştırıldığında işlemler zincirlenir. Paralel stream kullanarak otomatik çoklu çekirdek işleme yapılabilir.
 
<!-- List<String> names = List.of("Ali", "Veli", "Ayşe", "Fatma");
List<String> filtered = names.stream()
    .filter(name -> name.startsWith("A"))
    .map(String::toUpperCase)
    .collect(Collectors.toList());
System.out.println(filtered); // [ALI, AYŞE] -->
- Proje Pratiği:
Veri işleme, raporlama, filtreleme işlemlerinde okunabilir ve performanslı kod için Stream API önerilir.

## 2. Reflection API nedir ve nasıl kullanılır?
- Cevap:
Reflection API, çalışma zamanında (runtime) sınıfların, metodların, alanların dinamik olarak incelenmesini ve değiştirilmesini sağlar.

- Detaylı Açıklama:
Reflection ile private metodlara erişmek, dinamik nesne oluşturmak, annotation okumak mümkün. Ancak performans ve güvenlik açısından dikkatle kullanılmalı.
 
``` Class<?> clazz = Class.forName("com.example.Person");
Method method = clazz.getDeclaredMethod("getName");
method.setAccessible(true);
Object result = method.invoke(clazz.getConstructor().newInstance());
System.out.println(result);
```
- Proje Pratiği:
Framework ve kütüphanelerde (Spring, Hibernate) sık kullanılır. Uygulama kodunda ise zorunlu olmadıkça tercih edilmez.

## 3. Lambda ifadeleri nedir? Avantajları nelerdir?
- Cevap:
Lambda ifadeleri, fonksiyonel programlamaya izin veren, kısa ve anonim fonksiyon tanımlama yoludur. Java 8 ile geldi.

- Detaylı Açıklama:
Kodun okunabilirliğini artırır, anonim sınıflara göre daha az kod yazılır. Fonksiyonları parametre olarak verebilmek mümkün olur. Paralel ve fonksiyonel yapıların temelidir.
 
``` List<String> list = List.of("a", "b", "c");
list.forEach(s -> System.out.println(s.toUpperCase()));
```
- Proje Pratiği:
Koleksiyon işlemlerinde, event callbacklerinde ve Stream API ile beraber yaygın kullanılır.

## 4. Java 8 default metodlar nedir?
- Cevap:
Interface’lerde gövdeli metodlar (default methods) Java 8 ile geldi. Interface’e yeni metod eklerken, bu metodun implementasyonunu default olarak verebilirsiniz.

- Detaylı Açıklama:
Default metodlar geriye dönük uyumluluk sağlar, interface genişletilebilir. Ayrıca interface içinde ortak fonksiyonellik sağlamak için kullanılır.
 
``` interface MyInterface {
    default void defaultMethod() {
        System.out.println("Default method çalıştı");
    }
} 
```
- Proje Pratiği:
API’lerde ve framework geliştirmede interface değişikliklerini kolaylaştırmak için kullanılır.

## 5. Optional sınıfı neden tercih edilir?
- Cevap:
Optional, null değerler yerine kullanılabilen, null kontrolünü zorunlu hale getiren bir kapsayıcıdır.

- Detaylı Açıklama:
NullPointerException riskini azaltır, kod okunabilirliğini artırır. Değerin varlığı veya yokluğu açıkça belirtilir.
 
Optional<String> optional = Optional.ofNullable(getValue());
optional.ifPresent(System.out::println);
- Proje Pratiği:
API tasarımında null dönüşümleri azaltmak, hataları erken yakalamak için tercih edilir.

## 6. Java’da Checked ve Unchecked Exception farkları nelerdir?
- Cevap:
Checked Exceptionlar derleme zamanında handle edilmek zorundadır, Unchecked Exceptionlar ise runtime’da oluşan ve handle etmek zorunlu olmayan exceptionlardır.

- Detaylı Açıklama:
Checked: IOException, SQLException gibi. Method signature’da throws ile belirtilir.
Unchecked: RuntimeException ve alt sınıfları. Genellikle program hatası.

- Proje Pratiği:
Checked exceptionlar dış kaynaklı hatalar için, unchecked exceptionlar ise program hatası ve kontrol dışı durumlar için kullanılır.

## 7. try-catch blokları ve throws kullanımı nedir?
- Cevap:
try-catch blokları hata yönetimi için kullanılır; try içinde kod yazılır, catch hatayı yakalar. throws ise metodun exception fırlatacağını belirtir.

- Detaylı Açıklama:
throws method signature’da exception bildirir, çağıran methodda handle edilmelidir. try-catch ise doğrudan hatayı yakalar ve yönetir.
 
``` public void readFile() throws IOException {
    // throws bildirimi
    try (BufferedReader br = new BufferedReader(new FileReader("file.txt"))) {
        System.out.println(br.readLine());
    } catch (IOException e) {
        e.printStackTrace();
    }
} 
```
- Proje Pratiği:
Hata yönetimi temiz ve kontrollü olmalı, gereksiz catch blokları kod karmaşasına neden olur.

## 8. Custom Exception nasıl oluşturulur ve ne zaman kullanılır?
- Cevap:
Özel iş kurallarına veya uygulama spesifik hatalara uygun exceptionlar yaratılır.

- Detaylı Açıklama:
Exception veya RuntimeException sınıflarından extend edilir. Anlamlı mesaj ve ek alanlar eklenebilir.
 
```
public class InvalidUserException extends Exception {
    public InvalidUserException(String message) {
        super(message);
    }
} 
```
- Proje Pratiği:
Domain hataları, iş kuralı ihlalleri için custom exception kullanmak kodun anlaşılabilirliğini artırır.

## 9. InputStream, OutputStream, Reader, Writer farkı nedir?
- Cevap:
InputStream/OutputStream bayt (byte) bazlı, Reader/Writer karakter (char) bazlı veri okuma/yazma akışlarıdır.

- Detaylı Açıklama:

InputStream/OutputStream dosya, network gibi kaynaklardan ham byte okuma/yazma için.

Reader/Writer ise metin verileri için karakter bazında optimize edilmiş.

- Proje Pratiği:
Metin dosyaları için Reader/Writer tercih edilir, binary dosyalar için InputStream/OutputStream.

## 10. Dosya işlemlerinde File, Path ve Files nasıl kullanılır?
- Cevap:
File (Java 7 öncesi), Path (Java 7+), Files (yardımcı statik metodlar) sınıfları dosya ve dizin işlemlerinde kullanılır.

- Detaylı Açıklama:

File: Eski API, dosya/dizin varlığı kontrol, oluşturma.

Path: Daha modern, daha fazla özellik ve platform bağımsızlığı.

Files: Dosya kopyalama, okuma, yazma gibi statik yardımcı metotlar içerir.
```
Path path = Paths.get("example.txt");
if (!Files.exists(path)) {
    Files.createFile(path);
}
String content = "Merhaba Dünya";
Files.writeString(path, content); 
```

- Proje Pratiği:
Java 7 sonrası Path ve Files tercih edilir; daha güvenli ve esnek API sunar.


