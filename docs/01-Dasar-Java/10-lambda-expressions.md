# 10. Lambda Expressions di Java

## Apa Itu Lambda Expressions?

Lambda expressions adalah fitur yang diperkenalkan di Java 8 yang memungkinkan kita untuk menulis fungsi anonim (tanpa nama) yang bisa digunakan untuk membuat kode lebih ringkas dan mudah dibaca. Lambda expressions sangat berguna untuk menggantikan implementasi interface dengan satu metode (seperti `Runnable`, `Comparator`, dan sebagainya).

Lambda expressions memungkinkan kita untuk menulis kode dalam gaya deklaratif dan menghindari boilerplate code, khususnya ketika kita bekerja dengan koleksi data atau melakukan operasi berbasis callback.

### Sintaks Lambda Expression

Sintaks dasar dari lambda expression adalah sebagai berikut:

```java
(parameter) -> expression
```

- **parameter**: Parameter untuk lambda expression. Bisa lebih dari satu atau bahkan tidak ada sama sekali.
- **->**: Operator yang memisahkan parameter dengan body dari lambda expression.
- **expression**: Kode yang dijalankan oleh lambda expression.

### Contoh Dasar Lambda Expression

Berikut adalah contoh lambda expression yang sederhana:

```java
public class Main {
    public static void main(String[] args) {
        // Lambda expression untuk mencetak pesan
        Runnable runnable = () -> System.out.println("Hello, World!");
        runnable.run(); // Output: Hello, World!
    }
}
```

Dalam contoh ini, `Runnable` adalah interface dengan satu metode `run()`. Dengan lambda expression, kita dapat mengimplementasikan `run()` secara langsung tanpa perlu membuat kelas anonim atau implementasi terpisah.

## Penggunaan Lambda Expression dengan Koleksi

Lambda expression sangat berguna saat bekerja dengan koleksi data, seperti saat menggunakan stream API.

### Contoh: Menggunakan `forEach` untuk Iterasi

```java
import java.util.Arrays;
import java.util.List;

public class Main {
    public static void main(String[] args) {
        List<String> fruits = Arrays.asList("Apple", "Banana", "Orange");

        // Menggunakan lambda expression dengan forEach
        fruits.forEach(fruit -> System.out.println(fruit));
    }
}
```

Output:
```
Apple
Banana
Orange
```

Lambda expression di atas menggantikan cara tradisional menggunakan loop untuk iterasi melalui koleksi.

### Contoh: Menggunakan `filter` dan `map` dengan Stream API

Lambda expressions juga sering digunakan dengan Stream API untuk manipulasi data yang lebih kompleks.

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class Main {
    public static void main(String[] args) {
        List<String> fruits = Arrays.asList("Apple", "Banana", "Orange", "Pineapple");

        // Menggunakan lambda expression untuk filter dan map
        List<String> longFruits = fruits.stream()
                                        .filter(fruit -> fruit.length() > 5)
                                        .collect(Collectors.toList());

        System.out.println(longFruits); // Output: [Banana, Orange, Pineapple]
    }
}
```

Dalam contoh ini:
- `filter()` digunakan untuk memilih elemen dengan panjang lebih dari 5 karakter.
- `collect()` digunakan untuk mengumpulkan hasil stream menjadi sebuah list.

## Keuntungan Menggunakan Lambda Expressions

1. **Kode Lebih Ringkas dan Bersih**  
   Lambda expression mengurangi kode boilerplate yang perlu ditulis, menjadikan kode lebih ringkas dan mudah dibaca.
   
2. **Memungkinkan Pemrograman Fungsional**  
   Java 8 memungkinkan pendekatan pemrograman fungsional, di mana fungsi dapat diperlakukan sebagai objek dan dapat diteruskan sebagai parameter.

3. **Dukungan untuk Parallel Processing**  
   Dengan menggunakan stream API bersama lambda, kita bisa lebih mudah melakukan operasi paralel yang memanfaatkan banyak inti prosesor.

## Fungsi dan Method References

Selain lambda expression, Java juga menyediakan fitur lain yang sering digunakan bersamaan, yaitu **method references**. Method references adalah cara singkat untuk menulis lambda expression yang memanggil metode yang sudah ada.

Contoh:

```java
import java.util.Arrays;
import java.util.List;

public class Main {
    public static void main(String[] args) {
        List<String> fruits = Arrays.asList("Apple", "Banana", "Orange");

        // Menggunakan method reference
        fruits.forEach(System.out::println);
    }
}
```

Method reference di atas menggantikan lambda expression `fruit -> System.out.println(fruit)` dengan `System.out::println`.

### Jenis-jenis Method References
1. **Reference to a static method**:
   ```java
   ClassName::staticMethod
   ```
2. **Reference to an instance method of a particular object**:
   ```java
   instance::instanceMethod
   ```
3. **Reference to an instance method of an arbitrary object**:
   ```java
   ClassName::instanceMethod
   ```

## Kesimpulan

Lambda expressions adalah fitur yang sangat powerful di Java yang memungkinkan kita menulis kode lebih ringkas dan fleksibel. Dengan menggunakan lambda, kita bisa lebih mudah berinteraksi dengan koleksi data, memanfaatkan stream API, dan menulis kode yang lebih bersih dan terstruktur dengan baik.

Selalu ingat bahwa lambda expressions bukanlah pengganti mutlak untuk semua kasus. Mereka paling efektif ketika digunakan dalam konteks fungsional atau saat bekerja dengan API berbasis callback.
