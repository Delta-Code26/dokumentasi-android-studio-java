# 🧠 Objek dalam Java

Dalam pemrograman berorientasi objek (OOP), **objek** adalah representasi dari suatu entitas yang memiliki data dan perilaku. Di dalam Java, objek adalah instansi atau contoh dari kelas. Setiap objek memiliki **atribut** (data) dan **metode** (fungsi) yang didefinisikan dalam kelas.

---

## 📌 Apa Itu Objek?

Objek adalah instansi dari kelas yang berisi data dan metode untuk melakukan operasi terhadap data tersebut. Objek berfungsi untuk mengimplementasikan konsep dunia nyata ke dalam kode.

Contoh dunia nyata: Sebuah mobil adalah objek yang memiliki atribut seperti warna, merk, dan model, serta metode seperti `nyalakanMesin()` atau `rem()`.

---

## 📌 Membuat Objek

Untuk membuat objek, kita harus memiliki kelas terlebih dahulu. Setelah itu, kita dapat membuat objek menggunakan kata kunci `new`, yang akan memanggil konstruktor kelas untuk menginisialisasi objek.

### Contoh Membuat Objek:

```java
public class Mobil {
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
- `Mobil mobilSaya = new Mobil("Merah", "Toyota");` membuat objek `mobilSaya` dari kelas `Mobil` dengan atribut `warna` dan `merk` yang telah diinisialisasi.
- `mobilSaya.tampilkanInfo();` memanggil metode `tampilkanInfo()` yang menampilkan informasi objek.

---

## 📌 Atribut dalam Objek

Atribut adalah variabel yang mendefinisikan data yang dimiliki oleh objek. Setiap objek dapat memiliki nilai atribut yang berbeda. Atribut dideklarasikan di dalam kelas dan dapat diakses menggunakan objek yang dibuat.

### Contoh Atribut:

```java
public class Buku {
    String judul;
    String penulis;
}
```

Di sini, `judul` dan `penulis` adalah atribut yang dimiliki oleh objek `Buku`.

---

## 📌 Metode dalam Objek

Metode adalah fungsi yang mendefinisikan perilaku atau aksi yang dapat dilakukan oleh objek. Metode ini bisa mengakses dan memodifikasi atribut objek.

### Contoh Metode:

```java
public class Buku {
    String judul;
    String penulis;

    public Buku(String judul, String penulis) {
        this.judul = judul;
        this.penulis = penulis;
    }

    // Metode untuk menampilkan informasi buku
    public void tampilkanInfo() {
        System.out.println("Judul: " + judul + ", Penulis: " + penulis);
    }
}
```

Di sini, `tampilkanInfo()` adalah metode yang digunakan untuk menampilkan informasi buku yang ada pada objek `Buku`.

---

## 📌 Memanggil Atribut dan Metode Objek

Setelah objek dibuat, kita dapat mengakses atribut dan memanggil metode objek menggunakan sintaks `objek.atribut` atau `objek.metode()`.

### Contoh Memanggil Atribut dan Metode:

```java
public class Main {
    public static void main(String[] args) {
        Buku bukuSaya = new Buku("Belajar Java", "John Doe");

        // Memanggil metode objek
        bukuSaya.tampilkanInfo(); // Output: Judul: Belajar Java, Penulis: John Doe
    }
}
```

---

## 📌 Menyusun Objek dalam Array

Kita juga dapat membuat array dari objek. Array objek memungkinkan kita untuk menyimpan beberapa objek dalam satu struktur data.

### Contoh Array Objek:

```java
public class Buku {
    String judul;
    String penulis;

    public Buku(String judul, String penulis) {
        this.judul = judul;
        this.penulis = penulis;
    }

    public void tampilkanInfo() {
        System.out.println("Judul: " + judul + ", Penulis: " + penulis);
    }
}

public class Main {
    public static void main(String[] args) {
        // Membuat array objek Buku
        Buku[] daftarBuku = new Buku[2];

        // Mengisi array dengan objek Buku
        daftarBuku[0] = new Buku("Belajar Java", "John Doe");
        daftarBuku[1] = new Buku("Pemrograman Android", "Jane Smith");

        // Memanggil metode dari setiap objek dalam array
        for (Buku buku : daftarBuku) {
            buku.tampilkanInfo();
        }
    }
}
```

Output:
```
Judul: Belajar Java, Penulis: John Doe
Judul: Pemrograman Android, Penulis: Jane Smith
```

---

## 📌 Objek dan Konstruktor

Setiap objek yang dibuat melalui kata kunci `new` akan menjalani proses konstruksi. Konstruktor adalah metode yang dipanggil ketika objek dibuat dan digunakan untuk menginisialisasi atribut objek.

### Contoh Konstruktor dalam Objek:

```java
public class Mobil {
    String warna;
    String merk;

    // Konstruktor
    public Mobil(String warna, String merk) {
        this.warna = warna;
        this.merk = merk;
    }

    public void tampilkanInfo() {
        System.out.println("Mobil warna: " + warna + " dan merk: " + merk);
    }
}

public class Main {
    public static void main(String[] args) {
        // Membuat objek Mobil dan menginisialisasi atribut dengan konstruktor
        Mobil mobilSaya = new Mobil("Biru", "Honda");
        mobilSaya.tampilkanInfo(); // Output: Mobil warna: Biru dan merk: Honda
    }
}
```

---

## 📌 Latihan

1. **Buat kelas `Karyawan`** dengan atribut `nama`, `jabatan`, dan `gaji`. Buat konstruktor untuk menginisialisasi atribut tersebut dan metode untuk menampilkan informasi karyawan.
2. **Buat objek `Perpustakaan`** yang memiliki atribut `nama`, `lokasi`, dan `jumlahBuku`. Implementasikan konstruktor dan metode untuk menampilkan jumlah buku yang ada.
3. **Buat objek `Sepeda`** dengan atribut `merk`, `warna`, dan `kecepatan`. Tambahkan metode untuk menambah kecepatan sepeda.

---

## 🎯 Kesimpulan

- **Objek** adalah instansi dari kelas dan dapat memiliki data (atribut) dan perilaku (metode).
- **Konstruktor** digunakan untuk menginisialisasi objek saat objek pertama kali dibuat.
- Objek dapat mengakses atribut dan metode untuk melakukan operasi pada data yang dimilikinya.
- Kita juga dapat menyusun objek dalam array untuk mengelola koleksi objek.

Memahami objek dan cara kerjanya adalah dasar penting dalam pemrograman berorientasi objek dan akan menjadi landasan untuk membangun aplikasi yang lebih kompleks di Java.

---

> 🚀 Next: [06 - Inheritance dalam Java](06-inheritance-dalam-java.md)
```

---

Materi ini memberikan penjelasan tentang objek dalam Java, termasuk cara membuat objek, atribut, metode, dan cara mengelola objek dalam array. Jika ada hal lain yang perlu disesuaikan atau ditambahkan, beri tahu saya!