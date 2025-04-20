# 🧠 Struktur Kontrol If-Else dalam Java

Pernyataan kondisi `if-else` adalah cara untuk mengambil keputusan dalam program berdasarkan kondisi tertentu. Dengan `if-else`, kamu dapat menjalankan blok kode yang berbeda tergantung pada apakah suatu kondisi benar (true) atau salah (false).

---

## 📌 Sintaks Dasar If-Else

Struktur dasar pernyataan `if-else` di Java adalah sebagai berikut:

```java
if (kondisi) {
    // kode yang dijalankan jika kondisi bernilai true
} else {
    // kode yang dijalankan jika kondisi bernilai false
}
```

**Contoh:**

```java
int angka = 10;

if (angka > 5) {
    System.out.println("Angka lebih besar dari 5");
} else {
    System.out.println("Angka kurang atau sama dengan 5");
}
```

Pada contoh di atas, program akan memeriksa apakah variabel `angka` lebih besar dari 5. Jika iya, maka akan mencetak `Angka lebih besar dari 5`. Jika tidak, maka akan mencetak `Angka kurang atau sama dengan 5`.

---

## 📌 Pernyataan If-Else If

Jika kamu memiliki lebih dari dua kemungkinan untuk dipilih, kamu bisa menggunakan pernyataan `else if` untuk menambah kondisi tambahan sebelum mencapai bagian `else`.

### Sintaks:

```java
if (kondisi1) {
    // kode jika kondisi1 bernilai true
} else if (kondisi2) {
    // kode jika kondisi2 bernilai true
} else {
    // kode jika semua kondisi sebelumnya bernilai false
}
```

**Contoh:**

```java
int angka = 10;

if (angka > 10) {
    System.out.println("Angka lebih besar dari 10");
} else if (angka == 10) {
    System.out.println("Angka sama dengan 10");
} else {
    System.out.println("Angka lebih kecil dari 10");
}
```

Pada contoh di atas, program akan memeriksa tiga kondisi:
1. Jika `angka` lebih besar dari 10, maka akan mencetak `Angka lebih besar dari 10`.
2. Jika `angka` sama dengan 10, maka akan mencetak `Angka sama dengan 10`.
3. Jika kedua kondisi di atas tidak terpenuhi, maka akan mencetak `Angka lebih kecil dari 10`.

---

## 📌 Penggunaan Operator Logika

Seringkali, kondisi dalam pernyataan `if-else` memerlukan lebih dari satu syarat. Untuk itu, kamu bisa menggunakan **operator logika** untuk menggabungkan beberapa kondisi.

### Operator Logika:
- **`&&` (AND)**: Kondisi benar jika kedua kondisi bernilai true.
- **`||` (OR)**: Kondisi benar jika salah satu dari kondisi bernilai true.
- **`!` (NOT)**: Membalikkan nilai kondisi.

### Contoh:

```java
int umur = 20;
boolean memilikiSIM = true;

if (umur >= 18 && memilikiSIM) {
    System.out.println("Kamu boleh mengemudi");
} else {
    System.out.println("Kamu tidak boleh mengemudi");
}
```

Pada contoh di atas, agar program mencetak "Kamu boleh mengemudi", kedua kondisi (`umur >= 18` dan `memilikiSIM == true`) harus bernilai true.

---

## 📌 Penggunaan If-Else di Dalam Statement Lain

Pernyataan `if-else` dapat diletakkan di dalam pernyataan lainnya, baik itu `if` lainnya maupun dalam perulangan seperti `for`, `while`, dan sebagainya.

### Contoh:

```java
int angka = 10;

if (angka > 0) {
    if (angka % 2 == 0) {
        System.out.println("Angka positif dan genap");
    } else {
        System.out.println("Angka positif dan ganjil");
    }
} else {
    System.out.println("Angka negatif");
}
```

Pada contoh di atas, program pertama-tama memeriksa apakah `angka` lebih besar dari 0. Jika ya, maka akan memeriksa apakah `angka` genap atau ganjil. Jika tidak, maka akan mencetak "Angka negatif".

---

## 📌 Nested If-Else

Kamu juga bisa membuat **nested if-else**, yaitu menggunakan pernyataan `if-else` di dalam blok lain dari `if` atau `else`.

### Contoh:

```java
int nilai = 85;

if (nilai >= 90) {
    System.out.println("Nilai A");
} else if (nilai >= 80) {
    System.out.println("Nilai B");
} else if (nilai >= 70) {
    System.out.println("Nilai C");
} else {
    System.out.println("Nilai D");
}
```

Pada contoh di atas, program akan mencetak "Nilai B" karena `nilai` adalah 85, yang memenuhi kondisi `nilai >= 80`.

---

## 🧪 Latihan

1. Buat program yang mengecek apakah suatu angka genap atau ganjil menggunakan pernyataan `if-else`.
2. Buat program untuk menentukan apakah seseorang boleh memilih berdasarkan umur (18 tahun ke atas boleh memilih).
3. Buat program yang menentukan apakah sebuah tahun adalah tahun kabisat (tahun yang habis dibagi 4 dan, jika dibagi 100, harus habis dibagi 400).

---

## 🎯 Kesimpulan

- Pernyataan `if-else` digunakan untuk mengambil keputusan dalam program berdasarkan kondisi tertentu.
- Kamu bisa menggunakan `if`, `else if`, dan `else` untuk menangani berbagai kondisi.
- Operator logika seperti `&&`, `||`, dan `!` membantu menggabungkan beberapa kondisi dalam satu pernyataan.
- Pernyataan `if-else` juga dapat digunakan di dalam perulangan dan pernyataan lain.

Dengan memahami dan menggunakan struktur kontrol ini, kamu akan dapat membuat program Java yang lebih dinamis dan interaktif!

---

> 🚀 Next: [04 - Switch Case dalam Java](04-switch-case-dalam-java.md)
```

---

Materi ini menjelaskan tentang penggunaan pernyataan kondisi `if-else` di Java. Pernyataan ini sangat penting dalam pengembangan logika program, dan kamu akan sering menggunakannya untuk membuat keputusan berdasarkan kondisi yang ada.
