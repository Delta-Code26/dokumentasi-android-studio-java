# 🧠 Dasar Sintaks Java

Selamat datang di dunia pemrograman Java! Di bagian ini, kita akan belajar tentang **sintaks dasar Java**. Kalau kamu belum pernah ngoding Java sebelumnya, don't worry — kita mulai dari nol!

---

## ✍️ Struktur Dasar Program Java

Setiap program Java **wajib** punya struktur seperti ini:

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Halo, dunia!");
    }
}
```

### Penjelasan:

| Bagian | Penjelasan |
|-------|------------|
| `public class HelloWorld` | Mendeklarasikan class dengan nama `HelloWorld`. Java adalah bahasa yang berbasis class. |
| `public static void main(String[] args)` | Titik awal (entry point) dari program Java. Tanpa ini, program tidak akan jalan. |
| `System.out.println(...)` | Fungsi untuk mencetak output ke layar. |

---

## 📌 Aturan Sintaks Java

- **Case Sensitive**: `MyClass` dan `myclass` dianggap beda.
- **Setiap statement diakhiri `;`**
- Nama file **harus sama** dengan nama class publik (`public class`).
- Struktur kode dibagi dalam **class → method → statement**.

---

## 🔤 Variabel dan Tipe Data

Contoh deklarasi variabel:

```java
int umur = 20;
String nama = "Andi";
boolean aktif = true;
```

### Tipe Data Umum:

| Tipe | Contoh | Keterangan |
|------|--------|------------|
| `int` | 10 | Bilangan bulat |
| `double` | 3.14 | Bilangan desimal |
| `boolean` | true/false | Nilai logika |
| `char` | 'A' | Karakter |
| `String` | "Halo" | Teks (objek) |

---

## 🔁 Kontrol Alur: IF dan LOOP

### IF Statement:

```java
int nilai = 80;

if (nilai >= 75) {
    System.out.println("Lulus!");
} else {
    System.out.println("Gagal!");
}
```

### FOR Loop:

```java
for (int i = 0; i < 5; i++) {
    System.out.println("Perulangan ke-" + i);
}
```

### WHILE Loop:

```java
int i = 0;
while (i < 5) {
    System.out.println("Nilai: " + i);
    i++;
}
```

---

## 🔧 Fungsi / Method

Fungsi mempermudah kamu buat menulis kode yang bisa digunakan ulang.

```java
public static void halo(String nama) {
    System.out.println("Halo, " + nama);
}
```

Pemanggilan fungsi:

```java
halo("Andi");
```

---

## 📦 Komentar

Komentar tidak dijalankan oleh program, tapi penting buat dokumentasi.

```java
// Ini komentar satu baris

/*
   Ini komentar
   multi baris
*/
```

---

## 🧪 Latihan

Coba buat program sederhana yang menampilkan:

- Nama kamu
- Umur
- Apakah kamu mahasiswa (true/false)
- Cetak “Lulus” jika nilai >= 70, else cetak “Remedial”

---

## 🎯 Kesimpulan

- Java butuh struktur class dan method utama (`main`).
- Sintaks Java sangat ketat dan **case-sensitive**.
- Kenali tipe data dan alur kontrol seperti `if`, `for`, `while`.
- Komentar penting untuk dokumentasi.

Kalau kamu udah paham bagian ini, kamu udah punya pondasi yang kuat untuk lanjut ke bab-bab berikutnya!

---

> 🚀 Next: [02 - Variabel dan Operator](02-variabel-dan-operator.md)
