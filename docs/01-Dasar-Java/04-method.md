# 🧠 Metode dalam Java

Metode (atau fungsi) adalah blok kode dalam Java yang dirancang untuk melakukan suatu tugas tertentu. Metode dapat dipanggil kapan saja dalam program untuk menjalankan tugas tersebut. Penggunaan metode memungkinkan kita untuk mengorganisir kode menjadi bagian-bagian yang lebih kecil dan mudah dipelihara.

---

## 📌 Apa Itu Metode?

Metode adalah bagian dari kelas dalam Java yang memiliki fungsi tertentu. Setiap kali kamu ingin melakukan suatu tindakan berulang, kamu bisa menulis kode tersebut dalam bentuk metode.

Metode dapat mengembalikan nilai (misalnya, angka atau string) atau tidak mengembalikan nilai sama sekali (menggunakan `void`).

---

## 📌 Struktur Dasar Metode

Struktur dasar metode di Java terdiri dari beberapa bagian:
1. **Modifikator Akses**: Menentukan hak akses untuk metode (misalnya `public`, `private`).
2. **Tipe Kembalian**: Jenis nilai yang dikembalikan oleh metode, seperti `int`, `String`, atau `void` jika tidak ada nilai yang dikembalikan.
3. **Nama Metode**: Nama untuk mengidentifikasi metode.
4. **Parameter (opsional)**: Nilai yang diberikan ke metode saat dipanggil. Parameter bersifat opsional dan bisa lebih dari satu.
5. **Blok Kode**: Bagian yang berisi perintah yang dijalankan saat metode dipanggil.

### Contoh Struktur Metode:

```java
public void tampilkanPesan() {
    System.out.println("Hello, World!");
}
```

Penjelasan:
- `public`: Modifikator akses yang memungkinkan metode ini dapat dipanggil dari luar kelas.
- `void`: Tipe kembalian yang menunjukkan bahwa metode ini tidak mengembalikan nilai.
- `tampilkanPesan`: Nama metode.
- `{}`: Blok kode yang berisi instruksi yang dijalankan saat metode dipanggil.

---

## 📌 Metode dengan Tipe Kembalian

Metode juga bisa mengembalikan nilai. Tipe kembalian metode ini bisa berupa tipe data dasar seperti `int`, `double`, `String`, atau objek dari kelas lain.

### Contoh Metode dengan Tipe Kembalian:

```java
public int tambahAngka(int a, int b) {
    return a + b;
}
```

Penjelasan:
- `int`: Tipe kembalian yang menunjukkan bahwa metode ini akan mengembalikan nilai bertipe `int`.
- `tambahAngka`: Nama metode.
- `int a, int b`: Parameter yang akan diterima oleh metode.
- `return a + b`: Mengembalikan hasil penjumlahan antara `a` dan `b`.

**Pemanggilan metode:**

```java
int hasil = tambahAngka(5, 3);
System.out.println(hasil); // Output: 8
```

---

## 📌 Parameter dan Argumen

Metode dapat menerima **parameter**, yang digunakan untuk memberikan data ke dalam metode saat pemanggilannya. **Argumen** adalah nilai yang diberikan saat memanggil metode.

### Contoh Penggunaan Parameter:

```java
public void sapaPengguna(String nama) {
    System.out.println("Halo, " + nama + "!");
}
```

**Pemanggilan metode:**

```java
sapaPengguna("John"); // Output: Halo, John!
```

Penjelasan:
- `String nama`: Parameter yang digunakan oleh metode untuk menerima data berupa string.
- `sapaPengguna("John")`: Memanggil metode dan memberikan argumen `"John"`.

---

## 📌 Metode Overloading

Metode overloading memungkinkan kita mendefinisikan beberapa metode dengan nama yang sama, tetapi dengan parameter yang berbeda. Java akan membedakan metode berdasarkan jumlah dan jenis parameter.

### Contoh Metode Overloading:

```java
public int tambah(int a, int b) {
    return a + b;
}

public double tambah(double a, double b) {
    return a + b;
}
```

**Pemanggilan metode:**

```java
int hasil1 = tambah(2, 3); // Menggunakan metode dengan parameter int
double hasil2 = tambah(2.5, 3.5); // Menggunakan metode dengan parameter double
System.out.println(hasil1); // Output: 5
System.out.println(hasil2); // Output: 6.0
```

---

## 📌 Metode Rekursif

Rekursi adalah ketika suatu metode memanggil dirinya sendiri untuk menyelesaikan tugas tertentu. Metode rekursif sering digunakan untuk masalah yang dapat dibagi menjadi sub-masalah yang lebih kecil.

### Contoh Rekursi:

```java
public int hitungFaktorial(int n) {
    if (n == 1) {
        return 1; // Kasus dasar
    } else {
        return n * hitungFaktorial(n - 1); // Pemanggilan rekursif
    }
}
```

**Pemanggilan metode:**

```java
int hasil = hitungFaktorial(5);
System.out.println(hasil); // Output: 120
```

Penjelasan:
- `hitungFaktorial` memanggil dirinya sendiri dengan nilai yang lebih kecil hingga mencapai kasus dasar (`n == 1`).
- `return n * hitungFaktorial(n - 1)` adalah langkah rekursif untuk menghitung faktorial.

---

## 📌 Latihan

1. Buatlah metode `kaliAngka` yang menerima dua parameter dan mengembalikan hasil perkaliannya.
2. Buatlah metode `sapa` yang menerima nama dan usia, lalu mencetak pesan "Halo, [nama]! Kamu berusia [usia] tahun."
3. Cobalah untuk membuat metode overloading untuk menghitung luas berbagai bentuk (persegi, lingkaran, dan segitiga).
4. Cobalah membuat metode rekursif untuk menghitung deret Fibonacci.

---

## 🎯 Kesimpulan

- **Metode** adalah cara untuk mengorganisir kode dalam program.
- **Modifikator Akses** menentukan siapa yang dapat memanggil metode.
- **Tipe Kembalian** menunjukkan jenis nilai yang dikembalikan oleh metode.
- **Parameter** memungkinkan data dikirimkan ke metode.
- **Metode Overloading** memungkinkan kita memiliki beberapa metode dengan nama yang sama, tetapi dengan parameter yang berbeda.
- **Rekursi** adalah teknik untuk menyelesaikan masalah dengan memanggil metode itu sendiri.

Metode sangat penting dalam pengembangan perangkat lunak karena memungkinkan kode yang modular dan dapat dipelihara dengan baik. Dengan memahami konsep dasar metode, kamu dapat mulai mengorganisir logika program dengan lebih baik.

---

> 🚀 Next: [05 - Kelas dan Objek dalam Java](05-kelas-dan-objek-dalam-java.md)
```

---

Materi ini memberikan pemahaman tentang metode dalam Java, termasuk pengenalan tentang struktur dasar, tipe kembalian, parameter, overloading, dan rekursi. Dengan memahami metode, kamu akan lebih siap untuk menulis kode yang lebih terstruktur dan efisien. Jika ada hal lain yang perlu ditambahkan, jangan ragu untuk menghubungi saya!