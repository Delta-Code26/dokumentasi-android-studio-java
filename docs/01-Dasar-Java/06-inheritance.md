# 🧠 Inheritance dalam OOP (Pemrograman Berorientasi Objek) di Java

**Inheritance** (pewarisan) adalah konsep dalam **Pemrograman Berorientasi Objek (OOP)** yang memungkinkan sebuah kelas untuk mewarisi sifat-sifat (method dan variabel) dari kelas lain. Konsep ini mendukung prinsip **reuse** (penggunaan kembali) kode dan memungkinkan pengembangan aplikasi yang lebih modular dan terstruktur.

Dengan **inheritance**, kita dapat membuat kelas baru (kelas **turunan**) yang mewarisi atribut dan perilaku dari kelas yang sudah ada (kelas **induk**).

---

## 📌 Apa Itu Inheritance?

Inheritance memungkinkan kita untuk membuat kelas yang lebih spesifik yang berbagi atribut dan perilaku dari kelas umum. Kelas turunan akan mendapatkan **semua properti** dan **metode** dari kelas induk, namun kita juga dapat menambahkan atau memodifikasi perilaku tertentu.

### Contoh Dunia Nyata:
Bayangkan Anda memiliki dua jenis kendaraan: **Mobil** dan **Motor**. Kedua kendaraan ini memiliki beberapa kesamaan seperti **roda** dan **mesin**. Anda dapat membuat kelas **Kendaraan** yang berisi atribut umum, dan kemudian kelas **Mobil** dan **Motor** akan mewarisi kelas **Kendaraan** untuk mendapatkan properti dan perilaku umum tersebut, tetapi dengan tambahan spesifik untuk setiap jenis kendaraan.

---

## 📌 Cara Mengimplementasikan Inheritance di Java

### Langkah 1: Membuat Kelas Induk (Super Class)

Kelas induk adalah kelas yang berisi properti dan metode umum yang ingin diwariskan ke kelas turunan.

### Langkah 2: Membuat Kelas Turunan (Sub Class)

Kelas turunan akan menggunakan keyword `extends` untuk mewarisi kelas induk. Kelas turunan dapat menambahkan atribut atau metode tambahan, atau menimpa (override) metode yang diwarisi dari kelas induk.

---

## 📌 Contoh Kode Inheritance

Berikut adalah contoh sederhana untuk mengimplementasikan inheritance di Java:

### Contoh Kode:

```java
// Kelas Induk (Super Class)
class Kendaraan {
    // Variabel umum
    String merk;
    int tahun;

    // Konstruktor kelas induk
    public Kendaraan(String merk, int tahun) {
        this.merk = merk;
        this.tahun = tahun;
    }

    // Metode umum
    public void bergerak() {
        System.out.println("Kendaraan ini bergerak.");
    }

    public void informasi() {
        System.out.println("Merk: " + merk + ", Tahun: " + tahun);
    }
}

// Kelas Turunan (Sub Class)
class Mobil extends Kendaraan {
    // Variabel spesifik untuk Mobil
    int jumlahPintu;

    // Konstruktor kelas turunan
    public Mobil(String merk, int tahun, int jumlahPintu) {
        super(merk, tahun); // Memanggil konstruktor kelas induk
        this.jumlahPintu = jumlahPintu;
    }

    // Menambahkan metode spesifik untuk Mobil
    public void honk() {
        System.out.println("Mobil ini membunyikan klakson.");
    }

    // Overriding metode informasi dari kelas induk
    @Override
    public void informasi() {
        super.informasi(); // Memanggil informasi dari kelas induk
        System.out.println("Jumlah Pintu: " + jumlahPintu);
    }
}

public class Main {
    public static void main(String[] args) {
        // Membuat objek dari kelas turunan Mobil
        Mobil mobil = new Mobil("Toyota", 2021, 4);
        
        // Memanggil metode dari kelas induk
        mobil.informasi();
        mobil.bergerak();
        mobil.honk();
    }
}
```

### Penjelasan:
- **Kelas `Kendaraan`** adalah kelas induk yang memiliki variabel `merk` dan `tahun`, serta metode `bergerak()` dan `informasi()`.
- **Kelas `Mobil`** adalah kelas turunan yang mewarisi kelas `Kendaraan`. Kelas `Mobil` menambahkan variabel `jumlahPintu` dan metode `honk()`. Kelas `Mobil` juga melakukan **overriding** pada metode `informasi()` untuk menambahkan detail tentang jumlah pintu.
- **Keyword `super`** digunakan untuk memanggil konstruktor dan metode dari kelas induk.

---

## 📌 Pewarisan Berlapis

Java juga mendukung pewarisan berlapis (multiple inheritance) dalam hal implementasi interface. Namun, Java tidak mendukung pewarisan berlapis untuk kelas biasa (class). Artinya, sebuah kelas hanya dapat mewarisi satu kelas induk (single inheritance).

---

## 📌 Menggunakan `super` dalam Inheritance

Keyword `super` memiliki dua fungsi utama dalam inheritance:

1. **Memanggil Konstruktor Kelas Induk**: Menggunakan `super()` di dalam konstruktor kelas turunan untuk memanggil konstruktor dari kelas induk.
2. **Memanggil Metode Kelas Induk**: Menggunakan `super.metode()` untuk memanggil metode yang ada di kelas induk, meskipun metode tersebut telah dioverride di kelas turunan.

---

## 📌 Overriding dan Overloading dalam Inheritance

- **Method Overriding**: Metode dalam kelas turunan yang menggantikan (menimpa) metode yang ada di kelas induk dengan implementasi yang baru.
  
  Contoh:
  
  ```java
  @Override
  public void bergerak() {
      System.out.println("Mobil ini berjalan di jalan raya.");
  }
  ```

- **Method Overloading**: Menambahkan metode dengan nama yang sama, namun dengan parameter yang berbeda. Overloading bukan bagian dari inheritance, tetapi dapat digunakan dalam kelas turunan untuk variasi metode.

---

## 📌 Manfaat Inheritance

1. **Reusability**: Dengan inheritance, kita dapat menggunakan kembali kode yang sudah ada tanpa menulis ulang kode yang sama.
2. **Modularitas**: Kode menjadi lebih terstruktur dan mudah untuk dikelola, karena kelas turunan mewarisi sifat dari kelas induk.
3. **Pemeliharaan yang Lebih Mudah**: Jika ada perubahan dalam kelas induk, perubahan tersebut akan otomatis tercermin pada kelas turunan.
4. **Polymorphism**: Inheritance memungkinkan konsep **polymorphism**, di mana objek dari kelas turunan dapat diperlakukan sebagai objek dari kelas induk.

---

## 📌 Contoh Lain Penggunaan Inheritance

Berikut adalah contoh lain yang lebih kompleks tentang pewarisan antara berbagai jenis hewan:

### Contoh Kode:

```java
// Kelas Induk
class Hewan {
    public void suara() {
        System.out.println("Hewan ini bersuara.");
    }
}

// Kelas Turunan
class Anjing extends Hewan {
    @Override
    public void suara() {
        System.out.println("Anjing menggonggong.");
    }
}

// Kelas Turunan
class Kucing extends Hewan {
    @Override
    public void suara() {
        System.out.println("Kucing mengeong.");
    }
}

public class Main {
    public static void main(String[] args) {
        Hewan hewan1 = new Anjing();
        Hewan hewan2 = new Kucing();

        // Memanggil metode suara untuk objek yang berbeda
        hewan1.suara();  // Output: Anjing menggonggong.
        hewan2.suara();  // Output: Kucing mengeong.
    }
}
```

### Penjelasan:
- Kelas **Hewan** adalah kelas induk dengan metode `suara()`.
- Kelas **Anjing** dan **Kucing** adalah kelas turunan yang meng-override metode `suara()` untuk memberikan implementasi masing-masing.
- Polymorphism memungkinkan kita untuk menggunakan referensi kelas induk untuk objek kelas turunan.

---

## 🎯 Kesimpulan

- **Inheritance** memungkinkan sebuah kelas untuk mewarisi atribut dan metode dari kelas lain, yang meningkatkan **reuse** dan **modularitas** kode.
- Dengan menggunakan keyword `extends`, kelas turunan dapat mewarisi semua metode dan variabel dari kelas induk, dan dapat **meng-overload** atau **meng-overriding** metode sesuai kebutuhan.
- Konsep ini memungkinkan pembuatan kode yang lebih efisien, mudah dipelihara, dan lebih mudah dikembangkan.

---

> 🚀 Next: [07 - Polymorphism dalam Java](07-polymorphism-dalam-java.md)
```

---

Materi ini menjelaskan konsep **Inheritance** dalam Pemrograman Berorientasi Objek di Java, serta contoh penerapannya dengan berbagai kelas dan metode. Jika ada yang perlu disesuaikan atau ditambahkan, beri tahu saya!