# 🧩 Deep Dive ke Dependency Injection di Android

> Dependency Injection (DI) adalah teknik desain perangkat lunak yang membantu mengelola ketergantungan antar komponen dalam aplikasi. DI meningkatkan fleksibilitas, pengujian, dan pemeliharaan kode aplikasi.

---

## 📚 Apa Itu Dependency Injection?

Dependency Injection adalah teknik yang digunakan untuk menginjeksi atau memberikan dependensi (komponen atau objek yang diperlukan) ke dalam suatu kelas, daripada membuat atau menginisialisasi objek secara langsung di dalam kelas itu sendiri.

Dengan menggunakan DI, kita dapat membuat kode lebih modular dan mudah diuji.

---

## 🚀 Kenapa Dependency Injection Penting?

1. **Meningkatkan Pengujian**: Dengan DI, kita dapat lebih mudah melakukan unit testing karena kita bisa mengganti dependensi dengan mock atau objek tiruan.
2. **Mengurangi Ketergantungan Kelas**: DI mengurangi coupling antara kelas, membuat kode lebih fleksibel dan mudah diperbarui.
3. **Mempermudah Pengelolaan Kode**: Memisahkan pembuatan objek dari penggunaannya membuat aplikasi lebih terorganisir.

---

## 🧑‍💻 Implementasi Dependency Injection di Android

Di Android, kita bisa menerapkan Dependency Injection menggunakan beberapa framework. Dua yang paling populer adalah:

1. **Dagger 2** - Sebuah framework DI yang kuat dan sangat sering digunakan di Android.
2. **Hilt** - Sebuah wrapper di atas Dagger 2 yang disediakan oleh Google untuk memudahkan implementasi DI di Android.

### 1. **Menggunakan Dagger 2 di Android**

#### a. **Menambahkan Dagger ke Proyek**

Untuk menggunakan Dagger 2, pertama kita perlu menambahkannya ke dalam dependensi aplikasi di file `build.gradle`:

```gradle
dependencies {
    implementation 'com.google.dagger:dagger:2.40.5'
    annotationProcessor 'com.google.dagger:dagger-compiler:2.40.5'
}
```

#### b. **Membuat Modul untuk Mengatur Dependency**

Di Dagger, kita membuat **Module** untuk menyediakan objek atau dependensi. Modul ini mendeklarasikan metode-metode yang mengembalikan dependensi yang akan diinjeksi.

```java
@Module
public class NetworkModule {

    @Provides
    public static OkHttpClient provideOkHttpClient() {
        return new OkHttpClient();
    }
    
    @Provides
    public static Retrofit provideRetrofit(OkHttpClient client) {
        return new Retrofit.Builder()
                .baseUrl("https://api.example.com")
                .client(client)
                .build();
    }
}
```

#### c. **Membuat Komponen untuk Menyuntikkan Dependensi**

Selanjutnya, kita membuat **Component** yang akan menghubungkan Modul dengan kelas yang membutuhkan dependensi.

```java
@Component(modules = {NetworkModule.class})
public interface AppComponent {
    void inject(MainActivity mainActivity);
}
```

#### d. **Melakukan Injeksi di Kelas yang Membutuhkan**

Terakhir, kita menggunakan `@Inject` di kelas yang membutuhkan dependensi.

```java
public class MainActivity extends AppCompatActivity {

    @Inject
    Retrofit retrofit;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Melakukan injeksi dependensi
        DaggerAppComponent.create().inject(this);
    }
}
```

---

### 2. **Menggunakan Hilt di Android**

Hilt adalah solusi Dependency Injection yang lebih sederhana dibandingkan Dagger dan dirancang khusus untuk Android.

#### a. **Menambahkan Hilt ke Proyek**

Untuk menggunakan Hilt, tambahkan dependensi Hilt ke file `build.gradle`:

```gradle
dependencies {
    implementation 'androidx.hilt:hilt-lifecycle-viewmodel:1.0.0-alpha03'
    implementation 'com.google.dagger:hilt-android:2.40.5'
    kapt 'com.google.dagger:hilt-compiler:2.40.5'
}
```

Kemudian, aktifkan plugin Hilt di bagian atas file `build.gradle`:

```gradle
apply plugin: 'dagger.hilt.android.plugin'
```

#### b. **Menandai Kelas dengan Hilt**

Untuk menggunakan Hilt di Android, kita menambahkan `@AndroidEntryPoint` pada `Activity`, `Fragment`, atau `ViewModel` yang membutuhkan injeksi dependensi.

```java
@AndroidEntryPoint
public class MainActivity extends AppCompatActivity {

    @Inject
    Retrofit retrofit;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        
        // Hilt akan menginjeksi dependensi secara otomatis
    }
}
```

#### c. **Membuat Modul Hilt untuk Menyediakan Dependensi**

Modul Hilt digunakan untuk menyediakan dependensi yang akan diinjeksi ke dalam komponen-komponen Android.

```java
@Module
@InstallIn(SingletonComponent.class)
public class NetworkModule {

    @Provides
    public static Retrofit provideRetrofit() {
        OkHttpClient client = new OkHttpClient();
        return new Retrofit.Builder()
                .baseUrl("https://api.example.com")
                .client(client)
                .build();
    }
}
```

Dengan Hilt, kita tidak perlu lagi membuat komponen secara manual seperti di Dagger.

---

## 🎨 Best Practices untuk Dependency Injection

- **Gunakan Scope yang Tepat**: Pastikan menggunakan scope yang tepat untuk objek yang perlu bertahan lama atau yang hanya perlu dibuat sekali, seperti `@Singleton`.
- **Modularisasi yang Baik**: Jangan membuat modul yang terlalu besar. Pisahkan dependensi sesuai dengan fungsionalitas aplikasi.
- **Pertahankan Kesederhanaan**: Jangan terlalu membebani aplikasi dengan banyak dependensi. Cobalah untuk menjaga agar dependensi tetap minimum.

---

## ⚡ Keuntungan dan Tantangan Dependency Injection

### Keuntungan:

1. **Mempermudah Pengujian Unit**: DI memungkinkan kita untuk mengganti dependensi dengan mock atau objek tiruan, sehingga mempermudah pengujian unit.
2. **Memisahkan Tanggung Jawab**: DI memungkinkan pemisahan tanggung jawab antar komponen aplikasi, yang menjadikannya lebih modular dan terorganisir.
3. **Mengurangi Ketergantungan**: DI mengurangi ketergantungan langsung antar kelas, yang membuat kode lebih mudah dipelihara dan diperbarui.

### Tantangan:

1. **Kurva Belajar**: DI, khususnya dengan framework seperti Dagger, bisa memiliki kurva belajar yang curam, terutama bagi pengembang yang baru mengenalnya.
2. **Konfigurasi yang Rumit**: Konfigurasi dan setup awal untuk DI, terutama dengan Dagger, bisa cukup rumit dan membingungkan.
3. **Kinerja**: Penggunaan DI yang berlebihan tanpa perencanaan yang baik dapat mempengaruhi kinerja aplikasi, terutama dalam hal inisialisasi dan pengelolaan objek.

---

## 💬 Kesimpulan

Dependency Injection adalah alat yang sangat berguna untuk mengelola ketergantungan dalam aplikasi Android. Dengan menggunakan Dagger atau Hilt, kamu dapat mengelola objek dan komponen aplikasi dengan lebih efisien dan fleksibel. Meskipun ada tantangan dalam implementasinya, keuntungan yang didapatkan, seperti pengujian yang lebih mudah dan kode yang lebih modular, menjadikannya investasi yang sangat berharga dalam pengembangan aplikasi Android.

> "Gunakan DI dengan bijak untuk mengubah kode yang rapuh menjadi aplikasi yang lebih fleksibel dan teruji!" 🧩