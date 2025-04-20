# 🧠 Exception Handling dalam Java

**Exception Handling** adalah mekanisme dalam Java yang memungkinkan kita untuk menangani kesalahan (error) yang mungkin terjadi selama eksekusi program, tanpa menghentikan program secara keseluruhan. Dengan Exception Handling, kita dapat menangani berbagai jenis kesalahan, seperti kesalahan pada input pengguna, kesalahan dalam operasi I/O, atau kesalahan lainnya yang terjadi selama runtime.

Java menyediakan model **try-catch** yang memungkinkan kita untuk menangkap dan menangani kesalahan yang terjadi dalam program.

---

## 📌 Apa Itu Exception?

**Exception** adalah objek yang menggambarkan suatu kondisi yang tidak normal dalam program yang menyebabkan eksekusi program terganggu. Ketika suatu exception terjadi, alur eksekusi program akan berhenti dan eksekusi akan dilanjutkan ke blok `catch` yang sesuai (jika ada).

---

## 📌 Jenis-Jenis Exception

Di Java, exception dibagi menjadi dua kategori utama:

1. **Checked Exceptions**: Exception yang harus ditangani atau dideklarasikan dalam kode. Biasanya terkait dengan masalah eksternal seperti kesalahan input atau kesalahan dalam operasi I/O. Misalnya, `IOException`, `SQLException`.
2. **Unchecked Exceptions**: Exception yang tidak wajib ditangani atau dideklarasikan dalam kode. Biasanya terkait dengan kesalahan logika program yang dapat terjadi kapan saja, seperti `NullPointerException`, `ArrayIndexOutOfBoundsException`, dll.

---

## 📌 Struktur Dasar Exception Handling

Struktur dasar untuk menangani exception di Java menggunakan **blok try-catch** adalah sebagai berikut:

```java
try {
    // Kode yang mungkin menyebabkan exception
} catch (ExceptionType1 e1) {
    // Menangani ExceptionType1
} catch (ExceptionType2 e2) {
    // Menangani ExceptionType2
} finally {
    // Kode yang selalu dieksekusi, baik exception terjadi atau tidak
}
```

### Penjelasan:
- **try**: Blok kode yang mungkin menghasilkan exception.
- **catch**: Blok kode yang menangani exception yang terjadi di blok `try`.
- **finally**: Blok kode yang selalu dieksekusi setelah `try-catch`, terlepas dari apakah exception terjadi atau tidak.

---

## 📌 Contoh Penggunaan Exception Handling

### Contoh Kode 1: Menangani ArithmeticException

```java
public class Main {
    public static void main(String[] args) {
        try {
            int result = 10 / 0;  // Akan menyebabkan ArithmeticException
        } catch (ArithmeticException e) {
            System.out.println("Terjadi kesalahan: " + e.getMessage());
        }
    }
}
```

### Penjelasan:
- Pada contoh di atas, terjadi pembagian dengan angka nol, yang menghasilkan `ArithmeticException`.
- Exception ini ditangani oleh blok `catch`, dan pesan kesalahan ditampilkan.

---

## 📌 Multiple Catch Blocks

Kita bisa menangani beberapa jenis exception menggunakan beberapa blok `catch`. Java memungkinkan kita untuk menangani berbagai jenis exception dalam satu blok `try-catch`.

### Contoh Kode 2: Menangani Multiple Exceptions

```java
public class Main {
    public static void main(String[] args) {
        try {
            String text = null;
            System.out.println(text.length());  // NullPointerException

            int[] numbers = new int[5];
            numbers[10] = 100;  // ArrayIndexOutOfBoundsException
        } catch (NullPointerException e) {
            System.out.println("Terjadi NullPointerException: " + e.getMessage());
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Terjadi ArrayIndexOutOfBoundsException: " + e.getMessage());
        }
    }
}
```

### Penjelasan:
- Pada contoh ini, dua exception yang berbeda (`NullPointerException` dan `ArrayIndexOutOfBoundsException`) ditangani dalam blok `catch` yang berbeda.

---

## 📌 Blok `finally`

Blok `finally` digunakan untuk mengeksekusi kode yang harus dijalankan terlepas dari apakah exception terjadi atau tidak. Blok `finally` biasanya digunakan untuk menutup sumber daya seperti file atau koneksi jaringan yang telah dibuka.

### Contoh Kode 3: Penggunaan `finally`

```java
public class Main {
    public static void main(String[] args) {
        try {
            System.out.println("Kode di dalam try block.");
            int result = 10 / 0;  // ArithmeticException
        } catch (ArithmeticException e) {
            System.out.println("Terjadi ArithmeticException.");
        } finally {
            System.out.println("Kode di dalam finally block.");
        }
    }
}
```

### Penjelasan:
- Walaupun terjadi exception di dalam blok `try`, kode di dalam blok `finally` tetap dijalankan.

---

## 📌 Throw dan Throws

1. **throw**: Digunakan untuk secara eksplisit melemparkan exception dalam kode.
2. **throws**: Digunakan dalam deklarasi metode untuk memberitahukan bahwa metode tersebut mungkin melemparkan exception tertentu.

### Contoh Kode 4: Penggunaan `throw`

```java
public class Main {
    public static void main(String[] args) {
        try {
            checkAge(15);  // Melempar exception karena usia kurang dari 18
        } catch (IllegalArgumentException e) {
            System.out.println(e.getMessage());
        }
    }

    public static void checkAge(int age) {
        if (age < 18) {
            throw new IllegalArgumentException("Usia harus lebih dari 18 tahun.");
        }
    }
}
```

### Penjelasan:
- Di dalam metode `checkAge()`, jika usia kurang dari 18, kita melemparkan `IllegalArgumentException` menggunakan `throw`.

---

### Contoh Kode 5: Penggunaan `throws`

```java
public class Main {
    public static void main(String[] args) {
        try {
            bacaFile("file.txt");
        } catch (IOException e) {
            System.out.println("Terjadi kesalahan saat membaca file: " + e.getMessage());
        }
    }

    public static void bacaFile(String fileName) throws IOException {
        // Menyebabkan exception jika file tidak ditemukan
        throw new IOException("File " + fileName + " tidak ditemukan.");
    }
}
```

### Penjelasan:
- Dalam metode `bacaFile()`, kita menggunakan `throws` untuk mendeklarasikan bahwa metode ini bisa melemparkan `IOException`.
- Jika file tidak ditemukan, exception akan dilempar dan ditangani di dalam blok `catch` pada metode `main()`.

---

## 📌 Menangani Exception Kustom

Terkadang, kita perlu membuat exception kita sendiri untuk menangani situasi tertentu dalam program.

### Contoh Kode 6: Membuat Exception Kustom

```java
class UsiaException extends Exception {
    public UsiaException(String message) {
        super(message);
    }
}

public class Main {
    public static void main(String[] args) {
        try {
            validasiUsia(15);  // Melempar exception karena usia kurang dari 18
        } catch (UsiaException e) {
            System.out.println(e.getMessage());
        }
    }

    public static void validasiUsia(int usia) throws UsiaException {
        if (usia < 18) {
            throw new UsiaException("Usia harus lebih dari 18 tahun.");
        }
    }
}
```

### Penjelasan:
- Kita mendefinisikan exception kustom `UsiaException`, yang akan dilempar jika usia yang diberikan kurang dari 18.

---

## 🎯 Kesimpulan

- **Exception Handling** adalah mekanisme untuk menangani kesalahan (exception) yang terjadi dalam program tanpa menghentikan program secara keseluruhan.
- Java menyediakan beberapa cara untuk menangani exception, seperti blok `try-catch`, `finally`, dan penggunaan `throw` dan `throws`.
- Kita dapat menangani **checked exceptions** dengan mendeklarasikan `throws` atau menangani exception tersebut dengan blok `catch`.
- **Unchecked exceptions** lebih terkait dengan kesalahan logika dan dapat terjadi kapan saja selama eksekusi program.
- Membuat dan menggunakan **exception kustom** memungkinkan kita untuk menangani situasi tertentu dalam program dengan cara yang lebih spesifik.

---

> 🚀 Next: [08 - Koleksi dalam Java](08-koleksi-dalam-java.md)