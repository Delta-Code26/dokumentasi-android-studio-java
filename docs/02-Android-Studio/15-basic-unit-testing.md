# ✅ Basic Unit Testing di Android Studio

> Kalau coding itu bikin nasi goreng, **unit testing** itu nyicipin tiap bahan sebelum digoreng. Biar nggak zonk pas disajikan ke user 😅

---

## 🧪 Apa Itu Unit Testing?

Unit Testing adalah teknik pengujian kode di mana kita menguji **bagian terkecil dari program (unit)** — biasanya fungsi atau method — untuk memastikan output-nya sesuai ekspektasi.

---

## ⚙️ Tools & Framework Default di Android

- `JUnit` → Framework testing paling dasar dan populer
- `Assert` → Untuk memeriksa hasil yang diharapkan
- Android Studio sudah support built-in!

---

## ✍️ Contoh Unit Test Sederhana

Misal kita punya fungsi di Java:

```java
public class Calculator {
    public int tambah(int a, int b) {
        return a + b;
    }
}
```

Unit test-nya:

```java
import org.junit.Test;
import static org.junit.Assert.*;

public class CalculatorTest {

    @Test
    public void testTambah() {
        Calculator calc = new Calculator();
        int hasil = calc.tambah(2, 3);
        assertEquals(5, hasil);
    }
}
```

> `assertEquals(expected, actual)` bakal lolos kalau 5 == 5. Kalau nggak, test gagal 🚨

---

## 🏃 Cara Menjalankan Unit Test

1. Klik kanan pada file test → `Run`
2. Atau klik icon ▶️ di samping @Test
3. Lihat hasilnya di panel **Run / Test Results**

---

## 🧠 Good Practice

- Satu test hanya untuk satu fungsi / satu skenario.
- Gunakan penamaan method seperti `testNamaFungsi_Kondisi_ExpectedOutput`
- Jangan hardcode data di fungsi, gunakan parameter biar bisa dites.

---

## 📦 Struktur Folder Test

Biasanya unit test ada di:

```
src/test/java/com/namapackage
```

> Beda dengan `src/androidTest/` yang khusus untuk Instrumentation Test (uji komponen Android langsung).

---

## 🔁 Tes Lain yang Bisa Dikembangkan

- **Negative test**: Masukan yang salah → harus tetap aman.
- **Boundary test**: Coba angka ekstrem (0, -1, Integer.MAX_VALUE)
- **Parameterized test**: Satu fungsi dites pakai banyak data input.

---

## 🚀 Bonus: Bikin Test Lebih Kuat dengan Mockito

Kalau kamu mau ngetes function yang punya **dependensi eksternal**, seperti API atau database, bisa pakai `Mockito` buat mock object.

---

## 🎯 Kesimpulan

- Unit test penting buat jaga kualitas kode.
- Gampang dipakai di Android Studio.
- Mulai dari fungsi sederhana → lanjut ke fitur kompleks.

> Ingat, kode tanpa test itu kayak masak tanpa nyicip. Gak mau kan user kita keracunan? 😂
