# 🧠 Variabel dalam Java

Variabel adalah tempat untuk menyimpan data yang digunakan dalam program. Setiap variabel memiliki **nama**, **tipe data**, dan **nilai**. Variabel memungkinkan kamu untuk menyimpan dan memanipulasi data selama program berjalan.

---

## 📌 Mendeklarasikan Variabel

Untuk mendeklarasikan variabel di Java, kamu perlu menyebutkan **tipe data** variabel, diikuti dengan **nama** variabel. Setelah itu, kamu bisa memberikan **nilai** ke variabel tersebut.

### Sintaks Umum

```java
tipeData namaVariabel = nilai;
```

**Contoh:**

```java
int umur = 20;
String nama = "Alice";
double tinggi = 1.75;
```

---

## 📌 Aturan Penamaan Variabel

Nama variabel harus mengikuti aturan berikut:

1. Nama variabel hanya boleh terdiri dari huruf (a-z, A-Z), angka (0-9), dan simbol underscore (`_`).
2. Nama variabel tidak boleh diawali dengan angka (misalnya, `1nama` tidak valid).
3. Nama variabel harus unik dalam lingkupnya.
4. Nama variabel harus dimulai dengan huruf kecil, dan jika terdiri dari beberapa kata, kata kedua dan seterusnya diawali dengan huruf besar (camelCase). Misalnya: `umurSiswa`, `totalHarga`.

Contoh yang benar:

```java
int usia = 25;
double hargaBarang = 199.99;
```

Contoh yang salah:

```java
int 2umur = 25;  // Tidak boleh diawali angka
double total_harga$ = 199.99;  // Tidak boleh menggunakan simbol selain underscore
```

---

## 📌 Tipe Data Variabel

Variabel dapat memiliki berbagai tipe data. Tipe data menentukan jenis data yang dapat disimpan dalam variabel tersebut. Berikut adalah beberapa tipe data yang umum digunakan:

- **`int`**: Menyimpan angka bulat (contoh: 10, -5, 100).
- **`double`**: Menyimpan angka desimal (contoh: 3.14, -0.001, 100.5).
- **`String`**: Menyimpan teks atau rangkaian karakter (contoh: "Hello", "Alice").
- **`boolean`**: Menyimpan nilai `true` atau `false`.

---

## 📌 Inisialisasi Variabel

Selain mendeklarasikan variabel, kamu juga bisa menginisialisasi atau memberikan nilai awal pada variabel saat mendeklarasikannya.

### Contoh:

```java
int angka = 10;  // Variabel angka diinisialisasi dengan nilai 10
String nama = "Bob";  // Variabel nama diinisialisasi dengan nilai "Bob"
```

Kamu juga bisa mendeklarasikan variabel terlebih dahulu, dan memberikan nilai pada variabel tersebut di kemudian hari.

### Contoh:

```java
int angka;
angka = 20;  // Variabel angka diisi dengan nilai 20 setelah deklarasi
```

---

## 📌 Variabel Konstanta

Terkadang, kita membutuhkan variabel yang nilainya tidak akan berubah selama program berjalan. Untuk itu, kita bisa menggunakan **konstanta** dengan kata kunci `final`. Variabel yang dideklarasikan dengan `final` tidak bisa diubah nilainya setelah diinisialisasi.

### Contoh:

```java
final double PI = 3.14159;  // Nilai PI tidak dapat diubah lagi
```

---

## 📌 Lingkup Variabel (Scope)

Variabel memiliki **lingkup** atau **scope** yang menentukan di mana variabel tersebut dapat diakses. Variabel bisa memiliki lingkup global atau lokal.

- **Variabel lokal**: Dideklarasikan dalam sebuah metode dan hanya dapat diakses di dalam metode tersebut.
  
  **Contoh:**
  
  ```java
  public void hitungLuas() {
      int panjang = 5;  // Variabel lokal, hanya bisa diakses dalam metode hitungLuas
      int lebar = 10;
      System.out.println(panjang * lebar);
  }
  ```

- **Variabel global (atau variabel instans)**: Dideklarasikan di luar metode, biasanya di dalam kelas, dan dapat diakses di seluruh bagian kelas.

  **Contoh:**
  
  ```java
  public class Lingkaran {
      double radius;  // Variabel global atau instans
  
      public void setRadius(double r) {
          radius = r;
      }
  
      public double hitungLuas() {
          return Math.PI * radius * radius;
      }
  }
  ```

---

## 📌 Mengubah Nilai Variabel

Kamu bisa mengubah nilai variabel kapan saja setelah deklarasi, asalkan variabel tersebut tidak bertipe `final`.

### Contoh:

```java
int angka = 10;  // Nilai awal
angka = 20;      // Nilai diubah
```

---

## 📌 Variabel dalam Array

Variabel dalam array menyimpan beberapa nilai dengan tipe data yang sama. Kamu bisa mendeklarasikan array dan memberikan nilai kepada setiap elemen array.

### Contoh:

```java
int[] angkaArray = {10, 20, 30, 40};  // Array dengan 4 elemen
System.out.println(angkaArray[0]);     // Output: 10
```

---

## 🧪 Latihan

1. Deklarasikan variabel dengan tipe data `int`, `double`, dan `String`, lalu tampilkan nilainya.
2. Coba buat variabel bertipe `boolean` dan gunakan untuk menentukan apakah suatu angka lebih besar dari 10.
3. Coba buat sebuah konstanta yang menyimpan nilai pi (3.14159) dan tampilkan nilai tersebut.

---

## 🎯 Kesimpulan

- Variabel digunakan untuk menyimpan data dalam program Java.
- Nama variabel harus mengikuti aturan penamaan yang benar.
- Variabel bisa bertipe data primitif (seperti `int`, `double`, dan `boolean`) atau referensi (seperti `String` dan array).
- Variabel yang dideklarasikan dengan `final` menjadi konstanta dan tidak dapat diubah nilainya.

Setelah memahami konsep variabel, kamu akan lebih mudah dalam menyimpan dan memanipulasi data dalam program Java kamu!

---

> 🚀 Next: [03 - Operator dalam Java](03-operator-dalam-java.md)
```

---

Materi ini menjelaskan tentang variabel, aturan penamaannya, tipe data variabel, serta cara menginisialisasi dan mengubah nilai variabel dalam Java. Setelah memahami variabel, kamu bisa menggunakannya untuk membuat aplikasi Java yang lebih dinamis.