# 🧠 Kelas dalam Java

Kelas (class) adalah salah satu konsep dasar dalam pemrograman berorientasi objek (OOP) di Java. Kelas adalah blueprint atau cetak biru untuk objek. Dalam sebuah kelas, kita mendefinisikan atribut (data) dan perilaku (metode) yang akan dimiliki oleh objek yang dibuat dari kelas tersebut.

---

## 📌 Apa Itu Kelas?

Kelas adalah template atau blueprint untuk membuat objek. Di dalam kelas, kita dapat mendefinisikan:
1. **Atribut**: Variabel yang menyimpan data atau informasi.
2. **Metode**: Fungsi atau prosedur yang mendefinisikan tindakan atau perilaku dari objek.

---

## 📌 Struktur Kelas

Struktur dasar sebuah kelas di Java terdiri dari beberapa elemen:
1. **Modifikator Akses**: Seperti `public`, `private`, atau `protected`, untuk menentukan tingkat akses ke kelas.
2. **Nama Kelas**: Nama yang digunakan untuk mendefinisikan kelas.
3. **Atribut**: Variabel yang digunakan untuk menyimpan data atau keadaan objek.
4. **Metode**: Fungsi yang mendefinisikan perilaku objek.
5. **Konstruktor**: Fungsi khusus yang digunakan untuk membuat objek dari kelas.

### Contoh Struktur Kelas:

```java
public class Mobil {
    // Atribut
    String warna;
    String merk;

    // Konstruktor
    public Mobil(String warna, String merk) {
        this.warna = warna;
        this.merk = merk;
    }

    // Metode
    public void tampilkanInfo() {
        System.out.println("Mobil warna: " + warna + " dan merk: " + merk);
    }
}
```

Penjelasan:
- `public class Mobil`: Menandakan bahwa kelas ini dapat diakses oleh kelas lain.
- `String warna, String merk`: Atribut dari kelas `Mobil`.
- Konstruktor `Mobil(String warna, String merk)` digunakan untuk menginisialisasi atribut saat objek dibuat.
- `tampilkanInfo()` adalah metode yang menampilkan informasi mobil.

---

## 📌 Membuat dan Menggunakan Objek

Untuk membuat objek dari kelas, kita perlu menggunakan kata kunci `new` dan memanggil konstruktor kelas tersebut. Setelah objek dibuat, kita dapat mengakses atribut dan metode objek tersebut.

### Contoh Membuat Objek:

```java
public class Main {
    public static void main(String[] args) {
        // Membuat objek mobil
        Mobil mobilSaya = new Mobil("Merah", "Toyota");

        // Mengakses metode objek
        mobilSaya.tampilkanInfo(); // Output: Mobil warna: Merah dan merk: Toyota
    }
}
```

Penjelasan:
- `Mobil mobilSaya = new Mobil("Merah", "Toyota");` membuat objek `mobilSaya` dari kelas `Mobil` dan menginisialisasi atribut `warna` dan `merk` dengan nilai yang diberikan.
- `mobilSaya.tampilkanInfo();` memanggil metode `tampilkanInfo()` untuk menampilkan informasi mobil.

---

## 📌 Konstruktor

Konstruktor adalah metode khusus yang digunakan untuk menginisialisasi objek baru. Konstruktor memiliki nama yang sama dengan kelas dan tidak memiliki tipe kembalian. Jika tidak ada konstruktor yang ditulis, Java akan menyediakan konstruktor default yang tidak melakukan apa-apa.

### Contoh Konstruktor:

```java
public class Buku {
    String judul;
    String penulis;

    // Konstruktor
    public Buku(String judul, String penulis) {
        this.judul = judul;
        this.penulis = penulis;
    }

    // Metode
    public void tampilkanInfo() {
        System.out.println("Judul: " + judul + ", Penulis: " + penulis);
    }
}
```

Pemanggilan konstruktor:
```java
Buku bukuSaya = new Buku("Belajar Java", "John Doe");
bukuSaya.tampilkanInfo(); // Output: Judul: Belajar Java, Penulis: John Doe
```

Penjelasan:
- Konstruktor digunakan untuk menginisialisasi objek `Buku` dengan `judul` dan `penulis`.

---

## 📌 Method dalam Kelas

Metode dalam kelas berfungsi untuk mendefinisikan perilaku objek. Metode bisa memiliki parameter dan nilai kembali, atau bisa juga tidak mengembalikan nilai (menggunakan `void`).

### Contoh Metode dalam Kelas:

```java
public class Perpustakaan {
    String namaPerpustakaan;

    // Konstruktor
    public Perpustakaan(String namaPerpustakaan) {
        this.namaPerpustakaan = namaPerpustakaan;
    }

    // Metode
    public void bukaPerpustakaan() {
        System.out.println("Perpustakaan " + namaPerpustakaan + " sedang dibuka.");
    }
}
```

Pemanggilan metode:
```java
Perpustakaan perpustakaanSaya = new Perpustakaan("Perpus ABC");
perpustakaanSaya.bukaPerpustakaan(); // Output: Perpustakaan Perpus ABC sedang dibuka.
```

Penjelasan:
- `bukaPerpustakaan()` adalah metode yang digunakan untuk menampilkan informasi bahwa perpustakaan sedang dibuka.

---

## 📌 Aksesibilitas Atribut dan Metode

Java menggunakan **modifikator akses** untuk mengatur visibilitas dan aksesibilitas kelas, atribut, dan metode:
1. `public`: Dapat diakses dari mana saja.
2. `private`: Hanya dapat diakses dari dalam kelas itu sendiri.
3. `protected`: Dapat diakses oleh kelas dalam paket yang sama atau kelas turunan.
4. **default** (tanpa modifikator): Dapat diakses dalam paket yang sama.

### Contoh Modifikator Akses:

```java
public class Person {
    // Atribut dengan modifikator akses
    private String nama;
    public int usia;

    // Konstruktor
    public Person(String nama, int usia) {
        this.nama = nama;
        this.usia = usia;
    }

    // Metode dengan akses private
    private void setNama(String nama) {
        this.nama = nama;
    }

    // Metode untuk mengakses nama
    public String getNama() {
        return nama;
    }
}
```

Pemanggilan:
```java
Person orang = new Person("Alice", 30);
System.out.println(orang.getNama()); // Output: Alice
// orang.setNama("Bob"); // Error karena setNama() private
```

Penjelasan:
- `nama` adalah atribut `private` dan hanya bisa diakses melalui metode `getNama()`.
- `usia` adalah atribut `public` dan dapat diakses langsung.

---

## 📌 Latihan

1. Buatlah kelas `Laptop` dengan atribut `merk`, `model`, dan `tahun`, dan buatlah metode untuk menampilkan informasi laptop.
2. Buatlah konstruktor dalam kelas `Karyawan` untuk menginisialisasi `nama`, `gaji`, dan `departemen`, dan buat metode untuk menampilkan gaji karyawan.
3. Cobalah membuat kelas `PersegiPanjang` dengan atribut `panjang` dan `lebar`, dan buat metode untuk menghitung luasnya.

---

## 🎯 Kesimpulan

- **Kelas** adalah blueprint untuk membuat objek yang memiliki atribut dan metode.
- **Konstruktor** digunakan untuk menginisialisasi objek dengan nilai tertentu saat objek dibuat.
- **Metode** dalam kelas mendefinisikan perilaku objek.
- **Modifikator akses** digunakan untuk mengontrol akses ke atribut dan metode dalam kelas.
- **Objek** adalah instance dari sebuah kelas yang memiliki data dan dapat menjalankan metode yang didefinisikan oleh kelas tersebut.

Dengan memahami kelas dan objek, kamu akan dapat mulai membangun program berorientasi objek yang lebih terstruktur dan modular di Java.

---

> 🚀 Next: [06 - Inheritance dalam Java](06-inheritance-dalam-java.md)
```

---

Materi ini menjelaskan dasar-dasar kelas dalam Java, termasuk cara membuat dan menggunakan kelas, konstruktor, metode, serta aksesibilitas atribut dan metode. Semoga ini membantu memahami konsep kelas dalam Java! Jika ada hal lain yang perlu disesuaikan, beri tahu saya!