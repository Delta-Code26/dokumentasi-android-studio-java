# 🧠 Polymorphism dalam OOP (Pemrograman Berorientasi Objek) di Java

**Polymorphism** adalah salah satu prinsip dasar dalam **Pemrograman Berorientasi Objek (OOP)** yang memungkinkan objek untuk memiliki banyak bentuk. Dalam konteks Java, polymorphism memungkinkan satu metode atau objek untuk berperilaku berbeda tergantung pada konteks penggunaannya.

Secara sederhana, polymorphism memungkinkan kita untuk **menggunakan satu antarmuka (interface)** untuk merepresentasikan banyak tipe objek yang berbeda. Ini memberikan fleksibilitas dalam pengembangan aplikasi dengan memungkinkan penggunaan metode atau objek yang sama dengan cara yang berbeda.

---

## 📌 Apa Itu Polymorphism?

Polymorphism terdiri dari dua jenis utama dalam Java:
1. **Compile-Time Polymorphism (Method Overloading)**: Terjadi saat waktu kompilasi dan melibatkan overloading metode.
2. **Runtime Polymorphism (Method Overriding)**: Terjadi saat waktu eksekusi dan melibatkan overriding metode di kelas turunan.

---

## 📌 Compile-Time Polymorphism (Method Overloading)

**Method Overloading** adalah bentuk polymorphism yang terjadi saat kompilasi. Ini terjadi ketika kita memiliki beberapa metode dengan nama yang sama tetapi dengan parameter yang berbeda (baik dalam jumlah atau tipe parameter).

### Contoh Kode Overloading:

```java
class Kalkulator {

    // Overloading metode jumlah dengan dua parameter
    public int jumlah(int a, int b) {
        return a + b;
    }

    // Overloading metode jumlah dengan tiga parameter
    public int jumlah(int a, int b, int c) {
        return a + b + c;
    }

    // Overloading metode jumlah dengan dua parameter bertipe double
    public double jumlah(double a, double b) {
        return a + b;
    }
}

public class Main {
    public static void main(String[] args) {
        Kalkulator kalkulator = new Kalkulator();
        
        System.out.println("Jumlah 2 angka (int): " + kalkulator.jumlah(5, 10));        // Output: 15
        System.out.println("Jumlah 3 angka (int): " + kalkulator.jumlah(5, 10, 15));    // Output: 30
        System.out.println("Jumlah 2 angka (double): " + kalkulator.jumlah(5.5, 10.5)); // Output: 16.0
    }
}
```

### Penjelasan:
- **Method Overloading** terjadi saat waktu kompilasi, ketika kita memiliki beberapa metode dengan nama yang sama tetapi parameter yang berbeda.
- Pada contoh di atas, metode `jumlah()` di kelas `Kalkulator` di-overload dengan dua, tiga, dan dua parameter bertipe `double`. 

---

## 📌 Runtime Polymorphism (Method Overriding)

**Method Overriding** adalah bentuk polymorphism yang terjadi saat eksekusi. Ini terjadi ketika kelas turunan memberikan implementasi baru untuk metode yang sudah ada di kelas induk. Dengan demikian, objek dari kelas turunan dapat memanggil metode yang di-override, meskipun metode tersebut didefinisikan di kelas induk.

### Contoh Kode Overriding:

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
        Hewan hewan1 = new Anjing();  // Objek Anjing
        Hewan hewan2 = new Kucing();  // Objek Kucing

        // Memanggil metode suara untuk objek yang berbeda
        hewan1.suara();  // Output: Anjing menggonggong.
        hewan2.suara();  // Output: Kucing mengeong.
    }
}
```

### Penjelasan:
- **Method Overriding** memungkinkan kelas turunan untuk memberikan implementasi baru untuk metode yang sudah ada di kelas induk.
- Dalam contoh di atas, kelas `Anjing` dan `Kucing` meng-override metode `suara()` yang didefinisikan di kelas `Hewan`. Meskipun objek `hewan1` dan `hewan2` bertipe `Hewan`, mereka memanggil implementasi yang berbeda dari metode `suara()` sesuai dengan tipe objek mereka (Anjing atau Kucing).

---

## 📌 Polymorphism dengan Objek Kelas Induk

Salah satu fitur kuat dari polymorphism adalah kemampuan untuk menggunakan referensi kelas induk untuk objek kelas turunan. Ini memungkinkan kita untuk menulis kode yang lebih fleksibel dan generik.

### Contoh Kode:

```java
class Hewan {
    public void suara() {
        System.out.println("Hewan ini bersuara.");
    }
}

class Anjing extends Hewan {
    @Override
    public void suara() {
        System.out.println("Anjing menggonggong.");
    }
}

class Kucing extends Hewan {
    @Override
    public void suara() {
        System.out.println("Kucing mengeong.");
    }
}

public class Main {
    public static void main(String[] args) {
        Hewan hewan = new Hewan();     // Objek Hewan
        hewan.suara();                 // Output: Hewan ini bersuara.

        hewan = new Anjing();          // Objek Anjing
        hewan.suara();                 // Output: Anjing menggonggong.

        hewan = new Kucing();          // Objek Kucing
        hewan.suara();                 // Output: Kucing mengeong.
    }
}
```

### Penjelasan:
- Dalam contoh di atas, referensi `Hewan hewan` digunakan untuk merujuk ke objek dari kelas `Hewan`, `Anjing`, dan `Kucing`.
- Saat objek dari kelas turunan dipanggil melalui referensi kelas induk, metode yang sesuai dengan objek yang sebenarnya akan dipanggil (metode yang di-override).

---

## 📌 Manfaat Polymorphism

1. **Flexibilitas dan Reusability**: Polymorphism memungkinkan kita untuk menulis kode yang lebih fleksibel dan reusable karena kita dapat menggunakan referensi kelas induk untuk merujuk ke objek kelas turunan.
2. **Pengurangan Kode Duplikat**: Dengan polymorphism, kita dapat mengurangi duplikasi kode, karena kita dapat menggunakan metode yang sama untuk objek yang berbeda.
3. **Pengembangan yang Lebih Mudah**: Polymorphism membuat pengembangan dan pemeliharaan aplikasi lebih mudah, karena kita bisa menambah fitur baru tanpa perlu mengubah banyak kode yang sudah ada.

---

## 📌 Polymorphism dengan Interface

Polymorphism juga dapat digunakan dengan **interface** untuk mencapai hasil yang lebih fleksibel dan berbasis kontrak.

### Contoh Kode dengan Interface:

```java
// Interface Hewan
interface Hewan {
    void suara();
}

// Kelas Anjing mengimplementasikan interface Hewan
class Anjing implements Hewan {
    @Override
    public void suara() {
        System.out.println("Anjing menggonggong.");
    }
}

// Kelas Kucing mengimplementasikan interface Hewan
class Kucing implements Hewan {
    @Override
    public void suara() {
        System.out.println("Kucing mengeong.");
    }
}

public class Main {
    public static void main(String[] args) {
        Hewan hewan1 = new Anjing();  // Objek Anjing
        Hewan hewan2 = new Kucing();  // Objek Kucing

        hewan1.suara();  // Output: Anjing menggonggong.
        hewan2.suara();  // Output: Kucing mengeong.
    }
}
```

### Penjelasan:
- Interface `Hewan` mendefinisikan metode `suara()`, yang diimplementasikan oleh kelas `Anjing` dan `Kucing`.
- Polymorphism dengan interface memungkinkan kita untuk menggunakan referensi dari jenis interface untuk objek yang mengimplementasikan interface tersebut.

---

## 🎯 Kesimpulan

- **Polymorphism** memungkinkan kita untuk menggunakan satu antarmuka (metode atau objek) untuk berbagai tipe objek yang berbeda, meningkatkan fleksibilitas dan reusability kode.
- Polymorphism terdiri dari dua jenis: **method overloading** (compile-time polymorphism) dan **method overriding** (runtime polymorphism).
- Polymorphism memungkinkan kita untuk mengurangi duplikasi kode dan membuat aplikasi lebih modular, fleksibel, dan mudah dikembangkan.

---

> 🚀 Next: [07 - Interfaces dalam Java](07-interfaces-dalam-java.md)
