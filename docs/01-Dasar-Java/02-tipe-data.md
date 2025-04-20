# 🧠 Tipe Data dalam Java

Tipe data adalah cara untuk mendefinisikan jenis nilai yang bisa disimpan dalam sebuah variabel. Setiap tipe data memiliki ukuran dan karakteristik yang berbeda-beda. Dalam Java, ada dua jenis tipe data utama: **Tipe Data Primitif** dan **Tipe Data Referensi**.

---

## 📌 Tipe Data Primitif

Tipe data primitif adalah tipe data dasar yang sudah ada di Java dan langsung merepresentasikan nilai.

### 1. **Tipe Data Integer**

- **`byte`**: Menyimpan angka bulat (integer) dari -128 hingga 127.
- **`short`**: Menyimpan angka bulat dari -32.768 hingga 32.767.
- **`int`**: Menyimpan angka bulat dari -2^31 hingga 2^31 - 1 (lebih umum digunakan).
- **`long`**: Menyimpan angka bulat lebih besar dari `int`, yaitu dari -2^63 hingga 2^63 - 1.

**Contoh penggunaan:**

```java
byte a = 120;
short b = 32000;
int c = 100000;
long d = 1000000000L; // Menambahkan 'L' di akhir untuk mendeklarasikan long
```

### 2. **Tipe Data Desimal**

- **`float`**: Menyimpan angka desimal dengan presisi 7 digit angka.
- **`double`**: Menyimpan angka desimal dengan presisi lebih tinggi, hingga 15 digit angka.

**Contoh penggunaan:**

```java
float e = 3.14f;  // Menambahkan 'f' di akhir untuk mendeklarasikan float
double f = 3.14159;
```

### 3. **Tipe Data Karakter**

- **`char`**: Menyimpan satu karakter (misalnya 'a', 'B', '1', dll). Representasi karakter menggunakan format Unicode.

**Contoh penggunaan:**

```java
char g = 'A';
```

### 4. **Tipe Data Boolean**

- **`boolean`**: Menyimpan nilai `true` atau `false`, digunakan untuk operasi logika dan kontrol alur program.

**Contoh penggunaan:**

```java
boolean h = true;
```

---

## 📌 Tipe Data Referensi

Tipe data referensi adalah tipe data yang menyimpan referensi atau alamat memori ke objek. Tipe data ini bisa berupa objek atau array.

### 1. **String**

- **`String`**: Menyimpan teks atau rangkaian karakter. String di Java adalah objek yang digunakan untuk bekerja dengan teks.

**Contoh penggunaan:**

```java
String i = "Hello, World!";
```

### 2. **Array**

- **`Array`**: Menyimpan kumpulan data dengan tipe yang sama. Ukuran array tidak dapat diubah setelah dibuat.

**Contoh penggunaan:**

```java
int[] arr = {1, 2, 3, 4, 5};
String[] names = {"Alice", "Bob", "Charlie"};
```

---

## 📌 Nilai Default Tipe Data

Jika sebuah variabel bertipe primitif dideklarasikan tapi tidak diberikan nilai, maka variabel tersebut akan mendapatkan nilai default sebagai berikut:

| Tipe Data | Nilai Default |
|-----------|---------------|
| `byte`    | 0             |
| `short`   | 0             |
| `int`     | 0             |
| `long`    | 0L            |
| `float`   | 0.0f          |
| `double`  | 0.0d          |
| `char`    | '\u0000' (null character) |
| `boolean` | false         |

---

## 📌 Konversi Tipe Data (Type Casting)

Kadang, kamu perlu mengubah nilai dari satu tipe data ke tipe data lain. Ada dua jenis konversi:

### 1. **Paksakan Konversi (Explicit Casting)**

- Mengubah tipe data dari tipe yang lebih besar ke tipe yang lebih kecil, seperti mengubah `double` menjadi `int`.

**Contoh penggunaan:**

```java
double j = 3.14;
int k = (int) j;  // Hasilnya 3, karena pecahan dibuang
```

### 2. **Konversi Otomatis (Implicit Casting)**

- Mengubah tipe data dari tipe yang lebih kecil ke tipe yang lebih besar, seperti mengubah `int` menjadi `double`.

**Contoh penggunaan:**

```java
int l = 100;
double m = l;  // Konversi otomatis dari int ke double
```

---

## 🧪 Latihan

1. Deklarasikan sebuah variabel dengan tipe data `byte`, `short`, `int`, `long`, dan `double`, lalu tampilkan nilai-nilai tersebut.
2. Coba buat sebuah array dengan 5 elemen bertipe `String`, lalu tampilkan setiap elemen array menggunakan perulangan `for`.

---

## 🎯 Kesimpulan

- **Tipe data primitif** adalah tipe dasar yang langsung menyimpan nilai.
- **Tipe data referensi** menyimpan alamat memori ke objek atau array.
- Java memiliki berbagai tipe data untuk menyimpan berbagai jenis nilai, dan kamu bisa mengonversi antar tipe data jika diperlukan.

Setelah memahami tipe data ini, kamu bisa mulai menggunakan berbagai tipe data dalam program Java yang kamu buat!

---

> 🚀 Next: [03 - Variabel dan Konstanta](03-variabel-dan-konstanta.md)
```

---

Materi ini menjelaskan berbagai tipe data yang akan kamu temui dalam Java. Memahami tipe data dengan baik sangat penting karena setiap tipe data memiliki karakteristik yang berbeda dan digunakan untuk kebutuhan yang berbeda. Kamu bisa mencoba latihan-latihan di atas untuk lebih memahami konsep tipe data.
