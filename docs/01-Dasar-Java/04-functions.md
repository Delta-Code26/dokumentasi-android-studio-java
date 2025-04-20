# 🧠 Fungsi dan Metode dalam Java

Fungsi (atau metode) adalah blok kode yang dirancang untuk melakukan tugas tertentu, dan bisa dipanggil kapan saja di dalam program. Dalam Java, fungsi atau metode digunakan untuk mengorganisir kode menjadi bagian-bagian kecil yang dapat dipanggil ulang.

---

## 📌 Apa itu Fungsi dan Metode?

Dalam Java, istilah **fungsi** dan **metode** sering digunakan bergantian, meskipun keduanya pada dasarnya mengacu pada hal yang sama. Metode adalah fungsi yang ada dalam sebuah kelas. Jadi, setiap kali kita berbicara tentang fungsi dalam Java, kita sebenarnya berbicara tentang metode.

---

## 📌 Struktur Dasar Metode di Java

Struktur dasar sebuah metode dalam Java terdiri dari beberapa bagian utama, yaitu:
1. **Modifikator Akses** (seperti `public`, `private`, dll.)
2. **Tipe Kembalian** (seperti `void` jika tidak ada nilai yang dikembalikan)
3. **Nama Metode** (sebagai identitas metode)
4. **Parameter (opsional)** – variabel yang diberikan ke metode saat dipanggil
5. **Blok Kode** – bagian yang berisi instruksi yang dijalankan saat metode dipanggil

### Contoh Struktur Metode:

```java
public void tampilkanPesan() {
    System.out.println("Hello, World!");
}
```

**Penjelasan:**
- `public`: Modifikator akses, yang berarti metode ini dapat dipanggil dari mana saja.
- `void`: Tipe kembalian, yang berarti metode ini tidak mengembalikan nilai.
- `tampilkanPesan`: Nama metode.
- `()`: Tanda kurung digunakan untuk mendefinisikan parameter metode. Jika tidak ada parameter, biarkan kosong.
- `{}`: Blok kode metode, yang berisi instruksi yang dijalankan saat metode dipanggil.

---

## 📌 Metode dengan Tipe Kembalian

Selain `void`, metode juga dapat mengembalikan nilai tertentu. Dalam hal ini, kita harus menentukan tipe data yang dikembalikan, seperti `int`, `String`, atau tipe data lainnya.

### Contoh Metode dengan Tipe Kembalian:

```java
public int tambahDuaAngka(int a, int b) {
    return a + b;
}
```

**Penjelasan:**
- `int`: Tipe kembalian, yang berarti metode ini mengembalikan nilai bertipe `int`.
- `tambahDuaAngka`: Nama metode.
- `int a, int b`: Parameter yang diterima oleh metode. Kedua parameter ini akan digunakan untuk perhitungan di dalam metode.
- `return`: Digunakan untuk mengembalikan nilai dari metode.

**Pemanggilan metode ini:**

```java
int hasil = tambahDuaAngka(5, 3);
System.out.println(hasil); // Output: 8
```

---

## 📌 Parameter dan Argumen

Metode dapat menerima **parameter**, yang memungkinkan kita untuk mengirimkan data ke dalam metode saat memanggilnya. **Parameter** adalah variabel yang didefinisikan dalam tanda kurung setelah nama metode. Saat memanggil metode, kita mengirimkan **argumen**, yang merupakan nilai yang sesuai dengan parameter yang telah didefinisikan.

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

---

## 📌 Metode dengan Banyak Parameter

Kita dapat mendefinisikan metode dengan lebih dari satu parameter untuk menerima beberapa nilai.

### Contoh Metode dengan Banyak Parameter:

```java
public void tampilkanInfo(String nama, int usia) {
    System.out.println("Nama: " + nama + ", Usia: " + usia);
}
```

**Pemanggilan metode:**

```java
tampilkanInfo("Alice", 25); // Output: Nama: Alice, Usia: 25
```

---

## 📌 Metode Overloading

Java memungkinkan kita untuk mendefinisikan beberapa metode dengan nama yang sama, tetapi dengan parameter yang berbeda. Ini disebut **metode overloading**. Java akan membedakan metode berdasarkan jumlah dan jenis parameter yang diberikan saat pemanggilan.

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

## 📌 Rekursi

Rekursi adalah ketika sebuah metode memanggil dirinya sendiri. Ini berguna untuk menyelesaikan masalah yang bisa dibagi menjadi sub-masalah yang lebih kecil, seperti menghitung faktorial atau mencari nilai dalam struktur data pohon.

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

Metode `hitungFaktorial` akan memanggil dirinya sendiri dengan nilai yang lebih kecil hingga mencapai kasus dasar (`n == 1`).

---

## 📌 Latihan

1. Buat metode `tambahAngka` yang menerima dua parameter dan mengembalikan hasil penjumlahannya.
2. Buat metode `sapa` yang menerima nama dan usia, lalu mencetak pesan "Halo, [nama]! Kamu berusia [usia] tahun."
3. Coba buat metode overloading untuk menghitung luas area dengan parameter yang berbeda (misalnya untuk persegi, lingkaran, dan segitiga).
4. Coba buat metode rekursif untuk menghitung deret Fibonacci.

---

## 🎯 Kesimpulan

- Metode adalah blok kode yang dapat dipanggil untuk melakukan tugas tertentu.
- Metode dapat memiliki tipe kembalian dan parameter.
- **Overloading** memungkinkan kita untuk membuat beberapa metode dengan nama yang sama tetapi parameter yang berbeda.
- **Rekursi** adalah teknik di mana metode memanggil dirinya sendiri untuk menyelesaikan masalah.

Dengan memahami konsep-konsep dasar tentang metode, kamu bisa mengorganisir kode dengan lebih baik dan membuat program yang lebih modular dan efisien.

---

> 🚀 Next: [05 - Kelas dan Objek dalam Java](05-kelas-dan-objek-dalam-java.md)
```

---

Materi ini memberikan pemahaman dasar mengenai fungsi atau metode di Java, termasuk penjelasan tentang struktur, parameter, overloading, dan rekursi, yang sangat penting untuk pemula. Jika ada yang perlu ditambahkan atau pertanyaan lainnya, saya siap membantu!