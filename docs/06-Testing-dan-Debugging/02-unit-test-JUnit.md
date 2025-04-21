# 🧪 Unit Test dengan JUnit di Android

## 📌 Apa Itu Unit Test?

Unit Test adalah metode pengujian kode secara _isolated_, biasanya di level fungsi atau metode, untuk memastikan output-nya sesuai harapan. Di Android (dan Java), kita sering menggunakan **JUnit** untuk ini.

> Anggap aja unit test itu kayak kamu lagi ngecek satu baut di mesin sebelum semuanya dirakit 🚀

---

## 🧠 Apa Itu JUnit?

**JUnit** adalah framework testing untuk Java, dan digunakan secara luas di proyek Android. Versi terbaru yang umum digunakan: **JUnit 4** atau **JUnit 5**.

---

## ✅ Struktur Dasar Unit Test JUnit

```java
import org.junit.Test;
import static org.junit.Assert.*;

public class CalculatorTest {

    @Test
    public void testPenjumlahan() {
        int result = 2 + 3;
        assertEquals(5, result);
    }
}
```

### 🔍 Penjelasan:

- `@Test` → Menandakan bahwa method ini adalah test unit.
- `assertEquals(expected, actual)` → Mengecek apakah hasilnya sesuai ekspektasi.

---

## 🧪 Jenis Assertions

| Assertion | Fungsi |
|----------|--------|
| `assertEquals(a, b)` | True jika a == b |
| `assertTrue(condition)` | True jika condition bernilai true |
| `assertFalse(condition)` | True jika condition bernilai false |
| `assertNull(obj)` | True jika objek null |
| `assertNotNull(obj)` | True jika objek tidak null |

---

## 🛠️ Menambahkan Unit Test di Android Studio

1. Klik kanan pada package → **New → Java Class** → beri nama (misal: `MyTest`).
2. Tambahkan `@Test` di method yang ingin diuji.
3. Klik kanan di file → **Run 'MyTest'**.

> Tes akan dijalankan di JVM lokal (bukan emulator).

---

## 💡 Contoh Nyata: Kalkulator Sederhana

### Kode yang Diuji:

```java
public class Calculator {
    public int tambah(int a, int b) {
        return a + b;
    }
}
```

### Unit Test:

```java
import org.junit.Test;
import static org.junit.Assert.*;

public class CalculatorTest {
    @Test
    public void testTambah() {
        Calculator calc = new Calculator();
        int hasil = calc.tambah(4, 6);
        assertEquals(10, hasil);
    }
}
```

---

## 🔄 Menjalankan Unit Test

1. Klik kanan di nama class → Run
2. Atau gunakan shortcut: `Ctrl + Shift + F10` (Windows)

---

## ⚠️ Tips dan Best Practice

- Gunakan nama method yang deskriptif, contoh: `shouldReturnCorrectResult_whenAddingTwoNumbers()`.
- Satu unit test = satu skenario.
- Gunakan **mocking** untuk testing class yang tergantung pada external API/database.
- Jangan test UI dengan JUnit! Gunakan Espresso untuk itu.

---

## 🔥 Kesimpulan

Unit testing pakai JUnit itu seperti senjata rahasia developer buat ngecek logika tanpa perlu buka emulator. Makin rajin ngetes, makin kecil kemungkinan bug lolos ke produksi.

> _“Code without tests is like a car without brakes” – Keren sih, tapi ngeri.”_ 😅

---