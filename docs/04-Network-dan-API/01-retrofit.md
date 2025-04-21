# 🌐 Retrofit: Menghubungkan Aplikasi Android dengan API

> **Retrofit** adalah library yang memudahkan kita dalam menghubungkan aplikasi Android dengan API menggunakan HTTP. Retrofit menangani permintaan HTTP dan parsing data JSON menjadi objek Java secara otomatis. Dalam dokumentasi ini, kita akan mempelajari cara menggunakan Retrofit untuk mengakses API dari aplikasi Android.

---

## 📚 Pengantar Retrofit

Retrofit adalah salah satu library paling populer di Android untuk berkomunikasi dengan server melalui RESTful API. Retrofit memungkinkan kita untuk melakukan operasi HTTP seperti `GET`, `POST`, `PUT`, dan `DELETE` dengan sangat mudah.

Dengan Retrofit, kita tidak perlu menulis kode berulang untuk membuat HTTP request, menangani respons, dan mengonversi data JSON. Retrofit menangani semua itu dengan hanya beberapa baris kode.

---

## 🔧 Setup Retrofit di Android Studio

### 1. **Menambahkan Dependensi Retrofit**

Untuk menggunakan Retrofit, kita perlu menambahkan dependensi ke file `build.gradle` (Module: app) proyek Android kita.

```gradle
dependencies {
    implementation 'com.squareup.retrofit2:retrofit:2.9.0'
    implementation 'com.squareup.retrofit2:converter-gson:2.9.0'  // Untuk parsing JSON menggunakan Gson
    implementation 'com.squareup.okhttp3:logging-interceptor:4.9.0'  // Optional, untuk logging request dan response
}
```

Setelah itu, klik **Sync Now** agar Android Studio mengunduh dependensi yang dibutuhkan.

---

## 🛠️ Mengonfigurasi Retrofit

### 1. **Membuat Interface API**

Retrofit bekerja dengan cara mendeklarasikan antarmuka (interface) yang berisi metode HTTP. Di setiap metode, kita menentukan jenis permintaan HTTP yang diinginkan (GET, POST, PUT, DELETE) dan URL endpointnya.

#### Contoh: Mengambil Daftar Pengguna

```java
public interface ApiService {
    @GET("users")
    Call<List<User>> getUsers();
}
```

Pada contoh ini, kita mendeklarasikan metode `getUsers()` yang akan melakukan permintaan HTTP `GET` ke endpoint `users`.

### 2. **Membuat Instance Retrofit**

Setelah mendefinisikan interface, kita perlu membuat instance Retrofit untuk menghubungkannya dengan API endpoint.

```java
Retrofit retrofit = new Retrofit.Builder()
        .baseUrl("https://api.example.com/")  // URL dasar dari API
        .addConverterFactory(GsonConverterFactory.create())  // Menambahkan converter untuk mengonversi JSON ke objek Java
        .build();

ApiService apiService = retrofit.create(ApiService.class);
```

Dengan kode di atas, kita membuat objek Retrofit dan menghubungkannya dengan URL dasar API (`baseUrl`). Kemudian, kita menambahkan konverter Gson untuk mengonversi data JSON menjadi objek Java.

### 3. **Menjalankan Permintaan API**

Untuk menjalankan permintaan API, kita perlu memanggil metode yang ada di `ApiService` dan menunggu responsnya.

#### Contoh: Mengambil Data Pengguna

```java
Call<List<User>> call = apiService.getUsers();
call.enqueue(new Callback<List<User>>() {
    @Override
    public void onResponse(Call<List<User>> call, Response<List<User>> response) {
        if (response.isSuccessful()) {
            // Berhasil mendapatkan data
            List<User> users = response.body();
            // Lakukan sesuatu dengan data pengguna
        } else {
            // Tangani respons error
        }
    }

    @Override
    public void onFailure(Call<List<User>> call, Throwable t) {
        // Tangani kegagalan permintaan (misalnya tidak ada koneksi internet)
    }
});
```

Pada contoh ini, kita menggunakan `enqueue()` untuk menjalankan permintaan API secara asinkron. Retrofit akan menangani thread utama untuk kita, sehingga kita tidak perlu khawatir akan terjadi ANR (Application Not Responding).

---

## 🧑‍💻 Menggunakan Request Body dan Parameter

Retrofit juga memungkinkan kita untuk mengirimkan data dalam permintaan, baik menggunakan body atau parameter URL.

### 1. **POST dengan Request Body**

Untuk mengirim data dengan metode POST, kita menggunakan anotasi `@Body`.

```java
@POST("users")
Call<User> createUser(@Body User user);
```

Dalam contoh ini, data `User` akan dikirimkan dalam tubuh permintaan (`POST`).

### 2. **Menggunakan Parameter dalam URL**

Untuk mengirim parameter melalui URL, kita menggunakan anotasi `@Query`.

```java
@GET("users")
Call<List<User>> getUsersByAge(@Query("age") int age);
```

Pada contoh ini, kita mengirimkan parameter `age` dalam URL seperti `https://api.example.com/users?age=25`.

### 3. **Mengirim Data dengan Path Parameter**

Kita juga bisa mengirim data melalui bagian URL (path) menggunakan anotasi `@Path`.

```java
@GET("users/{id}")
Call<User> getUserById(@Path("id") int userId);
```

Di sini, kita mengirimkan parameter `id` dalam path URL, seperti `https://api.example.com/users/1`.

---

## 🔄 Menangani Response API

### 1. **Menggunakan `Response` untuk Menangani Respons API**

Di dalam callback `onResponse()`, Retrofit mengembalikan objek `Response` yang berisi status HTTP, data, dan metadata lainnya.

```java
Response<List<User>> response = response.body();
if (response != null && response.isSuccessful()) {
    // Data tersedia
} else {
    // Respons error, tangani dengan baik
}
```

### 2. **Menangani Error**

Jika ada masalah dengan permintaan, kita dapat menangani error dengan memeriksa kode status HTTP atau pesan kesalahan.

```java
if (response.code() == 404) {
    // Tangani error 404 (not found)
} else if (response.code() == 500) {
    // Tangani error 500 (internal server error)
}
```

Selain itu, kita bisa menggunakan exception handling untuk menangani masalah yang terjadi selama permintaan API (misalnya masalah jaringan).

---

## 🔐 Menggunakan Autentikasi dan Authorization

Untuk API yang membutuhkan autentikasi, kita bisa menggunakan Retrofit dengan header Authorization.

```java
public interface ApiService {
    @GET("protected-data")
    Call<Data> getProtectedData(@Header("Authorization") String authHeader);
}
```

Pada contoh di atas, kita mengirimkan header `Authorization` untuk mengakses data yang dilindungi.

---

## 🛠️ Logging Request dan Response (Opsional)

Untuk tujuan debugging, kita bisa menggunakan **OkHttp Logging Interceptor** untuk mencatat semua permintaan dan respons HTTP yang dikirimkan.

### 1. **Menambahkan OkHttp Logging Interceptor**

```java
HttpLoggingInterceptor interceptor = new HttpLoggingInterceptor();
interceptor.setLevel(HttpLoggingInterceptor.Level.BODY);

OkHttpClient client = new OkHttpClient.Builder()
        .addInterceptor(interceptor)
        .build();

Retrofit retrofit = new Retrofit.Builder()
        .baseUrl("https://api.example.com/")
        .client(client)
        .addConverterFactory(GsonConverterFactory.create())
        .build();
```

Dengan kode ini, Retrofit akan mencatat semua permintaan dan respons yang dikirimkan ke konsol, sehingga memudahkan kita dalam proses debugging.

---

## 🎯 Kesimpulan

Retrofit adalah alat yang sangat berguna untuk berkomunikasi dengan API dalam aplikasi Android. Dengan menggunakan Retrofit, kita bisa melakukan operasi HTTP dengan cara yang sangat sederhana dan efisien. Retrofit juga memudahkan pengelolaan data JSON, autentikasi, dan error handling, menjadikannya pilihan utama untuk integrasi API di aplikasi Android.

> **"API integration doesn't have to be hard. Retrofit makes it easy!"**