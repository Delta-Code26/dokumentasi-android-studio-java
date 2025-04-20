# 🧠 Operator dalam Java

Operator adalah simbol yang digunakan untuk melakukan operasi terhadap variabel atau nilai. Di Java, ada beberapa jenis operator yang bisa kamu gunakan dalam program.

---

## 📌 Jenis-jenis Operator di Java

### 1. **Operator Aritmatika**

Operator ini digunakan untuk melakukan perhitungan matematika, seperti penjumlahan, pengurangan, dll.

| Operator | Nama        | Contoh         | Keterangan                           |
|----------|-------------|----------------|--------------------------------------|
| `+`      | Penjumlahan | `a + b`        | Menjumlahkan dua angka               |
| `-`      | Pengurangan | `a - b`        | Mengurangi angka pertama dengan angka kedua |
| `*`      | Perkalian   | `a * b`        | Mengalikan dua angka                 |
| `/`      | Pembagian   | `a / b`        | Membagi angka pertama dengan angka kedua |
| `%`      | Sisa bagi   | `a % b`        | Menghasilkan sisa dari pembagian     |

**Contoh penggunaan:**

```java
int a = 10;
int b = 5;
int hasil = a + b; // Hasilnya 15
```

---

### 2. **Operator Relasional (Perbandingan)**

Operator ini digunakan untuk membandingkan dua nilai.

| Operator | Nama        | Contoh         | Keterangan                           |
|----------|-------------|----------------|--------------------------------------|
| `==`     | Sama dengan | `a == b`       | Menghasilkan `true` jika `a` sama dengan `b` |
| `!=`     | Tidak sama dengan | `a != b` | Menghasilkan `true` jika `a` tidak sama dengan `b` |
| `>`      | Lebih besar | `a > b`        | Menghasilkan `true` jika `a` lebih besar dari `b` |
| `<`      | Lebih kecil | `a < b`        | Menghasilkan `true` jika `a` lebih kecil dari `b` |
| `>=`     | Lebih besar atau sama dengan | `a >= b` | Menghasilkan `true` jika `a` lebih besar atau sama dengan `b` |
| `<=`     | Lebih kecil atau sama dengan | `a <= b` | Menghasilkan `true` jika `a` lebih kecil atau sama dengan `b` |

**Contoh penggunaan:**

```java
int a = 10;
int b = 5;
boolean hasil = a > b; // Hasilnya true
```

---

### 3. **Operator Logika**

Operator ini digunakan untuk menggabungkan dua atau lebih kondisi boolean.

| Operator | Nama        | Contoh         | Keterangan                           |
|----------|-------------|----------------|--------------------------------------|
| `&&`     | AND         | `a && b`       | Menghasilkan `true` jika kedua kondisi benar |
| `||`     | OR          | `a || b`       | Menghasilkan `true` jika salah satu kondisi benar |
| `!`      | NOT         | `!a`           | Menghasilkan kebalikan dari kondisi `a` |

**Contoh penggunaan:**

```java
boolean a = true;
boolean b = false;
boolean hasil = a && b; // Hasilnya false
```

---

### 4. **Operator Penugasan**

Operator ini digunakan untuk memberikan nilai pada variabel.

| Operator | Nama       | Contoh         | Keterangan                           |
|----------|------------|----------------|--------------------------------------|
| `=`      | Penugasan  | `a = b`        | Memberikan nilai `b` ke variabel `a` |
| `+=`     | Penugasan Tambah | `a += b` | Menambahkan nilai `b` ke `a` dan menyimpan hasilnya ke `a` |
| `-=`     | Penugasan Kurang | `a -= b` | Mengurangi nilai `b` dari `a` dan menyimpan hasilnya ke `a` |
| `*=`     | Penugasan Kali | `a *= b` | Mengalikan nilai `a` dengan `b` dan menyimpan hasilnya ke `a` |
| `/=`     | Penugasan Bagi | `a /= b` | Membagi nilai `a` dengan `b` dan menyimpan hasilnya ke `a` |
| `%=`     | Penugasan Sisa Bagi | `a %= b` | Menghitung sisa pembagian nilai `a` dengan `b` dan menyimpan hasilnya ke `a` |

**Contoh penggunaan:**

```java
int a = 10;
a += 5;  // a = a + 5, hasilnya a = 15
```

---

### 5. **Operator Unary**

Operator ini digunakan untuk operasi pada satu variabel saja, seperti menambah atau mengurangi nilai variabel.

| Operator | Nama        | Contoh         | Keterangan                           |
|----------|-------------|----------------|--------------------------------------|
| `++`     | Increment   | `a++`          | Menambah nilai variabel sebesar 1    |
| `--`     | Decrement   | `a--`          | Mengurangi nilai variabel sebesar 1  |
| `+`      | Positif     | `+a`           | Menunjukkan angka positif (tidak mengubah nilai) |
| `-`      | Negatif     | `-a`           | Menunjukkan angka negatif            |

**Contoh penggunaan:**

```java
int a = 5;
a++;  // a menjadi 6
```

---

## 🧪 Latihan

Coba buat program yang:

- Menerima dua input angka.
- Melakukan perhitungan menggunakan operator aritmatika (+, -, *, /, %).
- Menampilkan hasil dari setiap operasi tersebut.

---

## 🎯 Kesimpulan

- Operator aritmatika digunakan untuk operasi matematika dasar.
- Operator relasional digunakan untuk perbandingan nilai.
- Operator logika digunakan untuk menggabungkan kondisi boolean.
- Operator penugasan digunakan untuk memberikan nilai pada variabel.
- Operator unary digunakan untuk operasi sederhana seperti increment dan decrement.

Dengan menguasai operator-operator ini, kamu akan bisa membuat berbagai jenis logika dan perhitungan dalam program Java!

---

> 🚀 Next: [03 - Tipe Data dan Variabel](03-tipe-data-dan-variabel.md)
```

---

Materi ini menjelaskan tentang operator yang akan sering kamu temui dalam pemrograman Java. Operator-operator ini adalah dasar yang akan mendukung kamu dalam menulis kode yang lebih kompleks. Kamu bisa coba latihan-latihan di atas untuk mempraktikkan apa yang sudah dipelajari!
