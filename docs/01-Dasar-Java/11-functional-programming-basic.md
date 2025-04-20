# 11. Dasar-Dasar Pemrograman Fungsional di Java

## Apa Itu Pemrograman Fungsional?

Pemrograman fungsional adalah paradigma pemrograman yang berfokus pada penggunaan fungsi-fungsi untuk memproses data dan menghindari penggunaan data mutable dan state. Di Java, pemrograman fungsional diperkenalkan mulai dari Java 8, melalui fitur-fitur seperti lambda expressions, stream API, dan method references.

Pemrograman fungsional memungkinkan kita untuk menulis kode yang lebih deklaratif, modular, dan dapat diprediksi. Ini sangat bermanfaat untuk bekerja dengan koleksi data dan operasi paralel.

### Ciri-ciri Pemrograman Fungsional

- **Fungsi sebagai Objek Pertama**: Fungsi dapat diperlakukan sebagai parameter, nilai, dan hasil dari operasi lain.
- **Immutabilitas**: Data tidak dapat diubah setelah dibuat, sehingga mengurangi kemungkinan terjadinya bug karena perubahan data yang tidak terduga.
- **Tidak ada Side Effects**: Fungsi seharusnya tidak memodifikasi data di luar scope mereka.
- **Higher-Order Functions**: Fungsi dapat menerima fungsi lain sebagai parameter atau mengembalikan fungsi sebagai hasil.

## Java dan Pemrograman Fungsional

Sejak Java 8, berbagai fitur baru telah ditambahkan untuk mendukung pemrograman fungsional, termasuk:
1. **Lambda Expressions**: Fungsi anonim yang memungkinkan penulisan kode yang lebih ringkas.
2. **Stream API**: Digunakan untuk memproses koleksi data secara deklaratif dan memungkinkan pemrosesan paralel.
3. **Method References**: Sintaks yang lebih ringkas untuk merujuk ke metode yang ada.
4. **Optional**: Untuk menangani nilai yang mungkin null tanpa menyebabkan `NullPointerException`.

### Fungsi Sebagai First-Class Citizen

Dalam pemrograman fungsional, fungsi diperlakukan sebagai "first-class citizen", yang berarti kita dapat menggunakan fungsi seperti halnya variabel. Fungsi dapat diteruskan sebagai parameter ke fungsi lain, dan bisa mengembalikan fungsi lain.

#### Contoh Fungsi sebagai Parameter:

```java
import java.util.Arrays;
import java.util.List;
import java.util.function.Consumer;

public class Main {
    public static void main(String[] args) {
        List<String> fruits = Arrays.asList("Apple", "Banana", "Orange");

        // Fungsi print sebagai parameter
        fruits.forEach(printItem);
    }

    // Fungsi untuk mencetak item
    static Consumer<String> printItem = item -> System.out.println(item);
}
```

Pada contoh di atas, fungsi `printItem` digunakan sebagai parameter dalam method `forEach` yang memproses setiap item dalam koleksi.

### Higher-Order Functions

Higher-order functions adalah fungsi yang dapat menerima fungsi lain sebagai parameter atau mengembalikan fungsi.

#### Contoh Higher-Order Function:

```java
import java.util.function.Function;

public class Main {
    public static void main(String[] args) {
        // Menggunakan higher-order function
        Function<Integer, Integer> multiplyByTwo = x -> x * 2;

        // Meneruskan function sebagai parameter
        System.out.println(applyFunction(5, multiplyByTwo)); // Output: 10
    }

    // Fungsi yang menerima fungsi lain sebagai parameter
    public static int applyFunction(int value, Function<Integer, Integer> func) {
        return func.apply(value);
    }
}
```

Di sini, `applyFunction` menerima fungsi sebagai parameter dan menerapkannya pada nilai yang diberikan.

## Stream API

Stream API adalah fitur di Java 8 yang memungkinkan kita untuk memproses koleksi data dengan cara deklaratif. Dengan stream, kita bisa menggunakan operasi seperti `filter`, `map`, `reduce`, dan lainnya untuk memanipulasi data dalam koleksi.

### Operasi Dasar Stream API

#### 1. **filter()**: Menyaring elemen berdasarkan kondisi tertentu.
```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class Main {
    public static void main(String[] args) {
        List<String> fruits = Arrays.asList("Apple", "Banana", "Orange", "Pineapple");

        // Filter buah yang panjang namanya lebih dari 5 karakter
        List<String> filteredFruits = fruits.stream()
                                            .filter(fruit -> fruit.length() > 5)
                                            .collect(Collectors.toList());

        System.out.println(filteredFruits); // Output: [Banana, Orange, Pineapple]
    }
}
```

#### 2. **map()**: Mengubah elemen dalam stream ke bentuk lain.
```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class Main {
    public static void main(String[] args) {
        List<String> fruits = Arrays.asList("apple", "banana", "orange");

        // Mengubah semua elemen menjadi huruf kapital
        List<String> upperCaseFruits = fruits.stream()
                                             .map(String::toUpperCase)
                                             .collect(Collectors.toList());

        System.out.println(upperCaseFruits); // Output: [APPLE, BANANA, ORANGE]
    }
}
```

#### 3. **reduce()**: Menggabungkan elemen dalam stream menjadi satu nilai.
```java
import java.util.Arrays;
import java.util.List;

public class Main {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);

        // Menjumlahkan semua angka dalam list
        int sum = numbers.stream()
                         .reduce(0, (a, b) -> a + b);

        System.out.println(sum); // Output: 15
    }
}
```

### Pemrosesan Paralel dengan Stream

Stream API juga mendukung pemrosesan paralel yang memungkinkan kita memanfaatkan banyak core prosesor untuk mempercepat proses pemrosesan data.

```java
import java.util.Arrays;
import java.util.List;

public class Main {
    public static void main(String[] args) {
        List<String> fruits = Arrays.asList("Apple", "Banana", "Orange", "Pineapple");

        // Pemrosesan paralel menggunakan stream
        fruits.parallelStream()
              .forEach(System.out::println); // Output dapat berbeda urutannya karena paralel
    }
}
```

## Optional

`Optional` adalah kelas yang digunakan untuk menangani nilai yang mungkin null, yang dapat mencegah terjadinya `NullPointerException`.

### Contoh Penggunaan `Optional`:

```java
import java.util.Optional;

public class Main {
    public static void main(String[] args) {
        String name = "John";

        Optional<String> optionalName = Optional.ofNullable(name);

        // Mengambil nilai dari Optional jika ada, jika tidak ada akan mengembalikan nilai default
        System.out.println(optionalName.orElse("Anonymous")); // Output: John
    }
}
```

## Kesimpulan

Pemrograman fungsional memberikan banyak manfaat untuk penulisan kode yang lebih bersih, modular, dan deklaratif. Dengan fitur-fitur seperti lambda expressions, stream API, dan method references, kita bisa menulis kode Java dengan gaya fungsional yang lebih ringkas dan efisien. Memahami pemrograman fungsional sangat penting bagi setiap pengembang Java, terutama jika kita ingin memanfaatkan sepenuhnya potensi Java 8 dan versi-versi berikutnya.
