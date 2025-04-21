# 🧪 Mocking dengan Mockito di Android Studio

## 👀 Apa itu Mockito?

Mockito adalah framework testing populer yang digunakan untuk **mocking** object—alias bikin tiruan object buat dites tanpa perlu akses ke resource asli (misalnya database, API, dsb).

> "Pura-pura tapi halal. That's mocking, not catfishing." 🫣

---

## 🎯 Kenapa Perlu Mocking?

- Mengisolasi unit test dari dependency eksternal.
- Menguji logika *service*, *presenter*, *viewmodel*, dll tanpa koneksi real.
- Simulasi respon API tanpa harus benar-benar manggil server.

---

## ⚙️ Setup Mockito

Tambahkan ke `build.gradle (Module)`:

```gradle
testImplementation 'org.mockito:mockito-core:5.2.0'
testImplementation 'org.mockito:mockito-inline:5.2.0'
testImplementation 'junit:junit:4.13.2'
```

> Untuk Android Instrumented Test, gunakan `mockito-android`.

---

## 🛠 Contoh Skenario

Misal kamu punya class:

```java
public class AuthService {
    public boolean login(String user, String pass) {
        // misal cek ke database
        return true;
    }
}
```

Dan `LoginPresenter` yang pakai `AuthService`:

```java
public class LoginPresenter {
    private AuthService authService;

    public LoginPresenter(AuthService authService) {
        this.authService = authService;
    }

    public boolean handleLogin(String u, String p) {
        return authService.login(u, p);
    }
}
```

---

## 🔧 Buat Tes Pakai Mockito

```java
@RunWith(MockitoJUnitRunner.class)
public class LoginPresenterTest {

    @Mock
    AuthService mockAuthService;

    @InjectMocks
    LoginPresenter presenter;

    @Test
    public void testLoginBerhasil() {
        when(mockAuthService.login("admin", "123")).thenReturn(true);

        boolean result = presenter.handleLogin("admin", "123");

        assertTrue(result);
        verify(mockAuthService).login("admin", "123");
    }
}
```

---

## 🧪 Metode Penting Mockito

| Fungsi                  | Deskripsi |
|--------------------------|----------|
| `@Mock`                 | Buat object palsu |
| `@InjectMocks`          | Inject mock ke object yang dites |
| `when(...).thenReturn()`| Tentukan hasil saat mock dipanggil |
| `verify()`              | Pastikan method dipanggil |
| `any()`, `eq()`         | Buat argumen fleksibel |

---

## 😎 Advanced Mocking

### Mock return berbeda-beda
```java
when(mock.getData())
    .thenReturn("Pertama")
    .thenReturn("Kedua");
```

### Simulasi error
```java
when(mock.getData()).thenThrow(new RuntimeException("API down"));
```

---

## 🚀 Kesimpulan

Mockito = sahabatmu untuk unit test. Bikin test lebih ringan, cepat, dan bebas dari dependency luar.

> "Dengan Mockito, kamu bisa ngoding sambil acting. Tapi acting-nya cuma buat object, bukan buat mantan." 😅

--- 

Kalau kamu butuh integrasi dengan `ViewModel`, `Repository`, atau bahkan `Retrofit`, tinggal bilang yaa — biar kita bikin lanjutannya 👨‍💻🔥