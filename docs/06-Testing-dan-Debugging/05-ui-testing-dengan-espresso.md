# ☕ UI Testing dengan Espresso di Android Studio

## 🔍 Apa itu Espresso?

Espresso adalah framework testing dari Google untuk menguji **UI Android**. Ia memungkinkan kamu **mensimulasikan interaksi pengguna** seperti klik, input teks, scroll, dan verifikasi tampilan—secara otomatis.

> "Espresso: bukan cuma kopi, tapi juga bikin kamu tenang saat testing UI." 😎

---

## 🎯 Kenapa Perlu UI Testing?

- Menjamin tampilan aplikasi bekerja sesuai rencana.
- Menghindari regresi saat ada perubahan layout/kode.
- Cocok untuk testing *form login*, *navigasi antar activity*, dan *komponen UI lainnya*.

---

## ⚙️ Setup Espresso

Tambahkan dependensi ke `build.gradle (Module)`:

```gradle
androidTestImplementation 'androidx.test.espresso:espresso-core:3.5.1'
androidTestImplementation 'androidx.test.ext:junit:1.1.5'
androidTestImplementation 'androidx.test:rules:1.5.0'
```

---

## 🛠 Struktur Test

Tes Espresso ditaruh di direktori:

```
src/androidTest/java/com/namapackage/
```

Contoh class test:
```java
@RunWith(AndroidJUnit4.class)
public class LoginActivityTest {

    @Rule
    public ActivityScenarioRule<LoginActivity> activityRule =
            new ActivityScenarioRule<>(LoginActivity.class);

    @Test
    public void testInputUsername() {
        onView(withId(R.id.username)).perform(typeText("admin"));
        onView(withId(R.id.username)).check(matches(withText("admin")));
    }
}
```

---

## ☝️ Perintah Dasar Espresso

| Aksi                        | Kode                                                    |
|-----------------------------|----------------------------------------------------------|
| Klik tombol                 | `onView(withId(R.id.btn)).perform(click());`             |
| Ketik teks                  | `onView(withId(R.id.input)).perform(typeText("Halo"));`  |
| Cek teks muncul             | `onView(withText("Berhasil")).check(matches(isDisplayed()));` |
| Scroll                      | `onView(withId(R.id.scrollview)).perform(scrollTo());`   |
| Tekan tombol "Back"         | `pressBack();`                                           |

---

## ✅ Contoh Tes: Form Login

```java
@Test
public void testLoginSukses() {
    onView(withId(R.id.edtUsername)).perform(typeText("admin"), closeSoftKeyboard());
    onView(withId(R.id.edtPassword)).perform(typeText("123456"), closeSoftKeyboard());
    onView(withId(R.id.btnLogin)).perform(click());
    
    onView(withText("Selamat datang")).check(matches(isDisplayed()));
}
```

---

## 🧪 Test RecyclerView

```java
@Test
public void testKlikItemRecyclerView() {
    onView(withId(R.id.recyclerView))
        .perform(RecyclerViewActions.actionOnItemAtPosition(0, click()));
    
    onView(withId(R.id.detailText)).check(matches(isDisplayed()));
}
```

---

## 🧠 Tips Tambahan

- Selalu tutup keyboard pakai `closeSoftKeyboard()` agar gak ganggu klik.
- Gunakan `IdlingResource` kalau kamu pakai background thread atau delay.
- Gunakan `Espresso Intents` untuk menguji *intent navigation*.

---

## 🧪 Menjalankan Test

Klik kanan file test → **Run**  
Atau: buka tab **Run > Run 'tesmu'**.

> Bisa juga langsung dari Android Studio Test UI. Jangan lupa pilih `androidTest`.

---

## 🚀 Kesimpulan

Espresso bikin kamu bisa ngetes UI tanpa harus pencet-pencet manual. Lebih cepat, lebih akurat, dan bisa diotomatisasi!

> "Tes UI otomatis? Lebih enak dari kopi espresso double shot." ☕🔥

---