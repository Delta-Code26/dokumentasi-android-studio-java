# 🐞 Debugging di Android Studio

## 🚨 Apa Itu Debugging?

Debugging adalah proses mencari dan memperbaiki bug (kesalahan) dalam aplikasi. Di Android Studio, kita bisa **menghentikan eksekusi sementara**, melihat **nilai variabel**, dan **mengikuti alur program** secara detail.

> Debugging itu kayak jadi detektif di dunia kode. 🕵️‍♂️

---

## 🧰 Tools Debugging di Android Studio

| Tool                      | Fungsi                                                                 |
|---------------------------|------------------------------------------------------------------------|
| Logcat                   | Menampilkan log aktivitas aplikasi dan sistem.                         |
| Breakpoint               | Menyisipkan titik berhenti di baris kode tertentu.                     |
| Debugger Window          | Melihat isi variabel saat breakpoint kena.                             |
| Step Into/Over/Out       | Menelusuri eksekusi program baris demi baris.                          |
| Evaluate Expression      | Mengecek nilai dari ekspresi/kode tertentu secara langsung.            |

---

## 🪵 1. Menggunakan Logcat

```java
Log.d("TAG", "Pesan debug");
Log.i("TAG", "Informasi penting");
Log.e("TAG", "Terjadi error!");
```

**Tips:**
- Gunakan tag yang konsisten (`"MainActivity"`, `"LoginLogic"`, dll).
- Filter berdasarkan package atau level (VERBOSE, DEBUG, INFO, WARN, ERROR).

---

## ⛔ 2. Menggunakan Breakpoint

Cara pasang:
1. Klik di sisi kiri baris kode (di samping nomor baris).
2. Jalankan aplikasi dengan tombol **debug (🐞)**, bukan run biasa (▶️).
3. Eksekusi akan berhenti di breakpoint.

---

## 🧭 3. Navigasi Saat Debugging

| Aksi                  | Fungsi                                                        |
|-----------------------|---------------------------------------------------------------|
| Step Over (F8)        | Jalankan baris ini, lalu lanjut ke baris berikutnya.          |
| Step Into (F7)        | Masuk ke dalam method yang dipanggil.                         |
| Step Out (Shift+F8)   | Keluar dari method ke pemanggilnya.                           |
| Resume Program (F9)   | Melanjutkan eksekusi sampai breakpoint berikutnya.            |

---

## 🔎 4. Evaluasi Nilai Ekspresi

1. Saat breakpoint kena, buka tab `Evaluate Expression`.
2. Masukkan ekspresi, contoh: `user.getNama()` atau `list.size()`.
3. Klik Evaluate → Akan muncul hasilnya.

Ini berguna buat nyari penyebab bug tanpa harus cetak log duluan. Instant insight!

---

## 🔄 5. Watch & Variable

- **Variables**: Tampilkan nilai semua variabel lokal.
- **Watches**: Tambahkan variabel atau ekspresi yang ingin dipantau terus-menerus.

---

## ⚙️ 6. Debugging Crash & Error

- Gunakan logcat untuk cari pesan `FATAL EXCEPTION`.
- Perhatikan **stack trace**: baris yang menyebut file & baris kode sumber bug.
- Debug log: Filter ke `Error` atau `Assert`.

Contoh:
```
E/AndroidRuntime: FATAL EXCEPTION: main
    java.lang.NullPointerException: Attempt to invoke method on null object reference
        at com.marno.myapp.MainActivity.onCreate(MainActivity.java:42)
```

> "NullPointerException: musuh abadi para Java devs." ☠️

---

## 🧠 Tips Debugging Pro

- Selalu simpan `Log.d()` pada bagian penting alur program.
- Periksa intent extras dengan `getIntent().getExtras()`.
- Jangan lupa cek `null` di setiap pemanggilan method/variabel.
- Gunakan `try-catch` dan log untuk exception handling.

---

## 🤹 Contoh Debugging Skenario

### Kasus: Tombol login tidak berfungsi

Langkah:
1. Pasang breakpoint di dalam listener tombol.
2. Jalankan aplikasi dengan debug mode.
3. Cek apakah listener terpanggil.
4. Lihat variabel `username`, `password` → kosong kah?
5. Cek response dari API, status code, body response.

---

## 🎯 Kesimpulan

Debugging bukan hanya soal memperbaiki error, tapi soal **memahami perilaku kode**. Semakin sering kamu debug, semakin tajam insting kamu.

> "Code works? Great. Code doesn’t work? Time to go full Sherlock." 🔍

---