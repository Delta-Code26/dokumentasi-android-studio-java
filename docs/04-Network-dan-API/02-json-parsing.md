# 🌐 JSON Parsing di Android

> **JSON (JavaScript Object Notation)** adalah format data yang sering digunakan untuk komunikasi antara server dan aplikasi. Dalam aplikasi Android, kita sering mengunduh data dalam format JSON dari API dan perlu mengonversinya menjadi objek Java. Di dokumentasi ini, kita akan mempelajari cara parsing JSON di Android menggunakan berbagai teknik, termasuk menggunakan **Gson** dan **Moshi**.

---

## 📚 Pengantar JSON

JSON adalah format teks yang ringan dan mudah dibaca untuk penyimpanan dan pertukaran data. JSON digunakan secara luas dalam aplikasi web dan mobile untuk bertukar informasi dengan server.

Contoh format JSON:

```json
{
  "id": 1,
  "name": "John Doe",
  "email": "john.doe@example.com"
}
```

Dalam contoh ini, data JSON berisi tiga properti: `id`, `name`, dan `email`. Kita perlu mengonversi data ini menjadi objek Java agar bisa diproses dalam aplikasi Android.

---

## 🔧 Teknik Parsing JSON di Android

Ada beberapa cara untuk melakukan parsing JSON di Android. Dua yang paling umum digunakan adalah **Gson** dan **Moshi**. Kita akan fokus pada **Gson** di sini, tetapi Moshi adalah alternatif yang baik jika kamu ingin mencobanya.

### 1. **Menggunakan Gson untuk Parsing JSON**

Gson adalah library populer yang dibuat oleh Google untuk parsing JSON ke objek Java dan sebaliknya. Gson sangat mudah digunakan dan mendukung parsing secara otomatis berdasarkan model Java yang sudah didefinisikan.

#### Langkah 1: Menambahkan Dependensi Gson

Tambahkan dependensi Gson ke dalam file `build.gradle` proyek Android kamu.

```gradle
dependencies {
    implementation 'com.google.code.gson:gson:2.8.8'
}
```

### 2. **Membuat Model Java**

Model Java adalah kelas yang mencerminkan struktur data JSON yang kita terima. Setiap elemen JSON akan dipetakan ke properti dalam kelas Java.

Contoh model Java untuk data JSON di atas:

```java
public class User {
    private int id;
    private String name;
    private String email;

    // Getter dan Setter untuk setiap field
    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getEmail() {
        return email;
    }

    public void setEmail(String email) {
        this.email = email;
    }
}
```

### 3. **Parsing JSON ke Objek Java**

Setelah memiliki model Java, kita dapat menggunakan Gson untuk mengonversi data JSON menjadi objek Java.

```java
import com.google.gson.Gson;

String jsonResponse = "{ \"id\": 1, \"name\": \"John Doe\", \"email\": \"john.doe@example.com\" }";

// Membuat instance Gson
Gson gson = new Gson();

// Parsing JSON ke objek User
User user = gson.fromJson(jsonResponse, User.class);

// Mengakses data objek
Log.d("User", "ID: " + user.getId());
Log.d("User", "Name: " + user.getName());
Log.d("User", "Email: " + user.getEmail());
```

Di sini, kita menggunakan `fromJson()` untuk mengonversi string JSON ke dalam objek `User`. Setelah parsing, kita dapat mengakses data objek tersebut dengan menggunakan getter yang telah kita definisikan.

---

## 🔄 JSON Array Parsing

Jika kamu menerima data JSON dalam bentuk array, seperti ini:

```json
[
    { "id": 1, "name": "John Doe", "email": "john.doe@example.com" },
    { "id": 2, "name": "Jane Doe", "email": "jane.doe@example.com" }
]
```

Kita bisa mengonversinya menjadi sebuah daftar objek Java.

```java
String jsonArrayResponse = "[{ \"id\": 1, \"name\": \"John Doe\", \"email\": \"john.doe@example.com\" }, { \"id\": 2, \"name\": \"Jane Doe\", \"email\": \"jane.doe@example.com\" }]";

Type userListType = new TypeToken<List<User>>(){}.getType();
List<User> users = gson.fromJson(jsonArrayResponse, userListType);

// Mengakses daftar user
for (User user : users) {
    Log.d("User", "ID: " + user.getId() + ", Name: " + user.getName());
}
```

Di sini, kita menggunakan `TypeToken<List<User>>` untuk memberitahu Gson bahwa kita ingin mengonversi JSON menjadi sebuah `List<User>`.

---

## 🧑‍💻 Parsing JSON dengan Retrofit dan Gson

Ketika menggunakan Retrofit untuk mengakses API, Retrofit secara otomatis akan menangani parsing JSON menjadi objek Java dengan bantuan converter seperti Gson.

### 1. **Membuat Interface API dengan Retrofit**

```java
public interface ApiService {
    @GET("users")
    Call<List<User>> getUsers();
}
```

### 2. **Menambahkan Gson Converter ke Retrofit**

```java
Retrofit retrofit = new Retrofit.Builder()
        .baseUrl("https://api.example.com/")
        .addConverterFactory(GsonConverterFactory.create())  // Menambahkan converter Gson
        .build();

ApiService apiService = retrofit.create(ApiService.class);
```

### 3. **Menggunakan Retrofit untuk Mendapatkan Data dan Parsing JSON**

```java
Call<List<User>> call = apiService.getUsers();
call.enqueue(new Callback<List<User>>() {
    @Override
    public void onResponse(Call<List<User>> call, Response<List<User>> response) {
        if (response.isSuccessful()) {
            List<User> users = response.body();
            for (User user : users) {
                Log.d("User", "ID: " + user.getId() + ", Name: " + user.getName());
            }
        } else {
            // Tangani respons error
        }
    }

    @Override
    public void onFailure(Call<List<User>> call, Throwable t) {
        // Tangani kegagalan permintaan
    }
});
```

Dengan cara ini, Retrofit dan Gson bekerja bersama untuk menangani parsing JSON secara otomatis, memungkinkan kita untuk fokus pada logika aplikasi.

---

## 📝 Menangani JSON yang Kompleks

Kadang-kadang, data JSON yang kita terima mungkin lebih kompleks, misalnya, dengan nested object atau array yang lebih dalam. Dalam kasus ini, kita hanya perlu membuat model Java yang mencerminkan struktur JSON yang lebih rumit.

Contoh JSON dengan objek nested:

```json
{
  "id": 1,
  "name": "John Doe",
  "address": {
    "street": "123 Main St",
    "city": "Anytown",
    "zip": "12345"
  }
}
```

Model Java yang sesuai:

```java
public class Address {
    private String street;
    private String city;
    private String zip;

    // Getter dan Setter
}

public class User {
    private int id;
    private String name;
    private Address address;

    // Getter dan Setter
}
```

Dengan model ini, Gson akan otomatis mengonversi objek JSON `address` menjadi objek `Address` di dalam objek `User`.

---

## 🔐 Menangani JSON yang Terkadang Null

Kadang-kadang, API mengembalikan nilai `null` untuk beberapa properti. Gson menangani ini secara otomatis, tetapi kita bisa mengontrolnya menggunakan anotasi `@SerializedName`.

```java
public class User {
    @SerializedName("user_id")
    private int id;

    @SerializedName("user_name")
    private String name;

    @SerializedName("email_address")
    private String email;

    // Getter dan Setter
}
```

Jika nama field JSON berbeda dengan nama properti di kelas Java, kita bisa menggunakan anotasi `@SerializedName` untuk memetakan nama field JSON dengan nama variabel dalam kelas Java.

---

## 🎯 Kesimpulan

Parsing JSON adalah bagian yang sangat penting dalam berinteraksi dengan API di Android. Dengan menggunakan Gson atau library lainnya, kita dapat mengonversi data JSON menjadi objek Java yang bisa kita proses lebih lanjut. Retrofit dan Gson memudahkan kita dalam menangani parsing JSON secara otomatis, membuat pengembangan aplikasi Android yang berkomunikasi dengan server lebih efisien dan mudah.

> **"JSON parsing made simple with Gson!"**