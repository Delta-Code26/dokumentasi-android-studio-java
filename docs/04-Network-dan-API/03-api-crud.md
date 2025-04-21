# 🌐 API CRUD di Android

API CRUD (Create, Read, Update, Delete) adalah operasi dasar yang sering digunakan dalam pengembangan aplikasi Android yang berinteraksi dengan server. API ini memungkinkan aplikasi untuk membuat, membaca, memperbarui, dan menghapus data dari server. Dalam dokumentasi ini, kita akan membahas cara mengimplementasikan operasi CRUD pada API menggunakan Retrofit di Android.

---

## 📚 Pengantar API CRUD

CRUD adalah singkatan dari empat operasi dasar yang dapat dilakukan pada data di aplikasi:

1. **Create**: Menambahkan data baru ke server.
2. **Read**: Mengambil data dari server.
3. **Update**: Memperbarui data yang ada di server.
4. **Delete**: Menghapus data dari server.

API CRUD memungkinkan aplikasi untuk melakukan operasi ini dengan mengirim permintaan HTTP (GET, POST, PUT, DELETE) ke server dan menerima respons berupa data yang diinginkan.

---

## 🔧 Teknik Implementasi API CRUD dengan Retrofit

Kita akan menggunakan **Retrofit** untuk mengakses API dan melakukan operasi CRUD. Retrofit adalah library populer untuk membuat permintaan HTTP di Android dan sangat mudah digunakan bersama dengan **Gson** untuk parsing JSON.

### 1. **Menambahkan Dependensi Retrofit**

Pertama, pastikan kamu telah menambahkan dependensi Retrofit dan Gson di `build.gradle` proyek Android kamu.

```gradle
dependencies {
    implementation 'com.squareup.retrofit2:retrofit:2.9.0'
    implementation 'com.squareup.retrofit2:converter-gson:2.9.0'
}
```

---

## 🔄 1. **Create** (Membuat Data)

Untuk menambahkan data baru ke server, kita biasanya menggunakan metode **POST**.

### 1.1 Membuat Endpoint API

Definisikan endpoint API untuk operasi **Create** di interface Retrofit kamu.

```java
public interface ApiService {
    @POST("users")
    Call<User> createUser(@Body User user);
}
```

Endpoint ini menerima objek `User` yang akan dibuat di server. Kita menggunakan anotasi `@Body` untuk mengirimkan data objek ke server dalam format JSON.

### 1.2 Mengirim Data ke API

Untuk mengirim data ke API, kita perlu membuat objek `User` dan mengirimkannya dengan menggunakan Retrofit.

```java
User newUser = new User();
newUser.setName("John Doe");
newUser.setEmail("john.doe@example.com");

ApiService apiService = retrofit.create(ApiService.class);
Call<User> call = apiService.createUser(newUser);

call.enqueue(new Callback<User>() {
    @Override
    public void onResponse(Call<User> call, Response<User> response) {
        if (response.isSuccessful()) {
            Log.d("API", "User created: " + response.body().getName());
        } else {
            Log.d("API", "Failed to create user");
        }
    }

    @Override
    public void onFailure(Call<User> call, Throwable t) {
        Log.d("API", "Error: " + t.getMessage());
    }
});
```

Di sini, kita membuat objek `User`, lalu mengirimnya melalui API dengan Retrofit. Setelah respons diterima, kita bisa memeriksa apakah permintaan berhasil dan menangani hasilnya.

---

## 🔄 2. **Read** (Membaca Data)

Untuk mendapatkan data dari server, kita biasanya menggunakan metode **GET**.

### 2.1 Membuat Endpoint API untuk Membaca Data

```java
public interface ApiService {
    @GET("users/{id}")
    Call<User> getUser(@Path("id") int userId);
}
```

Endpoint ini mengharuskan kita untuk menyertakan `id` pengguna dalam URL, yang akan digunakan untuk mengambil data pengguna tertentu dari server.

### 2.2 Mengambil Data dari API

Untuk mengakses data, kita cukup memanggil metode `getUser()` dan menangani responsnya.

```java
ApiService apiService = retrofit.create(ApiService.class);
Call<User> call = apiService.getUser(1); // Mengambil data user dengan ID 1

call.enqueue(new Callback<User>() {
    @Override
    public void onResponse(Call<User> call, Response<User> response) {
        if (response.isSuccessful()) {
            User user = response.body();
            Log.d("API", "User data: " + user.getName());
        } else {
            Log.d("API", "Failed to get user data");
        }
    }

    @Override
    public void onFailure(Call<User> call, Throwable t) {
        Log.d("API", "Error: " + t.getMessage());
    }
});
```

Dengan kode ini, aplikasi akan mendapatkan data pengguna berdasarkan `id` yang kita kirimkan melalui API.

---

## 🔄 3. **Update** (Memperbarui Data)

Untuk memperbarui data yang sudah ada di server, kita menggunakan metode **PUT** atau **PATCH**.

### 3.1 Membuat Endpoint API untuk Memperbarui Data

```java
public interface ApiService {
    @PUT("users/{id}")
    Call<User> updateUser(@Path("id") int userId, @Body User user);
}
```

Di sini, kita menggunakan anotasi `@Path` untuk mengganti ID pengguna di URL dan `@Body` untuk mengirimkan data pengguna yang sudah diperbarui.

### 3.2 Mengirim Data yang Diperbarui ke API

```java
User updatedUser = new User();
updatedUser.setName("John Updated");
updatedUser.setEmail("john.updated@example.com");

ApiService apiService = retrofit.create(ApiService.class);
Call<User> call = apiService.updateUser(1, updatedUser);

call.enqueue(new Callback<User>() {
    @Override
    public void onResponse(Call<User> call, Response<User> response) {
        if (response.isSuccessful()) {
            Log.d("API", "User updated: " + response.body().getName());
        } else {
            Log.d("API", "Failed to update user");
        }
    }

    @Override
    public void onFailure(Call<User> call, Throwable t) {
        Log.d("API", "Error: " + t.getMessage());
    }
});
```

Dengan kode ini, kita mengirimkan data pengguna yang sudah diperbarui ke server. Server akan memperbarui data sesuai dengan permintaan.

---

## 🔄 4. **Delete** (Menghapus Data)

Untuk menghapus data di server, kita menggunakan metode **DELETE**.

### 4.1 Membuat Endpoint API untuk Menghapus Data

```java
public interface ApiService {
    @DELETE("users/{id}")
    Call<Void> deleteUser(@Path("id") int userId);
}
```

Endpoint ini akan menghapus pengguna dengan ID yang diberikan.

### 4.2 Menghapus Data dari API

```java
ApiService apiService = retrofit.create(ApiService.class);
Call<Void> call = apiService.deleteUser(1); // Menghapus pengguna dengan ID 1

call.enqueue(new Callback<Void>() {
    @Override
    public void onResponse(Call<Void> call, Response<Void> response) {
        if (response.isSuccessful()) {
            Log.d("API", "User deleted");
        } else {
            Log.d("API", "Failed to delete user");
        }
    }

    @Override
    public void onFailure(Call<Void> call, Throwable t) {
        Log.d("API", "Error: " + t.getMessage());
    }
});
```

Di sini, kita mengirimkan permintaan untuk menghapus pengguna dengan ID tertentu. Jika berhasil, data pengguna akan dihapus dari server.

---

## 🧑‍💻 Kesimpulan

Dengan menggunakan Retrofit, kita dapat dengan mudah mengimplementasikan operasi CRUD dalam aplikasi Android. Retrofit menyediakan antarmuka yang sederhana untuk melakukan permintaan HTTP dan menangani responsnya, sementara Gson memungkinkan kita untuk melakukan parsing JSON secara otomatis. Dengan menggabungkan keduanya, kita dapat dengan cepat membuat aplikasi yang berinteraksi dengan server menggunakan API CRUD.

> **"Creating, Reading, Updating, and Deleting data with ease using Retrofit!"**