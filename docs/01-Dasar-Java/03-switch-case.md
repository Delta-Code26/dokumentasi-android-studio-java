# 🧠 Penggunaan Switch-Case dalam Java

Struktur kontrol `switch-case` adalah cara alternatif untuk menangani percabangan kondisi lebih dari dua, terutama ketika kita ingin membandingkan sebuah nilai terhadap beberapa pilihan yang sudah ditentukan sebelumnya. Dibandingkan dengan menggunakan banyak `if-else if`, `switch-case` sering kali lebih mudah dibaca dan lebih efisien dalam situasi tertentu.

---

## 📌 Struktur Dasar `switch-case`

Struktur dasar dari pernyataan `switch` adalah sebagai berikut:

```java
switch (ekspresi) {
    case nilai1:
        // kode yang dijalankan jika ekspresi == nilai1
        break;
    case nilai2:
        // kode yang dijalankan jika ekspresi == nilai2
        break;
    // lebih banyak case bisa ditambahkan
    default:
        // kode yang dijalankan jika ekspresi tidak cocok dengan case manapun
}
```

**Penjelasan:**
- **Ekspresi:** Ini adalah nilai atau variabel yang akan dibandingkan dengan setiap `case`.
- **case nilaiX:** Setiap `case` berisi nilai yang dibandingkan dengan ekspresi.
- **break:** Pernyataan `break` digunakan untuk keluar dari struktur `switch` setelah blok kode pada case tertentu dijalankan. Jika `break` tidak ditambahkan, eksekusi akan dilanjutkan ke case berikutnya (fall-through).
- **default:** Bagian ini opsional, digunakan jika tidak ada case yang cocok dengan ekspresi.

---

## 📌 Contoh Penggunaan `switch-case`

Misalnya, kita ingin mencetak nama hari berdasarkan angka yang dimasukkan. Angka 1 akan berarti Senin, angka 2 berarti Selasa, dan seterusnya.

### Contoh Kode:

```java
int hari = 3;
switch (hari) {
    case 1:
        System.out.println("Senin");
        break;
    case 2:
        System.out.println("Selasa");
        break;
    case 3:
        System.out.println("Rabu");
        break;
    case 4:
        System.out.println("Kamis");
        break;
    case 5:
        System.out.println("Jumat");
        break;
    case 6:
        System.out.println("Sabtu");
        break;
    case 7:
        System.out.println("Minggu");
        break;
    default:
        System.out.println("Hari tidak valid");
}
```

**Output:**
```
Rabu
```

Pada contoh di atas, nilai `hari` adalah 3, yang berarti program akan mencetak "Rabu".

---

## 📌 Fall-through dalam `switch-case`

Jika kita menghilangkan `break` pada sebuah `case`, eksekusi akan jatuh ke `case` berikutnya, yang disebut dengan **fall-through**. Hal ini bisa berguna dalam beberapa kasus, tetapi harus hati-hati karena dapat menyebabkan hasil yang tidak diinginkan.

### Contoh Fall-through:

```java
int angka = 2;
switch (angka) {
    case 1:
        System.out.println("Satu");
    case 2:
        System.out.println("Dua");
    case 3:
        System.out.println("Tiga");
        break;
    default:
        System.out.println("Angka tidak valid");
}
```

**Output:**
```
Dua
Tiga
```

Pada contoh di atas, karena tidak ada `break` setelah `case 1` dan `case 2`, program melanjutkan untuk mengeksekusi `case 2` dan `case 3` meskipun ekspresi awalnya adalah 2.

---

## 📌 Penggunaan `default` dalam `switch-case`

Bagian `default` dalam `switch` dijalankan jika tidak ada `case` yang cocok dengan ekspresi. `default` bersifat opsional, tetapi sangat berguna untuk menangani kondisi yang tidak terduga atau kesalahan input.

### Contoh Kode:

```java
int angka = 8;
switch (angka) {
    case 1:
        System.out.println("Satu");
        break;
    case 2:
        System.out.println("Dua");
        break;
    default:
        System.out.println("Angka tidak valid");
}
```

**Output:**
```
Angka tidak valid
```

Karena tidak ada `case` yang cocok dengan angka 8, bagian `default` yang akan dijalankan.

---

## 📌 Penggunaan `switch` dengan String (Mulai Java 7)

Sejak Java 7, kita bisa menggunakan tipe data `String` dalam ekspresi `switch`. Hal ini sangat mempermudah pengkondisian berdasarkan nilai string.

### Contoh Kode dengan `String`:

```java
String hari = "Senin";
switch (hari) {
    case "Senin":
        System.out.println("Hari pertama minggu");
        break;
    case "Selasa":
        System.out.println("Hari kedua minggu");
        break;
    case "Rabu":
        System.out.println("Hari ketiga minggu");
        break;
    default:
        System.out.println("Hari tidak valid");
}
```

**Output:**
```
Hari pertama minggu
```

---

## 📌 Latihan

1. Buat program yang menggunakan `switch-case` untuk mencetak nama bulan berdasarkan angka (1 untuk Januari, 2 untuk Februari, dan seterusnya).
2. Buat program yang menggunakan `switch-case` untuk menilai sebuah angka sebagai "positif", "negatif", atau "nol".
3. Tambahkan opsi `default` dalam program kamu untuk menangani input yang tidak valid.
4. Cobalah menggunakan `switch-case` dengan `String` untuk mencetak pesan berdasarkan nama hari dalam seminggu.

---

## 🎯 Kesimpulan

- `switch-case` adalah alternatif yang lebih mudah dibaca dan lebih efisien daripada menggunakan banyak `if-else` ketika kita perlu membandingkan satu nilai dengan banyak pilihan.
- Setiap `case` harus diikuti dengan `break` untuk menghindari fall-through, kecuali jika memang diinginkan.
- `default` adalah bagian opsional yang akan dijalankan jika tidak ada `case` yang cocok.
- Sejak Java 7, kita dapat menggunakan tipe data `String` dalam ekspresi `switch`.

Dengan memahami penggunaan `switch-case`, kamu dapat membuat kode yang lebih terstruktur dan mudah dipahami, terutama ketika berhadapan dengan percabangan yang melibatkan banyak kondisi.

---

> 🚀 Next: [04 - Fungsi dan Metode dalam Java](04-fungsi-metode-dalam-java.md)
```

---

Materi ini memberikan pemahaman tentang penggunaan `switch-case` di Java, lengkap dengan contoh kode dan penjelasan. Dengan ini, pemula dapat memahami kapan dan bagaimana menggunakan `switch-case` untuk menangani berbagai kondisi dalam program.
