# ⚙️ Activity & Lifecycle di Android

## 📱 Apa Itu Activity?

> **Activity** adalah *layar* dalam aplikasi Android. Setiap kali kamu buka halaman baru di aplikasi, sebenarnya kamu sedang membuka *Activity* baru.

Contoh:
- Halaman login → 1 Activity
- Halaman dashboard → 1 Activity
- Halaman detail produk → 1 Activity

---

## 🧠 Struktur Dasar Activity

```java
public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }
}
```

### Penjelasan:
- `MainActivity` → kelas utama yang mewakili layar.
- `onCreate()` → method yang dipanggil saat activity dibuat pertama kali.
- `setContentView()` → menghubungkan Java dengan XML layout.

---

## 🔄 Siklus Hidup Activity (Activity Lifecycle)

Android mengelola setiap activity melalui *siklus hidup* agar efisien dan hemat resource.

```txt
onCreate() ➜ onStart() ➜ onResume() ➜ [Activity Aktif]
                  ↓
            onPause() ➜ onStop() ➜ onDestroy()
```

| Method        | Kapan Dipanggil                                          |
|---------------|----------------------------------------------------------|
| `onCreate()`  | Saat activity pertama kali dibuat                        |
| `onStart()`   | Saat activity muncul ke layar (belum interaktif)        |
| `onResume()`  | Saat activity jadi aktif dan bisa diinteraksi           |
| `onPause()`   | Saat activity mulai tidak fokus (misalnya buka dialog)  |
| `onStop()`    | Saat activity tidak terlihat di layar                   |
| `onDestroy()` | Saat activity dihancurkan (ditutup permanen)            |

---

## 🧪 Contoh Penggunaan Lifecycle

```java
@Override
protected void onStart() {
    super.onStart();
    Log.d("Lifecycle", "onStart dipanggil");
}
```

Cocok untuk:
- Memulai animasi
- Cek koneksi internet
- Load data dari database

---

## 🗃️ Aktivitas vs Fragment

| Activity                        | Fragment                         |
|--------------------------------|----------------------------------|
| Representasi satu layar penuh  | Bisa jadi bagian dari satu layar |
| Berat (lebih kompleks)         | Ringan & modular                 |
| Berdiri sendiri                | Harus hidup dalam Activity       |

---

## 💡 Tips Developer

- Jangan taruh terlalu banyak logic di `onCreate()`
- Gunakan `onPause()` atau `onStop()` untuk menyimpan data sementara
- Pakai `Log.d()` untuk debugging siklus hidup!

---

## 🧠 Mini Quiz

**Q:** Apa perbedaan antara `onCreate()` dan `onResume()`?  
**A:** `onCreate()` dipanggil sekali saat activity dibuat. `onResume()` dipanggil setiap kali activity jadi aktif (bisa berkali-kali).
