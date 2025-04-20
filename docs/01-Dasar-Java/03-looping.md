# 🧠 Perulangan (Looping) dalam Java

Perulangan (looping) adalah salah satu konsep dasar dalam pemrograman yang memungkinkan kita untuk mengeksekusi suatu blok kode secara berulang. Dalam Java, terdapat beberapa jenis perulangan yang dapat digunakan, antara lain `for`, `while`, dan `do-while`. Perulangan sangat berguna ketika kamu ingin melakukan tugas yang sama berulang kali tanpa menulis kode yang sama berulang-ulang.

---

## 📌 Jenis-jenis Perulangan di Java

1. **Perulangan For**
2. **Perulangan While**
3. **Perulangan Do-While**

---

## 📌 Perulangan `for`

Perulangan `for` digunakan ketika jumlah iterasi atau perulangan sudah diketahui sebelumnya. Struktur umumnya adalah sebagai berikut:

```java
for (inisialisasi; kondisi; perubahan) {
    // kode yang dijalankan selama kondisi bernilai true
}
```

### Contoh:

```java
for (int i = 0; i < 5; i++) {
    System.out.println("Perulangan ke-" + i);
}
```

**Penjelasan:**
- `int i = 0`: Inisialisasi, mendeklarasikan dan memberi nilai awal untuk variabel `i`.
- `i < 5`: Kondisi, perulangan terus berjalan selama `i` kurang dari 5.
- `i++`: Perubahan, setelah setiap iterasi, nilai `i` akan bertambah 1.

Output yang dihasilkan dari kode ini adalah:
```
Perulangan ke-0
Perulangan ke-1
Perulangan ke-2
Perulangan ke-3
Perulangan ke-4
```

---

## 📌 Perulangan `while`

Perulangan `while` digunakan ketika jumlah iterasi belum diketahui, tetapi perulangan dilakukan selama kondisi tertentu bernilai true.

Struktur umum perulangan `while` adalah sebagai berikut:

```java
while (kondisi) {
    // kode yang dijalankan selama kondisi bernilai true
}
```

### Contoh:

```java
int i = 0;
while (i < 5) {
    System.out.println("Perulangan ke-" + i);
    i++;
}
```

**Penjelasan:**
- Program akan terus melakukan perulangan selama `i` kurang dari 5.
- Setelah setiap iterasi, nilai `i` akan bertambah 1.

Output yang dihasilkan sama dengan perulangan `for`:
```
Perulangan ke-0
Perulangan ke-1
Perulangan ke-2
Perulangan ke-3
Perulangan ke-4
```

---

## 📌 Perulangan `do-while`

Perulangan `do-while` mirip dengan perulangan `while`, tetapi dengan perbedaan penting: kondisi diperiksa setelah blok kode dijalankan, sehingga perulangan akan selalu terjadi setidaknya sekali.

Struktur umum perulangan `do-while` adalah sebagai berikut:

```java
do {
    // kode yang dijalankan
} while (kondisi);
```

### Contoh:

```java
int i = 0;
do {
    System.out.println("Perulangan ke-" + i);
    i++;
} while (i < 5);
```

**Penjelasan:**
- Blok kode di dalam `do` akan dijalankan terlebih dahulu, kemudian kondisi pada `while` diperiksa.
- Jika kondisi `i < 5` masih true, perulangan akan dilanjutkan.

Output yang dihasilkan sama dengan perulangan `for` dan `while`:
```
Perulangan ke-0
Perulangan ke-1
Perulangan ke-2
Perulangan ke-3
Perulangan ke-4
```

---

## 📌 Penggunaan `break` dan `continue` dalam Perulangan

### `break`

Pernyataan `break` digunakan untuk menghentikan perulangan sebelum kondisi perulangan tersebut menjadi false.

### Contoh:

```java
for (int i = 0; i < 5; i++) {
    if (i == 3) {
        break;
    }
    System.out.println("Perulangan ke-" + i);
}
```

**Output:**
```
Perulangan ke-0
Perulangan ke-1
Perulangan ke-2
```

Perulangan berhenti ketika `i == 3` meskipun kondisi `i < 5` masih true.

### `continue`

Pernyataan `continue` digunakan untuk melewatkan iterasi saat ini dan melanjutkan ke iterasi berikutnya.

### Contoh:

```java
for (int i = 0; i < 5; i++) {
    if (i == 3) {
        continue;
    }
    System.out.println("Perulangan ke-" + i);
}
```

**Output:**
```
Perulangan ke-0
Perulangan ke-1
Perulangan ke-2
Perulangan ke-4
```

Perulangan ke-3 dilewatkan karena pernyataan `continue` dipanggil ketika `i == 3`.

---

## 📌 Latihan

1. Buat program yang menggunakan perulangan `for` untuk mencetak angka dari 1 hingga 10.
2. Buat program yang menggunakan perulangan `while` untuk menghitung jumlah angka dari 1 hingga 100.
3. Buat program yang menggunakan perulangan `do-while` untuk mencetak angka genap antara 1 hingga 20.
4. Tambahkan penggunaan `break` dalam salah satu perulangan untuk menghentikan perulangan lebih awal.
5. Tambahkan penggunaan `continue` dalam salah satu perulangan untuk melewatkan angka tertentu.

---

## 🎯 Kesimpulan

- Perulangan `for` digunakan ketika jumlah iterasi sudah diketahui sebelumnya.
- Perulangan `while` digunakan ketika jumlah iterasi belum diketahui dan perulangan bergantung pada kondisi tertentu.
- Perulangan `do-while` digunakan ketika perulangan harus dijalankan setidaknya satu kali, meskipun kondisi awal bernilai false.
- `break` dan `continue` adalah pernyataan yang digunakan untuk mengontrol jalannya perulangan.

Perulangan adalah konsep yang sangat penting dalam pemrograman karena memungkinkan kita untuk mengulang suatu tindakan secara efisien.

---

> 🚀 Next: [04 - Fungsi dan Metode dalam Java](04-fungsi-metode-dalam-java.md)
```

---

Materi ini memberikan penjelasan tentang berbagai jenis perulangan di Java, lengkap dengan contoh kode dan penjelasan. Pemahaman tentang perulangan sangat penting untuk pengembangan program yang efisien dan dinamis.
