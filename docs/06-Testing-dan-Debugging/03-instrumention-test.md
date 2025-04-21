# 🧪 Instrumentation Test di Android

## 📌 Apa Itu Instrumentation Test?

Instrumentation Test adalah jenis pengujian yang dijalankan langsung di perangkat Android atau emulator. Berbeda dengan Unit Test yang hanya butuh JVM, instrumentation test berinteraksi langsung dengan **komponen Android** seperti `Activity`, `Fragment`, `View`, dan lainnya.

> Bahasa gaulnya: "Tes lapangan langsung di medan perang!" 🪖📱

---

## 🧠 Kenapa Perlu?

- Menguji UI/UX secara langsung.
- Interaksi antar komponen Android (misalnya navigasi antar activity).
- Menguji lifecycle dan event Android (onClick, onBackPressed, dsb).
- Validasi UI di berbagai device/emulator.

---

## 📁 Struktur Folder Test

Android Studio memisahkan test berdasarkan lingkungan:

| Lokasi              | Tipe Test            |
|---------------------|----------------------|
| `src/test/java`     | Unit Test (JVM only) |
| `src/androidTest/java` | Instrumentation Test (di device) |

---

## 🚀 Contoh Instrumentation Test

### 1. Tambahkan Dependency

Di `build.gradle (Module: app)`:

```groovy
dependencies {
    androidTestImplementation 'androidx.test.ext:junit:1.1.5'
    androidTestImplementation 'androidx.test.espresso:espresso-core:3.5.1'
}
```

---

### 2. Buat Tes Sederhana

```java
import androidx.test.ext.junit.runners.AndroidJUnit4;
import androidx.test.rule.ActivityTestRule;

import org.junit.Rule;
import org.junit.Test;
import org.junit.runner.RunWith;

import static androidx.test.espresso.Espresso.onView;
import static androidx.test.espresso.matcher.ViewMatchers.withId;
import static androidx.test.espresso.assertion.ViewAssertions.matches;
import static androidx.test.espresso.matcher.ViewMatchers.withText;

@RunWith(AndroidJUnit4.class)
public class MainActivityTest {

    @Rule
    public ActivityTestRule<MainActivity> activityRule =
        new ActivityTestRule<>(MainActivity.class);

    @Test
    public void testTextView() {
        onView(withId(R.id.textView))
            .check(matches(withText("Halo Dunia!")));
    }
}
```

---

## 🔎 Penjelasan

- `@RunWith(AndroidJUnit4.class)` → Menjalankan test dengan AndroidJUnit.
- `ActivityTestRule` → Memastikan Activity yang akan diuji dibuka dulu.
- `Espresso` → Framework untuk interaksi dengan UI.

---

## 💡 Tips Penggunaan Espresso

| Aksi                          | Contoh                                      |
|------------------------------|---------------------------------------------|
| Klik view                    | `onView(withId(R.id.button)).perform(click());` |
| Isi input                    | `onView(withId(R.id.editText)).perform(typeText("Hello"));` |
| Cek hasil teks               | `onView(withId(R.id.textView)).check(matches(withText("Halo")));` |
| Scroll view tertentu         | `onView(withId(R.id.recyclerView)).perform(scrollTo());` |

---

## 🧠 Best Practice

- Gunakan **IdlingResource** untuk menunggu proses async (misalnya Retrofit).
- Hindari terlalu banyak UI test karena runtime-nya lama.
- Gabungkan dengan unit test untuk coverage maksimal.
- Gunakan emulator yang ringan khusus untuk testing (misalnya Android Go).

---

## 🛠️ Menjalankan Tes

1. Buka class test.
2. Klik kanan → Run 'MainActivityTest'.
3. Atau tekan `Shift + F10`.

---

## 🧨 Kekurangan Instrumentation Test

- **Lambat** karena perlu build + run emulator/device.
- Perlu emulator aktif atau perangkat terhubung.
- Sulit dijalankan di CI/CD tanpa emulator headless.

---

## 🎯 Kesimpulan

Instrumentation test cocok buat ngecek hal-hal yang nggak bisa dilakukan oleh unit test, terutama bagian UI & interaksi pengguna. Kalo unit test itu latihan mental, ini kayak sparring lawan musuh langsung. 😎

> _"Test UI mu seperti kamu takut bug di depan atasan."_ – Kata bijak Android Dev 🧘

---