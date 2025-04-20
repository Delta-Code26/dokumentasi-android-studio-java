# 12. Pemrograman Paralel (Concurrency) di Java

## Apa Itu Concurrency?

Concurrency atau pemrograman paralel adalah teknik yang digunakan untuk menjalankan beberapa tugas (tasks) secara bersamaan. Hal ini dapat membantu mempercepat proses dan membuat aplikasi lebih responsif, terutama dalam aplikasi yang membutuhkan banyak pengolahan data atau tugas yang memerlukan waktu lama. 

Di Java, concurrency memungkinkan kita untuk menjalankan beberapa thread secara bersamaan untuk meningkatkan performa aplikasi, menggunakan berbagai teknik, seperti **Thread**, **ExecutorService**, dan **ForkJoinPool**.

## Pentingnya Concurrency

Dengan semakin berkembangnya perangkat keras (hardware) yang memiliki banyak core CPU, kemampuan untuk menjalankan banyak thread secara paralel menjadi sangat penting. Dalam aplikasi yang membutuhkan performa tinggi (misalnya aplikasi yang memproses data besar atau melakukan penghitungan matematis kompleks), menggunakan concurrency dengan benar dapat mempercepat eksekusi aplikasi.

## Dasar-Dasar Thread di Java

Thread adalah unit terkecil dalam pemrograman paralel. Java menyediakan API yang memungkinkan pembuatan dan pengelolaan thread.

### Membuat dan Menjalankan Thread

Di Java, ada dua cara utama untuk membuat dan menjalankan thread:
1. **Mewarisi kelas `Thread`**.
2. **Mengimplementasikan interface `Runnable`**.

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

Pada contoh di atas, kita membuat kelas `MyThread` yang mewarisi kelas `Thread`, lalu meng-override method `run()` untuk mendefinisikan tugas yang dijalankan oleh thread tersebut. Method `start()` digunakan untuk menjalankan thread.

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

Di sini, kita mengimplementasikan interface `Runnable` dan menerapkan method `run()` untuk mendefinisikan tugas yang akan dijalankan oleh thread.

## Menunggu atau Menghentikan Thread

Thread dapat berhenti dengan beberapa cara, seperti melalui method `sleep()`, `join()`, atau dengan cara lain. Namun, berhati-hatilah saat menggunakan `stop()` karena dapat menyebabkan kondisi tidak stabil dalam program.

### Contoh `sleep()`:

```java
public class Main {
    public static void main(String[] args) throws InterruptedException {
        System.out.println("Thread dimulai");
        Thread.sleep(2000); // Thread akan tidur selama 2 detik
        System.out.println("Thread selesai tidur");
    }
}
```

### Contoh `join()`:

```java
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread berjalan...");
    }
}

public class Main {
    public static void main(String[] args) throws InterruptedException {
        MyThread thread = new MyThread();
        thread.start(); // Menjalankan thread
        thread.join();  // Menunggu thread selesai
        System.out.println("Thread selesai");
    }
}
```

Method `join()` digunakan untuk menunggu thread lain selesai sebelum melanjutkan eksekusi program utama.

## Executor Framework

`Executor` adalah interface yang menyediakan cara yang lebih fleksibel dan efisien untuk menjalankan thread. Salah satu implementasinya adalah `ExecutorService`.

### Menggunakan `ExecutorService`:

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

        executor.shutdown(); // Menutup executor
    }
}
```

Pada contoh di atas, kita menggunakan `ExecutorService` untuk mengeksekusi beberapa tugas secara paralel dengan menggunakan pool thread. `Executors.newFixedThreadPool(2)` membuat dua thread untuk menjalankan tugas.

## ForkJoinPool

`ForkJoinPool` adalah kelas di Java yang dirancang untuk memproses tugas besar yang dapat dibagi-bagi menjadi tugas lebih kecil yang dapat dikerjakan secara paralel. Ini sangat cocok untuk pemrograman paralel dengan pembagian tugas yang mendalam.

### Contoh ForkJoinPool:

```java
import java.util.concurrent.RecursiveTask;
import java.util.concurrent.ForkJoinPool;

public class Main {
    public static void main(String[] args) {
        ForkJoinPool pool = new ForkJoinPool();
        Task task = new Task(10);
        System.out.println(pool.invoke(task));
    }
}

class Task extends RecursiveTask<Integer> {
    private final int n;

    Task(int n) {
        this.n = n;
    }

    @Override
    protected Integer compute() {
        if (n <= 1) {
            return 1;
        } else {
            Task task1 = new Task(n - 1);
            task1.fork(); // Fork task to be processed asynchronously
            return n * task1.join(); // Combine the result
        }
    }
}
```

Pada contoh di atas, kita menggunakan `ForkJoinPool` untuk menyelesaikan tugas faktorial dengan cara membagi tugas menjadi sub-tugas lebih kecil yang dijalankan secara paralel.

## Synchronization dan Deadlock

Dalam aplikasi yang menggunakan banyak thread, kita perlu berhati-hati dengan **synchronization** untuk menghindari kondisi balapan (race condition) dan **deadlock**. Deadlock terjadi ketika dua thread saling menunggu untuk mendapatkan sumber daya yang terkunci oleh thread lainnya.

### Synchronization:

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

        // Menjalankan dua thread untuk mengubah nilai count
        Thread thread1 = new Thread(() -> counter.increment());
        Thread thread2 = new Thread(() -> counter.increment());

        thread1.start();
        thread2.start();

        thread1.join();
        thread2.join();

        System.out.println("Count: " + counter.getCount());
    }
}
```

Dengan menggunakan kata kunci `synchronized`, kita memastikan bahwa hanya satu thread yang dapat mengakses method `increment()` pada saat yang sama, menghindari kondisi balapan.

## Kesimpulan

Pemrograman paralel di Java memungkinkan kita untuk menjalankan beberapa thread secara bersamaan, meningkatkan efisiensi aplikasi, terutama dalam pengolahan data yang besar. Dengan menggunakan `Thread`, `ExecutorService`, `ForkJoinPool`, dan fitur lainnya, kita dapat memanfaatkan penuh kemampuan perangkat keras modern yang memiliki banyak core. Namun, perlu diingat bahwa concurrency juga membutuhkan perhatian ekstra dalam hal pengelolaan thread dan synchronization untuk menghindari masalah seperti race condition dan deadlock.
