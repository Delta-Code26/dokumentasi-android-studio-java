# 🧠 Abstraction dalam OOP (Pemrograman Berorientasi Objek) di Java

Abstraction adalah konsep dasar dalam **Pemrograman Berorientasi Objek (OOP)** yang memungkinkan kita untuk menyembunyikan implementasi detail dan hanya menampilkan fitur yang penting. Tujuan utama dari abstraction adalah untuk menyederhanakan antarmuka pengguna (user interface) dan menyembunyikan kompleksitas implementasi dari pengguna.

Di dalam Java, abstraction dapat dicapai menggunakan dua konsep utama:
- **Abstract Class** (Kelas Abstrak)
- **Interface**

---

## 📌 Apa Itu Abstraction?

Abstraction adalah mekanisme untuk mendefinisikan suatu **kelas atau antarmuka** yang hanya berisi informasi dasar dan mengabstraksi implementasi detil dari metode atau proses yang ada. Abstraction mengizinkan kita untuk bekerja dengan **ide atau konsep umum** tanpa harus memahami implementasi mendalam setiap kali.

Contoh dunia nyata: Sebuah **mobil** adalah objek yang memiliki berbagai komponen (mesin, roda, dll.), namun kita tidak perlu mengetahui bagaimana setiap bagian berfungsi untuk dapat mengendarainya. Kita hanya cukup mengetahui bagaimana menghidupkan mesin dan mengendalikan mobil.

---

## 📌 Kelas Abstrak (Abstract Class)

Kelas abstrak adalah kelas yang tidak dapat diinstansiasi (tidak dapat dibuat objeknya) secara langsung. Sebuah kelas abstrak bisa memiliki metode yang **berisi implementasi** dan bisa juga memiliki metode yang **tidak terimplementasi** (hanya deklarasi). Metode yang tidak terimplementasi di dalam kelas abstrak disebut **metode abstrak**.

### Menyatakan Kelas Abstrak:

Untuk mendeklarasikan kelas abstrak di Java, kita menggunakan kata kunci `abstract`.

### Contoh Kelas Abstrak:

```java
abstract class Hewan {
    // Metode abstrak (tanpa implementasi)
    public abstract void suara();

    // Metode dengan implementasi
    public void tidur() {
        System.out.println("Hewan sedang tidur...");
    }
}

class Anjing extends Hewan {
    // Mengimplementasikan metode abstrak suara()
    @Override
    public void suara() {
        System.out.println("Anjing menggonggong");
    }
}

public class Main {
    public static void main(String[] args) {
        // Hewan hewan = new Hewan(); // Error: Tidak bisa menginstansiasi kelas abstrak

        // Membuat objek dari kelas Anjing
        Hewan anjing = new Anjing();
        anjing.suara(); // Output: Anjing menggonggong
        anjing.tidur(); // Output: Hewan sedang tidur...
    }
}
```

### Penjelasan:
- Kelas `Hewan` adalah kelas abstrak karena memiliki metode abstrak `suara()`.
- Kelas `Anjing` mengimplementasikan metode `suara()` dari kelas `Hewan`.
- Objek `Hewan` tidak bisa langsung dibuat, tetapi bisa dibuat objek dari kelas turunan seperti `Anjing`.

---

## 📌 Interface

Interface adalah sebuah kontrak atau perjanjian yang menyatakan bahwa kelas yang mengimplementasikan interface harus mendefinisikan semua metode yang ada di dalam interface tersebut. Berbeda dengan kelas abstrak, **interface hanya dapat mendeklarasikan metode, tanpa implementasi apapun**.

### Menyatakan Interface:

Interface dideklarasikan dengan kata kunci `interface`.

### Contoh Interface:

```java
interface Kendaraan {
    // Metode dalam interface hanya memiliki deklarasi (tanpa implementasi)
    void berjalan();
}

class Mobil implements Kendaraan {
    // Implementasi metode berjalan()
    public void berjalan() {
        System.out.println("Mobil berjalan di jalan raya");
    }
}

class Sepeda implements Kendaraan {
    // Implementasi metode berjalan()
    public void berjalan() {
        System.out.println("Sepeda berjalan di trotoar");
    }
}

public class Main {
    public static void main(String[] args) {
        Kendaraan mobil = new Mobil();
        mobil.berjalan(); // Output: Mobil berjalan di jalan raya

        Kendaraan sepeda = new Sepeda();
        sepeda.berjalan(); // Output: Sepeda berjalan di trotoar
    }
}
```

### Penjelasan:
- `Kendaraan` adalah interface yang mendeklarasikan metode `berjalan()`.
- `Mobil` dan `Sepeda` mengimplementasikan interface `Kendaraan` dan mendefinisikan implementasi metode `berjalan()`.
- Interface dapat diimplementasikan oleh banyak kelas, dan setiap kelas harus menyediakan implementasi untuk semua metode dalam interface.

---

## 📌 Perbedaan Antara Kelas Abstrak dan Interface

| Fitur                    | Kelas Abstrak (Abstract Class)         | Interface                          |
|--------------------------|----------------------------------------|------------------------------------|
| Metode dengan implementasi | Bisa ada (bisa memiliki kode)         | Tidak ada implementasi sama sekali |
| Implementasi Metode       | Kelas turunan harus mengimplementasikan metode abstrak | Semua metode harus diimplementasikan oleh kelas yang mengimplementasikan interface |
| Konstruktor              | Bisa ada                               | Tidak ada konstruktur              |
| Multiple Inheritance     | Tidak bisa menggunakan multiple inheritance (hanya satu kelas induk) | Dapat mengimplementasikan banyak interface |
| Penggunaan Kata Kunci    | `abstract`                            | `interface`                        |

---

## 📌 Kapan Menggunakan Abstraction?

1. **Abstraction dengan Kelas Abstrak**:
   - Digunakan jika ada beberapa kelas yang memiliki fitur umum (seperti metode dengan implementasi yang sama), dan kelas turunan perlu mengimplementasikan beberapa metode yang lebih spesifik.
   - Digunakan ketika Anda ingin membuat kelas dengan implementasi dasar yang dapat digunakan oleh subclass.

2. **Abstraction dengan Interface**:
   - Digunakan ketika Anda ingin mendefinisikan suatu kontrak yang harus diikuti oleh kelas yang mengimplementasikan interface tersebut.
   - Interface cocok digunakan ketika Anda membutuhkan **multiple inheritance** (yaitu, sebuah kelas bisa mengimplementasikan banyak interface).

---

## 📌 Latihan

1. **Buat kelas abstrak `Kendaraan`** yang memiliki metode abstrak `bergerak()`, dan kelas turunan `Mobil` dan `Sepeda` yang mengimplementasikan metode tersebut.
2. **Buat interface `Penghitung`** yang memiliki metode `hitungJumlah()`. Buat dua kelas yang mengimplementasikan interface ini, yaitu `Perpustakaan` yang menghitung jumlah buku dan `Toko` yang menghitung jumlah barang.
3. **Implementasikan konsep abstraction dalam sistem manajemen hewan** dengan kelas abstrak `Hewan` dan kelas turunan seperti `Kucing` dan `Burung`.

---

## 🎯 Kesimpulan

- **Abstraction** menyembunyikan implementasi yang kompleks dan hanya menunjukkan antarmuka yang sederhana kepada pengguna.
- **Kelas abstrak** bisa memiliki metode dengan implementasi, sedangkan **interface** hanya mendeklarasikan metode yang harus diimplementasikan oleh kelas yang menggunakannya.
- Abstraction membantu mengorganisir kode menjadi lebih bersih, fleksibel, dan mudah dipelihara.

---

> 🚀 Next: [07 - Polymorphism dalam Java](07-polymorphism-dalam-java.md)
```

---

Materi ini menjelaskan konsep **Abstraction** dalam Pemrograman Berorientasi Objek di Java, menggunakan **kelas abstrak** dan **interface**. Jika ada hal lain yang perlu disesuaikan atau ditambahkan, beri tahu saya!