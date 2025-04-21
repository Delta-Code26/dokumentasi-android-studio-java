# 🚀 Implementasi Login, Register dan JWT Authentication di Android

Pada bagian ini, kita akan mempelajari cara mengimplementasikan sistem login dan registrasi menggunakan JSON Web Token (JWT) sebagai metode autentikasi di aplikasi Android. JWT adalah standar terbuka yang memungkinkan kita untuk mengirimkan informasi terautentikasi secara aman antar pihak melalui objek JSON.

---

## 🔑 Apa itu JWT?

**JWT (JSON Web Token)** adalah format token berbasis JSON yang digunakan untuk mentransmisikan informasi antar sistem dengan cara yang aman dan terstandarisasi. JWT sering digunakan untuk autentikasi dan pengelolaan sesi dalam aplikasi berbasis web atau aplikasi mobile.

JWT terdiri dari tiga bagian utama:

1. **Header**: Berisi informasi tentang algoritma yang digunakan untuk menandatangani token.
2. **Payload**: Berisi klaim atau informasi yang ingin disimpan di dalam token (misalnya, ID pengguna atau hak akses).
3. **Signature**: Digunakan untuk memverifikasi bahwa token tidak dimodifikasi.

---

## 🛠️ Persiapan Backend untuk JWT Authentication

Sebelum mengimplementasikan login dan registrasi di Android, pastikan backend API kamu sudah disiapkan untuk menangani JWT Authentication. Di sisi backend, kita perlu melakukan beberapa hal:

### 1. **Setup JWT Token di Backend**

Di backend, kamu akan membutuhkan library JWT untuk menghasilkan dan memverifikasi token. Jika kamu menggunakan framework seperti **FastAPI** atau **Flask** di Python, kamu bisa menggunakan library seperti `PyJWT`.

- **Generasi Token (Login)**: Ketika pengguna login, server akan memverifikasi kredensial dan mengembalikan token JWT.
- **Verifikasi Token (Setiap Permintaan)**: Setiap kali aplikasi Android mengirimkan permintaan API yang memerlukan autentikasi, token JWT akan dikirim dalam header `Authorization`.

---

## 📲 Implementasi Login di Android Studio

### 1. **Membuat Form Login**

Buat tampilan login menggunakan XML di Android Studio. Form login akan terdiri dari:

- EditText untuk memasukkan username/email
- EditText untuk memasukkan password
- Button untuk melakukan login

```xml
<EditText
    android:id="@+id/editTextUsername"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:hint="Username"/>

<EditText
    android:id="@+id/editTextPassword"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:hint="Password"
    android:inputType="textPassword"/>

<Button
    android:id="@+id/buttonLogin"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Login"/>
```

### 2. **Mengirim Permintaan Login ke API**

Gunakan **Retrofit** untuk mengirimkan permintaan login ke server. Berikut adalah contoh implementasi login di Android menggunakan Retrofit.

#### a. **Model untuk Request dan Response Login**

```java
public class LoginRequest {
    private String username;
    private String password;

    // Constructor, Getter dan Setter
}

public class LoginResponse {
    private String token;

    // Getter dan Setter
}
```

#### b. **Interface Retrofit untuk API Login**

```java
public interface ApiService {
    @POST("login")
    Call<LoginResponse> login(@Body LoginRequest request);
}
```

#### c. **Mengirim Permintaan di Activity**

```java
Retrofit retrofit = new Retrofit.Builder()
        .baseUrl("https://api.example.com/")
        .addConverterFactory(GsonConverterFactory.create())
        .build();

ApiService apiService = retrofit.create(ApiService.class);

LoginRequest loginRequest = new LoginRequest("username", "password");

apiService.login(loginRequest).enqueue(new Callback<LoginResponse>() {
    @Override
    public void onResponse(Call<LoginResponse> call, Response<LoginResponse> response) {
        if (response.isSuccessful()) {
            String token = response.body().getToken();
            // Simpan token untuk digunakan di request berikutnya
        } else {
            // Handle error
        }
    }

    @Override
    public void onFailure(Call<LoginResponse> call, Throwable t) {
        // Handle failure
    }
});
```

---

## 📝 Implementasi Register di Android Studio

Sama seperti login, form registrasi membutuhkan **username**, **email**, **password**, dan **confirm password**. Berikut adalah contoh UI untuk registrasi.

### 1. **Membuat Form Registrasi**

```xml
<EditText
    android:id="@+id/editTextEmail"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:hint="Email"/>

<EditText
    android:id="@+id/editTextUsername"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:hint="Username"/>

<EditText
    android:id="@+id/editTextPassword"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:hint="Password"
    android:inputType="textPassword"/>

<EditText
    android:id="@+id/editTextConfirmPassword"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:hint="Confirm Password"
    android:inputType="textPassword"/>

<Button
    android:id="@+id/buttonRegister"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Register"/>
```

### 2. **Mengirim Permintaan Register ke API**

#### a. **Model untuk Request dan Response Register**

```java
public class RegisterRequest {
    private String username;
    private String email;
    private String password;

    // Constructor, Getter dan Setter
}

public class RegisterResponse {
    private String message;

    // Getter dan Setter
}
```

#### b. **Interface Retrofit untuk API Register**

```java
public interface ApiService {
    @POST("register")
    Call<RegisterResponse> register(@Body RegisterRequest request);
}
```

#### c. **Mengirim Permintaan di Activity**

```java
ApiService apiService = retrofit.create(ApiService.class);

RegisterRequest registerRequest = new RegisterRequest("username", "email@example.com", "password");

apiService.register(registerRequest).enqueue(new Callback<RegisterResponse>() {
    @Override
    public void onResponse(Call<RegisterResponse> call, Response<RegisterResponse> response) {
        if (response.isSuccessful()) {
            // Handle successful registration
        } else {
            // Handle error
        }
    }

    @Override
    public void onFailure(Call<RegisterResponse> call, Throwable t) {
        // Handle failure
    }
});
```

---

## 🔒 Menggunakan JWT untuk Autentikasi di Setiap Permintaan

Setelah login berhasil dan kamu mendapatkan token JWT, kamu harus mengirim token tersebut di header setiap permintaan yang memerlukan autentikasi.

### 1. **Menambahkan Token ke Header Permintaan**

```java
OkHttpClient client = new OkHttpClient.Builder()
        .addInterceptor(new Interceptor() {
            @Override
            public Response intercept(Chain chain) throws IOException {
                Request original = chain.request();
                Request request = original.newBuilder()
                        .header("Authorization", "Bearer " + token) // Tambahkan JWT ke header
                        .build();
                return chain.proceed(request);
            }
        })
        .build();

Retrofit retrofit = new Retrofit.Builder()
        .baseUrl("https://api.example.com/")
        .client(client) // Set client dengan interceptor
        .addConverterFactory(GsonConverterFactory.create())
        .build();
```

Sekarang, setiap permintaan API akan mengirimkan token JWT dalam header **Authorization** untuk memverifikasi identitas pengguna.

---

## 🔑 Kesimpulan

Dengan implementasi login, registrasi, dan JWT di aplikasi Android, kamu dapat menjaga keamanan data pengguna dan memastikan hanya pengguna yang terautentikasi yang dapat mengakses API yang dilindungi. Menggunakan JWT memungkinkan aplikasi Android berkomunikasi dengan server secara aman dan efisien.

> **"Secure your app with JWT, and let your users feel safe!"**