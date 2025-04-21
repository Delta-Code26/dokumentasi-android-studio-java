# 📦 Android App Bundle (AAB): Format Masa Depan untuk Distribusi Aplikasi

Sejak Agustus 2021, Google Play mewajibkan aplikasi baru untuk diupload dalam format **.aab (Android App Bundle)**, bukan lagi .apk. Yuk kenalan sama AAB dan cara build-nya! 🚀

---

## 🤔 Apa Itu App Bundle?

Android App Bundle adalah format distribusi resmi dari Google yang memungkinkan Google Play membangun dan mengirimkan APK yang **dioptimalkan untuk perangkat pengguna**.

### ✨ Keuntungan AAB:
- 🔍 Ukuran aplikasi lebih kecil (Google Play hanya kirim bagian yang diperlukan).
- 📱 Mendukung fitur modularisasi.
- 📦 Lebih cepat diunduh & diinstal.
- ✅ Format wajib untuk aplikasi baru di Play Store.

---

## 🔨 Build AAB di Android Studio

### Langkah-langkah:

1. Buka Android Studio.
2. Klik menu: **Build > Build Bundle(s) / APK(s) > Build Bundle(s)**.
3. Tunggu proses build selesai.
4. Klik **Locate** di notifikasi build untuk membuka folder output.

📁 File `.aab` akan muncul di:

```
project-folder/app/build/outputs/bundle/release/app-release.aab
```

---

## 🔐 Generate AAB dengan Signing

Format .aab **wajib di-sign** untuk distribusi, terutama di Google Play.

### Langkah-langkah:

1. **Build > Generate Signed Bundle / APK**
2. Pilih **Android App Bundle**
3. Klik **Next**
4. Isi info keystore (gunakan yang sama seperti APK)
5. Pilih build type: `release`
6. Klik **Finish**

> Setelah selesai, kamu bisa upload ke Google Play Console.

---

## ☁️ Upload ke Google Play

1. Buka [Google Play Console](https://play.google.com/console)
2. Pilih aplikasimu / buat baru
3. Pilih **Release > Production > Create Release**
4. Upload file `.aab`
5. Isi changelog dan konfigurasi lainnya
6. Klik **Review > Release**

---

## 🔎 Debug AAB? Gimana Caranya?

AAB tidak bisa diinstal langsung seperti APK. Untuk testing lokal:

- **Gunakan emulator via Android Studio**
- Atau, gunakan **Google Play Internal Testing** via Play Console

---

## 💡 Tips Penting

- Simpan file keystore dengan aman! Google Play akan butuh itu untuk update app berikutnya.
- Pakai **Play App Signing** untuk keamanan lebih (Google yang jaga key-nya).
- Untuk aplikasi modular atau dengan dynamic features, AAB adalah solusi paling efisien.

---

## 🏁 Kesimpulan

| Format | Keterangan |
|--------|------------|
| `.apk` | Bisa diinstal langsung, cocok untuk debug/test lokal |
| `.aab` | Wajib untuk distribusi resmi via Google Play |

Kalau APK itu seperti warteg, AAB tuh kayak restoran all-you-can-eat: kita cukup ambil yang dibutuhin aja, sisanya enggak usah dimasak. 🍽️

---

Kalau kamu pengen lanjut ke topik **deploy ke Firebase App Distribution atau CI/CD dengan GitHub Actions**, tinggal bilang aja ya, bestie developer! 🧑‍💻💚