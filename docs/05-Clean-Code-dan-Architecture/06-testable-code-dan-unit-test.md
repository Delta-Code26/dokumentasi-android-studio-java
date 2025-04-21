# 🧪 Kode yang Dapat Diuji dan Unit Test dalam Pengembangan Aplikasi Android

**Kode yang dapat diuji** adalah prinsip penting dalam pengembangan perangkat lunak yang memastikan bahwa kode yang kita tulis dapat diuji dengan mudah menggunakan alat pengujian otomatis. **Unit test** adalah teknik pengujian yang digunakan untuk memverifikasi apakah bagian terkecil dari kode, yaitu unit, berfungsi sesuai yang diharapkan.

Pada dokumentasi ini, kita akan membahas cara menulis kode yang dapat diuji dengan mudah serta bagaimana cara menulis **unit test** untuk aplikasi Android menggunakan **JUnit** dan **Mockito**.

---

## 🛠️ Menulis Kode yang Dapat Diuji

Menulis kode yang dapat diuji adalah hal pertama yang perlu dipertimbangkan saat menulis kode. Kode yang dapat diuji tidak hanya mudah untuk diuji tetapi juga memudahkan pengembang untuk membuat perubahan tanpa takut merusak bagian lain dari sistem.

### 1. **Pemecahan Masalah Menjadi Fungsi Kecil**

Fungsi atau metode yang kecil dan fokus pada satu tugas akan lebih mudah diuji. Hindari menulis fungsi besar yang menangani banyak tugas sekaligus. Jika sebuah fungsi menangani lebih dari satu tugas, pertimbangkan untuk memecahnya menjadi beberapa fungsi kecil.

```java
public class Calculator {
    public int add(int a, int b) {
        return a + b;
    }

    public int multiply(int a, int b) {
        return a * b;
    }

    // Fungsi yang kecil dan terpisah
}
```

### 2. **Gunakan Dependensi yang Dapat Diganti (Dependency Injection)**

Dengan menggunakan **dependency injection**, Anda dapat mengganti dependensi dalam kode Anda dengan objek yang lebih mudah diuji. Hal ini membuat kelas-kelas Anda lebih modular dan memungkinkan Anda untuk menyuntikkan dependensi palsu (mock) saat pengujian.

#### Contoh yang Buruk:
```java
public class UserManager {
    private DatabaseHelper databaseHelper;

    public UserManager() {
        databaseHelper = new DatabaseHelper();  // Ketergantungan langsung
    }

    public void saveUser(User user) {
        databaseHelper.save(user);
    }
}
```

#### Perbaikan dengan Dependency Injection:
```java
public class UserManager {
    private DatabaseHelper databaseHelper;

    public UserManager(DatabaseHelper databaseHelper) {
        this.databaseHelper = databaseHelper;  // Menyuntikkan dependensi
    }

    public void saveUser(User user) {
        databaseHelper.save(user);
    }
}
```

Dengan menggunakan **dependency injection**, Anda dapat dengan mudah mengganti **DatabaseHelper** dengan versi palsu untuk pengujian.

### 3. **Pisahkan Logika Bisnis dari UI**

Logika bisnis, seperti pengolahan data dan keputusan aplikasi, harus dipisahkan dari logika antarmuka pengguna (UI). Dengan cara ini, Anda dapat menguji logika bisnis secara terpisah dari UI, yang lebih sulit untuk diuji.

#### Contoh yang Buruk:
```java
public class MainActivity extends AppCompatActivity {
    private TextView resultTextView;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        resultTextView = findViewById(R.id.resultTextView);
        resultTextView.setText(calculateResult());
    }

    private String calculateResult() {
        return "Hasil: " + (5 + 10);
    }
}
```

#### Perbaikan:
```java
public class Calculator {
    public String calculateResult(int a, int b) {
        return "Hasil: " + (a + b);
    }
}

public class MainActivity extends AppCompatActivity {
    private TextView resultTextView;
    private Calculator calculator;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        calculator = new Calculator(); // Memisahkan logika bisnis
        resultTextView = findViewById(R.id.resultTextView);
        resultTextView.setText(calculator.calculateResult(5, 10));
    }
}
```

Dengan memisahkan logika bisnis ke kelas `Calculator`, kita dapat menguji `Calculator` secara terpisah.

---

## 🧑‍🔬 Unit Testing di Android

**Unit testing** adalah proses pengujian unit terkecil dari aplikasi (seperti fungsi atau metode) untuk memastikan bahwa ia bekerja sesuai yang diinginkan. Android menyediakan beberapa alat untuk menulis dan menjalankan unit test, termasuk **JUnit** dan **Mockito**.

### 1. **Menggunakan JUnit untuk Unit Test**

JUnit adalah framework pengujian yang paling populer di Java dan dapat digunakan untuk menulis unit test di aplikasi Android.

#### Contoh Unit Test dengan JUnit:
```java
import org.junit.Test;
import static org.junit.Assert.*;

public class CalculatorTest {
    @Test
    public void testAdd() {
        Calculator calculator = new Calculator();
        int result = calculator.add(5, 10);
        assertEquals(15, result);
    }

    @Test
    public void testMultiply() {
        Calculator calculator = new Calculator();
        int result = calculator.multiply(5, 10);
        assertEquals(50, result);
    }
}
```

- **@Test**: Menandakan bahwa metode ini adalah unit test.
- **assertEquals**: Memverifikasi bahwa hasil dari metode yang diuji sesuai dengan nilai yang diharapkan.

### 2. **Menggunakan Mockito untuk Mocking**

Mockito adalah framework untuk membuat objek palsu (mock) yang dapat digunakan dalam unit test. Objek mock digunakan untuk menggantikan dependensi nyata yang mungkin sulit untuk diuji (misalnya, database atau API).

#### Contoh Penggunaan Mockito:
```java
import org.junit.Test;
import static org.mockito.Mockito.*;
import static org.junit.Assert.*;

public class UserManagerTest {
    @Test
    public void testSaveUser() {
        DatabaseHelper mockDatabaseHelper = mock(DatabaseHelper.class); // Membuat mock
        UserManager userManager = new UserManager(mockDatabaseHelper);

        User user = new User("John");
        userManager.saveUser(user);

        verify(mockDatabaseHelper).save(user); // Memverifikasi apakah save dipanggil
    }
}
```

- **mock(DatabaseHelper.class)**: Membuat objek mock dari kelas `DatabaseHelper`.
- **verify(mockDatabaseHelper)**: Memverifikasi bahwa metode `save` dipanggil pada objek mock.

---

## 🎯 Kesimpulan

Menulis **kode yang dapat diuji** dan melakukan **unit testing** adalah bagian penting dari pengembangan perangkat lunak yang berkualitas. Kode yang mudah diuji mempermudah pengujian dan pengelolaan aplikasi Android. Dengan mengikuti prinsip-prinsip ini, pengembang dapat memastikan aplikasi mereka bebas dari bug dan lebih mudah untuk diperbaiki dan dikembangkan lebih lanjut di masa depan.