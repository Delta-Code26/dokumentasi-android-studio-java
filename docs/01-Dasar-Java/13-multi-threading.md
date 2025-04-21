# 13. Multithreading di Java

## Apa Itu Multithreading?

Multithreading adalah kemampuan untuk menjalankan lebih dari satu thread secara bersamaan dalam satu aplikasi. Setiap thread berfungsi sebagai unit eksekusi yang terpisah dan dapat bekerja secara independen, yang memungkinkan aplikasi untuk melakukan beberapa tugas secara bersamaan. Konsep ini sangat penting dalam pengembangan aplikasi yang membutuhkan performa tinggi dan pengolahan data secara paralel.

Java memiliki dukungan kuat untuk multithreading dan memungkinkan programmer untuk mengelola banyak thread dalam aplikasi mereka dengan mudah. Dalam Java, sebuah thread adalah entitas yang menjalankan blok kode secara independen.

## Mengapa Multithreading Diperlukan?

Multithreading memiliki banyak keuntungan, di antaranya:
- **Efisiensi**: Dengan membagi pekerjaan ke dalam beberapa thread, kita bisa memanfaatkan waktu CPU lebih efektif, terutama pada perangkat dengan banyak core CPU.
- **Responsivitas**: Dalam aplikasi GUI atau aplikasi berbasis jaringan, multithreading memungkinkan antarmuka pengguna tetap responsif meskipun ada proses berat yang berjalan di latar belakang.
- **Pemrosesan Paralel**: Multithreading memungkinkan pemrosesan paralel, yang sangat penting untuk aplikasi yang melakukan perhitungan besar atau mengolah banyak data.

## Dasar-Dasar Thread di Java

### Membuat Thread

Ada dua cara utama untuk membuat dan menjalankan thread di Java:
1. **Dengan mewarisi kelas `Thread`**.
2. **Dengan mengimplementasikan interface `Runnable`**.

### 1. Menggunakan Kelas `Thread`

```java
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread berjalan...");
    }
}

public class Main {
    public static void main(String[] args) {
        MyThread thread = new MyThread();
        thread.start(); // Menjalankan thread
    }
}
```

Pada contoh di atas, kelas `MyThread` mewarisi kelas `Thread` dan meng-override method `run()` untuk menentukan tugas yang akan dijalankan oleh thread. Kemudian, kita memanggil method `start()` untuk menjalankan thread.

### 2. Menggunakan Interface `Runnable`

```java
class MyRunnable implements Runnable {
    public void run() {
        System.out.println("Thread berjalan...");
    }
}

public class Main {
    public static void main(String[] args) {
        MyRunnable myRunnable = new MyRunnable();
        Thread thread = new Thread(myRunnable);
        thread.start(); // Menjalankan thread
    }
}
```

Pada contoh ini, kita mengimplementasikan interface `Runnable` dan mendefinisikan method `run()`. Kemudian, kita buat objek `Thread` dan menjalankannya.

## Thread Lifecycle (Siklus Hidup Thread)

Thread memiliki beberapa status dalam siklus hidupnya:
1. **New**: Thread baru dibuat tetapi belum dijalankan.
2. **Runnable**: Thread siap untuk dijalankan oleh scheduler (scheduler akan memutuskan kapan thread dijalankan).
3. **Blocked**: Thread sedang menunggu untuk mendapatkan akses ke sumber daya yang diblokir oleh thread lain.
4. **Waiting**: Thread sedang menunggu kondisi tertentu sebelum melanjutkan eksekusi.
5. **Terminated**: Thread telah selesai menjalankan tugasnya.

### Contoh Siklus Hidup Thread

```java
class MyThread extends Thread {
    public void run() {
        try {
            System.out.println("Thread dimulai...");
            Thread.sleep(2000); // Menunggu selama 2 detik
            System.out.println("Thread selesai...");
        } catch (InterruptedException e) {
            System.out.println("Thread terinterupsi.");
        }
    }
}

public class Main {
    public static void main(String[] args) throws InterruptedException {
        MyThread thread = new MyThread();
        thread.start(); // Menjalankan thread

        // Thread utama menunggu thread selesai
        thread.join();  
        System.out.println("Thread utama selesai.");
    }
}
```

Pada contoh ini, thread utama menunggu thread `MyThread` selesai dengan menggunakan `join()`.

## Thread Synchronization

Ketika beberapa thread mengakses data atau sumber daya yang sama, terkadang mereka dapat mengubah data secara bersamaan yang dapat menyebabkan kondisi yang tidak diinginkan. Untuk itu, kita memerlukan **synchronization** agar hanya satu thread yang dapat mengakses data atau sumber daya pada waktu tertentu.

### Contoh Synchronization

```java
class Counter {
    private int count = 0;

    public synchronized void increment() {
        count++;
    }

    public int getCount() {
        return count;
    }
}

public class Main {
    public static void main(String[] args) throws InterruptedException {
        Counter counter = new Counter();

        // Membuat dua thread yang menjalankan tugas increment
        Thread thread1 = new Thread(() -> counter.increment());
        Thread thread2 = new Thread(() -> counter.increment());

        thread1.start();
        thread2.start();

        thread1.join();
        thread2.join();

        System.out.println("Counter: " + counter.getCount());
    }
}
```

Dengan menggunakan kata kunci `synchronized`, kita memastikan hanya satu thread yang dapat mengakses method `increment()` pada satu waktu.

## Executor Service

Daripada membuat thread secara manual, kita bisa menggunakan `ExecutorService` untuk mengelola thread dengan lebih mudah. `ExecutorService` memungkinkan kita untuk menggunakan thread pool (sekelompok thread yang siap digunakan) untuk mengeksekusi tugas-tugas dalam aplikasi.

### Menggunakan `ExecutorService`

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class Main {
    public static void main(String[] args) {
        ExecutorService executor = Executors.newFixedThreadPool(2);

        executor.submit(() -> {
            System.out.println("Task pertama berjalan...");
        });

        executor.submit(() -> {
            System.out.println("Task kedua berjalan...");
        });

        executor.shutdown(); // Menutup ExecutorService
    }
}
```

Pada contoh di atas, kita membuat thread pool dengan dua thread menggunakan `Executors.newFixedThreadPool(2)`, dan kemudian menjalankan beberapa tugas menggunakan `submit()`.

## Callable & Future

Terkadang, kita ingin thread mengembalikan hasil setelah selesai menjalankan tugas. Untuk itu, kita bisa menggunakan `Callable` dan `Future`.

### Menggunakan `Callable` dan `Future`

```java
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

public class Main {
    public static void main(String[] args) throws Exception {
        ExecutorService executor = Executors.newCachedThreadPool();

        Callable<Integer> task = () -> {
            return 10 + 20;
        };

        Future<Integer> future = executor.submit(task);

        Integer result = future.get(); // Mendapatkan hasil dari task
        System.out.println("Hasil: " + result);

        executor.shutdown();
    }
}
```

Pada contoh di atas, kita menggunakan `Callable` untuk tugas yang mengembalikan hasil dan `Future` untuk mendapatkan hasil dari thread setelah tugas selesai.

## Kesimpulan

Multithreading adalah fitur penting dalam pemrograman Java yang memungkinkan aplikasi untuk menjalankan banyak tugas secara bersamaan, meningkatkan performa dan responsivitas. Java menyediakan berbagai cara untuk mengelola thread, termasuk menggunakan kelas `Thread`, interface `Runnable`, `ExecutorService`, dan fitur lanjutan seperti `Callable` dan `Future`. Selain itu, kita juga perlu memikirkan penggunaan **synchronization** untuk menghindari masalah seperti race condition dan deadlock.

Memahami konsep dan implementasi multithreading akan sangat membantu dalam membangun aplikasi yang efisien dan dapat menangani banyak tugas secara bersamaan.
