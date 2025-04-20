# 14. Java Stream API

## Apa Itu Java Stream API?

Java Stream API adalah fitur yang diperkenalkan pada Java 8 yang memungkinkan pemrogram untuk memproses koleksi data (seperti `List`, `Set`, `Map`, dsb.) secara deklaratif. Stream API menyediakan cara yang lebih fungsional dan elegan untuk melakukan operasi pada data, seperti pengurutan, filter, dan pemrosesan paralel.

Stream API memungkinkan Anda untuk memproses data secara berurutan (sequential) atau paralel (parallel) tanpa perlu khawatir tentang manajemen thread atau mekanisme pemrosesan rendah.

## Dasar-Dasar Stream

### Apa itu Stream?

Stream adalah urutan elemen yang dapat diproses secara berurutan atau paralel. Perlu dicatat bahwa Stream bukanlah struktur data yang menyimpan elemen, melainkan representasi dari urutan elemen yang ada di dalam koleksi atau array.

### Membuat Stream

Stream dapat dibuat dari berbagai sumber, seperti koleksi (`List`, `Set`), array, atau bahkan dari input pengguna.

1. **Membuat Stream dari Koleksi**

```java
import java.util.List;
import java.util.stream.Stream;

public class Main {
    public static void main(String[] args) {
        List<String> list = List.of("Java", "Kotlin", "Python", "JavaScript");
        Stream<String> stream = list.stream();
        
        stream.forEach(System.out::println);  // Mencetak setiap elemen
    }
}
```

2. **Membuat Stream dari Array**

```java
import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        String[] array = {"Java", "Kotlin", "Python", "JavaScript"};
        Arrays.stream(array).forEach(System.out::println);
    }
}
```

### Operasi pada Stream

Stream API menyediakan dua jenis operasi:
1. **Operasi Intermediate**: Operasi ini mengubah Stream menjadi Stream lain, dan bersifat lazy (hanya dijalankan ketika diperlukan).
2. **Operasi Terminal**: Operasi ini menghasilkan hasil atau efek samping dan mengakhiri aliran data.

### 1. Operasi Intermediate

Operasi intermediate tidak menghasilkan hasil langsung, tetapi mengubah Stream menjadi Stream baru.

- **filter()**: Menyaring elemen-elemen yang tidak memenuhi kondisi.
- **map()**: Mengubah elemen menjadi bentuk lain (misalnya, mengubah elemen menjadi objek lain).
- **sorted()**: Mengurutkan elemen-elemen dalam Stream.

#### Contoh Penggunaan `filter()` dan `map()`

```java
import java.util.List;
import java.util.stream.Collectors;

public class Main {
    public static void main(String[] args) {
        List<String> list = List.of("Java", "Kotlin", "Python", "JavaScript");

        // Menyaring nama yang panjangnya lebih dari 4 karakter dan mengubahnya menjadi huruf kapital
        List<String> result = list.stream()
                                  .filter(s -> s.length() > 4)  // Filter berdasarkan panjang
                                  .map(String::toUpperCase)      // Ubah menjadi huruf kapital
                                  .collect(Collectors.toList()); // Mengumpulkan hasil ke dalam List

        System.out.println(result);
    }
}
```

Hasil dari kode di atas adalah:
```
[KOTLIN, JAVASCRIPT]
```

### 2. Operasi Terminal

Operasi terminal menghasilkan nilai atau efek samping dan mengakhiri Stream.

- **forEach()**: Menjalankan aksi pada setiap elemen Stream.
- **collect()**: Mengumpulkan elemen Stream ke dalam koleksi seperti `List`, `Set`, atau `Map`.
- **reduce()**: Menggabungkan elemen-elemen dalam Stream menjadi satu hasil.

#### Contoh Penggunaan `forEach()` dan `collect()`

```java
import java.util.List;
import java.util.stream.Collectors;

public class Main {
    public static void main(String[] args) {
        List<String> list = List.of("Java", "Kotlin", "Python", "JavaScript");

        // Menggunakan forEach untuk mencetak setiap elemen
        list.stream().forEach(System.out::println);

        // Menggunakan collect untuk mengubah Stream menjadi List
        List<String> collectedList = list.stream().collect(Collectors.toList());
        System.out.println(collectedList);
    }
}
```

Hasil dari kode di atas adalah:
```
Java
Kotlin
Python
JavaScript
[Java, Kotlin, Python, JavaScript]
```

### 3. Operasi Reduksi dengan `reduce()`

`reduce()` digunakan untuk menggabungkan elemen-elemen dalam Stream menjadi satu nilai, seperti menjumlahkan angka atau menggabungkan string.

```java
import java.util.List;
import java.util.Optional;

public class Main {
    public static void main(String[] args) {
        List<Integer> numbers = List.of(1, 2, 3, 4, 5);

        // Menjumlahkan semua elemen
        Optional<Integer> sum = numbers.stream().reduce((a, b) -> a + b);

        sum.ifPresent(System.out::println);  // Output: 15
    }
}
```

### 4. Pemrosesan Paralel

Stream API memungkinkan Anda untuk memproses data secara paralel, yang berguna untuk aplikasi yang memerlukan pemrosesan data besar atau waktu eksekusi cepat.

```java
import java.util.List;
import java.util.stream.Collectors;

public class Main {
    public static void main(String[] args) {
        List<String> list = List.of("Java", "Kotlin", "Python", "JavaScript");

        // Memproses Stream secara paralel
        List<String> result = list.parallelStream()
                                  .filter(s -> s.length() > 4)
                                  .collect(Collectors.toList());

        System.out.println(result);
    }
}
```

Dengan menggunakan `parallelStream()`, operasi akan diproses secara paralel oleh beberapa thread, yang bisa meningkatkan performa pada data yang sangat besar.

## Kesimpulan

Java Stream API adalah alat yang sangat kuat untuk memproses koleksi data dengan cara deklaratif dan fungsional. Dengan menggunakan Stream, kita dapat menulis kode yang lebih bersih, lebih mudah dipahami, dan lebih efisien. Fitur-fitur seperti pemrosesan paralel, operasi lazy, dan transformasi data membuat Stream API sangat berguna dalam pengolahan data di Java.

Beberapa operasi dasar yang perlu Anda kuasai adalah `filter()`, `map()`, `collect()`, dan `reduce()`, serta kemampuan untuk memproses data secara paralel dengan `parallelStream()`. 