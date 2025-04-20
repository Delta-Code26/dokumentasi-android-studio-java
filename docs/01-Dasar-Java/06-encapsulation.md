# 🧠 Encapsulation dalam OOP (Pemrograman Berorientasi Objek) di Java

**Encapsulation** adalah konsep penting dalam **Pemrograman Berorientasi Objek (OOP)** yang mengacu pada pembungkusan data (variabel) dan metode (fungsi) dalam satu unit yang disebut **kelas**. Konsep ini juga melibatkan penyembunyian data internal objek dan hanya membiarkan akses ke data tersebut melalui metode tertentu, yang disebut **getter** dan **setter**.

Dengan kata lain, **encapsulation** adalah cara untuk melindungi data dan memastikan data tersebut hanya dapat dimanipulasi dengan cara yang sah (terkontrol).

---

## 📌 Apa Itu Encapsulation?

Encapsulation memungkinkan kita untuk mengontrol akses terhadap data dengan cara yang terorganisir dan aman. Dalam Java, encapsulation dilakukan dengan menggunakan **modifikator akses** untuk menentukan apakah variabel atau metode dapat diakses langsung dari luar kelas atau tidak.

### Contoh Dunia Nyata:
Bayangkan Anda memiliki sebuah **kotak berisi barang berharga**. Anda bisa mengontrol bagaimana barang-barang tersebut bisa diambil atau disimpan melalui **kunci kotak**. Anda tidak membiarkan orang sembarangan membuka kotak tanpa pengawasan, melainkan mereka harus menggunakan kunci tertentu (getter atau setter) untuk melakukan tindakan tertentu.

---

## 📌 Cara Mengimplementasikan Encapsulation di Java

### Langkah 1: Menyembunyikan Data (Private Variables)

Untuk memulai, kita harus mendeklarasikan **variabel** yang ingin kita encapsulate sebagai `private`. Dengan begitu, variabel tersebut tidak dapat diakses langsung dari luar kelas.

### Langkah 2: Menyediakan Metode Akses (Getter & Setter)

Kemudian, kita menyediakan **metode akses** yang disebut **getter** untuk mengambil nilai variabel dan **setter** untuk mengubah nilai variabel.

---

## 📌 Contoh Kode Encapsulation

Berikut adalah contoh sederhana untuk mengimplementasikan encapsulation di Java:

### Contoh Kode:

```java
class Mahasiswa {
    // Variabel privat (disembunyikan dari luar kelas)
    private String nama;
    private int usia;

    // Getter untuk nama
    public String getNama() {
        return nama;
    }

    // Setter untuk nama
    public void setNama(String nama) {
        this.nama = nama;
    }

    // Getter untuk usia
    public int getUsia() {
        return usia;
    }

    // Setter untuk usia
    public void setUsia(int usia) {
        if (usia > 0) { // Validasi usia tidak boleh kurang dari 1
            this.usia = usia;
        } else {
            System.out.println("Usia tidak valid!");
        }
    }
}

public class Main {
    public static void main(String[] args) {
        // Membuat objek Mahasiswa
        Mahasiswa mahasiswa = new Mahasiswa();

        // Menggunakan setter untuk mengatur nilai
        mahasiswa.setNama("Budi");
        mahasiswa.setUsia(20);

        // Menggunakan getter untuk mendapatkan nilai
        System.out.println("Nama: " + mahasiswa.getNama());
        System.out.println("Usia: " + mahasiswa.getUsia());
    }
}
```

### Penjelasan:
- **Variabel `nama` dan `usia`** adalah **private**, artinya mereka tidak bisa diakses langsung dari luar kelas `Mahasiswa`.
- **Metode `getNama()` dan `setNama()`** adalah **getter dan setter** yang digunakan untuk mengambil dan mengubah nilai `nama`.
- **Metode `getUsia()` dan `setUsia()`** juga digunakan untuk mengakses dan memvalidasi nilai `usia`.
- Dalam setter `setUsia()`, terdapat validasi untuk memastikan usia yang dimasukkan lebih dari 0.

---

## 📌 Manfaat Encapsulation

1. **Kontrol Akses**: Dengan menggunakan getter dan setter, kita bisa mengontrol akses terhadap data dan memastikan bahwa data hanya dapat diubah dengan cara yang benar.
2. **Keamanan Data**: Penyembunyian data di dalam kelas (private variables) membuat data lebih aman, karena data tidak bisa diubah secara langsung oleh pihak luar.
3. **Mempermudah Pemeliharaan Kode**: Encapsulation memungkinkan kita untuk mengubah implementasi internal tanpa mempengaruhi bagian lain dari program yang menggunakan kelas tersebut.
4. **Pengendalian Validasi**: Dengan setter, kita dapat menambahkan **validasi** dan aturan bisnis saat data dimodifikasi.

---

## 📌 Contoh Lain Penggunaan Encapsulation

Mari lihat contoh lain yang lebih praktis dengan penggunaan validasi:

### Contoh Validasi Dengan Encapsulation:

```java
class AkunBank {
    private String nomorRekening;
    private double saldo;

    // Getter dan Setter untuk nomor rekening
    public String getNomorRekening() {
        return nomorRekening;
    }

    public void setNomorRekening(String nomorRekening) {
        this.nomorRekening = nomorRekening;
    }

    // Getter dan Setter untuk saldo
    public double getSaldo() {
        return saldo;
    }

    public void setSaldo(double saldo) {
        if (saldo >= 0) {
            this.saldo = saldo;
        } else {
            System.out.println("Saldo tidak bisa negatif.");
        }
    }

    // Metode untuk melakukan transfer
    public void transfer(AkunBank tujuan, double jumlah) {
        if (this.saldo >= jumlah) {
            this.saldo -= jumlah;
            tujuan.setSaldo(tujuan.getSaldo() + jumlah);
            System.out.println("Transfer berhasil.");
        } else {
            System.out.println("Saldo tidak cukup.");
        }
    }
}

public class Main {
    public static void main(String[] args) {
        AkunBank akun1 = new AkunBank();
        AkunBank akun2 = new AkunBank();

        akun1.setNomorRekening("1234567890");
        akun1.setSaldo(1000);

        akun2.setNomorRekening("0987654321");
        akun2.setSaldo(500);

        System.out.println("Saldo Akun 1: " + akun1.getSaldo());
        System.out.println("Saldo Akun 2: " + akun2.getSaldo());

        akun1.transfer(akun2, 300);

        System.out.println("Saldo Akun 1 setelah transfer: " + akun1.getSaldo());
        System.out.println("Saldo Akun 2 setelah transfer: " + akun2.getSaldo());
    }
}
```

### Penjelasan:
- Kelas `AkunBank` memiliki variabel **private** `nomorRekening` dan `saldo`.
- Setter untuk `saldo` melakukan **validasi** agar saldo tidak bisa bernilai negatif.
- Metode `transfer()` digunakan untuk melakukan transaksi antar akun, yang juga memeriksa apakah saldo mencukupi.

---

## 📌 Modifikator Akses dalam Encapsulation

Untuk mencapai encapsulation, kita menggunakan **modifikator akses** di Java:

- **`private`**: Variabel atau metode hanya bisa diakses dalam kelas yang sama.
- **`public`**: Variabel atau metode bisa diakses oleh kelas lain.
- **`protected`**: Variabel atau metode bisa diakses dalam paket yang sama atau kelas turunan (subclass).
- **`default` (tanpa modifikator)**: Variabel atau metode hanya bisa diakses dalam paket yang sama.

---

## 🎯 Kesimpulan

- **Encapsulation** menyembunyikan implementasi data dan hanya memberikan akses ke data melalui **getter dan setter**.
- Dengan menggunakan encapsulation, kita dapat mengontrol akses dan modifikasi data, serta menjaga integritas dan keamanan data.
- **Getter dan setter** memberikan fleksibilitas untuk memvalidasi atau memanipulasi data saat data diakses atau diubah.

---

> 🚀 Next: [07 - Polymorphism dalam Java](07-polymorphism-dalam-java.md)
```

---

Materi ini menjelaskan konsep **Encapsulation** dalam Pemrograman Berorientasi Objek di Java, termasuk cara mengimplementasikannya dengan menggunakan **private variables**, **getter**, dan **setter**. Jika ada hal lain yang perlu disesuaikan atau ditambahkan, beri tahu saya!