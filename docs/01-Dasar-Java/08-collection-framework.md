# 🧠 Collection Framework dalam Java

**Collection Framework** di Java menyediakan struktur data yang digunakan untuk menyimpan, mengelola, dan memanipulasi kumpulan objek. Framework ini memberikan berbagai kelas dan antarmuka untuk bekerja dengan data dalam bentuk yang lebih fleksibel, efisien, dan terstruktur. Dengan menggunakan Collection Framework, kita bisa menangani elemen-elemen data secara dinamis, dan dapat menambah, menghapus, dan mengakses data dengan cara yang lebih terorganisir.

---

## 📌 Apa Itu Collection Framework?

Collection Framework di Java terdiri dari tiga bagian utama:

1. **Collection Interface**: Antarmuka dasar untuk bekerja dengan kumpulan data.
2. **Implementasi Collection**: Kelas yang mengimplementasikan antarmuka Collection untuk berbagai jenis struktur data.
3. **Algoritma**: Metode-metode yang beroperasi pada struktur data seperti sorting, searching, dll.

---

## 📌 Struktur Collection Framework

Collection Framework terdiri dari dua kategori utama:

1. **Collection**: Mengelola kumpulan objek yang tidak berhubungan dengan posisi (seperti **List**, **Set**, dan **Queue**).
   - **List**: Mengelola elemen-elemen yang terurut dan memungkinkan elemen duplikat. Contoh: `ArrayList`, `LinkedList`.
   - **Set**: Mengelola elemen yang tidak terurut dan tidak mendukung duplikasi. Contoh: `HashSet`, `TreeSet`.
   - **Queue**: Mengelola elemen-elemen yang diatur dalam urutan tertentu, biasanya digunakan untuk antrean. Contoh: `PriorityQueue`, `LinkedList`.

2. **Map**: Mengelola data dalam pasangan **key-value** (kunci-nilai). Contoh: `HashMap`, `TreeMap`.

---

## 📌 Antarmuka Collection

Antarmuka utama yang mendefinisikan struktur data dalam Collection Framework adalah `Collection` dan `Map`.

### 1. **Collection Interface**

Antarmuka `Collection` adalah dasar untuk semua koleksi yang ada dalam Collection Framework. Kelas-kelas seperti `List`, `Set`, dan `Queue` mengimplementasikan antarmuka ini.

#### Beberapa metode utama dalam `Collection`:

- `add(E e)`: Menambahkan elemen ke koleksi.
- `remove(Object o)`: Menghapus elemen dari koleksi.
- `size()`: Mengembalikan jumlah elemen dalam koleksi.
- `clear()`: Menghapus semua elemen dari koleksi.
- `contains(Object o)`: Memeriksa apakah elemen ada dalam koleksi.

### 2. **Map Interface**

Antarmuka `Map` digunakan untuk mengelola pasangan kunci-nilai. Berbeda dengan koleksi lain, `Map` tidak mengimplementasikan antarmuka `Collection`, tetapi koleksi ini sering digunakan bersama.

#### Beberapa metode utama dalam `Map`:

- `put(K key, V value)`: Menambahkan pasangan kunci-nilai.
- `get(Object key)`: Mengambil nilai berdasarkan kunci.
- `remove(Object key)`: Menghapus pasangan berdasarkan kunci.
- `size()`: Mengembalikan jumlah pasangan kunci-nilai.
- `containsKey(Object key)`: Memeriksa apakah kunci ada dalam peta.

---

## 📌 Jenis-Jenis Collection dalam Java

### 1. **List**

`List` adalah jenis koleksi yang mempertahankan urutan elemen dan memungkinkan duplikasi elemen.

#### Contoh Kelas yang Mengimplementasikan `List`:
- `ArrayList`: Implementasi yang berbasis array dinamis.
- `LinkedList`: Implementasi yang berbasis struktur data linked list.
- `Vector`: Implementasi yang berbasis array yang dapat menyesuaikan ukuran secara otomatis.

#### Contoh Penggunaan `ArrayList`:

```java
import java.util.ArrayList;

public class Main {
    public static void main(String[] args) {
        ArrayList<String> list = new ArrayList<>();
        list.add("Java");
        list.add("Kotlin");
        list.add("Python");

        System.out.println("List: " + list);
    }
}
```

### 2. **Set**

`Set` adalah jenis koleksi yang tidak mengizinkan elemen duplikat dan tidak mempertahankan urutan elemen.

#### Contoh Kelas yang Mengimplementasikan `Set`:
- `HashSet`: Implementasi yang berbasis hashing untuk pencarian cepat.
- `LinkedHashSet`: Implementasi yang mempertahankan urutan elemen yang dimasukkan.
- `TreeSet`: Implementasi yang mengurutkan elemen-elemen secara otomatis.

#### Contoh Penggunaan `HashSet`:

```java
import java.util.HashSet;

public class Main {
    public static void main(String[] args) {
        HashSet<String> set = new HashSet<>();
        set.add("Java");
        set.add("Kotlin");
        set.add("Python");
        set.add("Java");  // Elemen duplikat, akan diabaikan

        System.out.println("Set: " + set);
    }
}
```

### 3. **Queue**

`Queue` adalah jenis koleksi yang digunakan untuk menangani elemen-elemen dalam urutan tertentu, seperti antrean.

#### Contoh Kelas yang Mengimplementasikan `Queue`:
- `LinkedList`: Digunakan baik untuk `List` maupun `Queue`.
- `PriorityQueue`: Digunakan untuk elemen yang dikelola dengan prioritas.

#### Contoh Penggunaan `LinkedList` sebagai Queue:

```java
import java.util.LinkedList;
import java.util.Queue;

public class Main {
    public static void main(String[] args) {
        Queue<String> queue = new LinkedList<>();
        queue.add("Java");
        queue.add("Kotlin");
        queue.add("Python");

        System.out.println("Queue: " + queue);
        queue.poll();  // Mengambil elemen pertama (Java)
        System.out.println("Queue setelah poll: " + queue);
    }
}
```

---

## 📌 Jenis-Jenis Map dalam Java

### 1. **HashMap**

`HashMap` adalah implementasi dasar dari antarmuka `Map` yang mengelola pasangan kunci-nilai. Elemen-elemen dalam `HashMap` tidak terurut.

#### Contoh Penggunaan `HashMap`:

```java
import java.util.HashMap;

public class Main {
    public static void main(String[] args) {
        HashMap<String, String> map = new HashMap<>();
        map.put("Nama", "John");
        map.put("Pekerjaan", "Developer");
        map.put("Kota", "Jakarta");

        System.out.println("Map: " + map);
    }
}
```

### 2. **TreeMap**

`TreeMap` adalah implementasi dari antarmuka `Map` yang mengurutkan pasangan kunci-nilai berdasarkan kunci.

#### Contoh Penggunaan `TreeMap`:

```java
import java.util.TreeMap;

public class Main {
    public static void main(String[] args) {
        TreeMap<Integer, String> map = new TreeMap<>();
        map.put(3, "Tiga");
        map.put(1, "Satu");
        map.put(2, "Dua");

        System.out.println("TreeMap: " + map);  // Diurutkan berdasarkan kunci
    }
}
```

---

## 📌 Algoritma dalam Collection Framework

Collection Framework menyediakan berbagai algoritma yang dapat digunakan untuk memanipulasi koleksi, seperti:

- **Sorting**: Mengurutkan elemen dalam koleksi.
- **Searching**: Mencari elemen dalam koleksi.
- **Shuffling**: Mengacak urutan elemen dalam koleksi.

Contoh penggunaan sorting menggunakan `Collections.sort()`:

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        List<Integer> list = new ArrayList<>();
        list.add(5);
        list.add(2);
        list.add(9);
        list.add(1);

        Collections.sort(list);  // Mengurutkan elemen

        System.out.println("List setelah diurutkan: " + list);
    }
}
```

---

## 🎯 Kesimpulan

- **Collection Framework** di Java menyediakan struktur data untuk menyimpan, mengelola, dan memanipulasi data secara efisien.
- Framework ini terdiri dari berbagai jenis koleksi seperti **List**, **Set**, **Queue**, dan **Map**, masing-masing dengan karakteristik dan kegunaan yang berbeda.
- `List` digunakan untuk elemen yang terurut dan mendukung duplikasi, `Set` untuk elemen yang tidak terurut dan tidak mendukung duplikasi, dan `Queue` untuk elemen yang diatur dalam antrean.
- `Map` digunakan untuk mengelola pasangan kunci-nilai.
- Java juga menyediakan algoritma untuk mengurutkan, mencari, dan mengacak elemen dalam koleksi.

---

> 🚀 Next: [09 - Threading dan Concurrency dalam Java](09-threading-dan-concurrency-dalam-java.md)