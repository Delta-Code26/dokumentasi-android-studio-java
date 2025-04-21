# 🚀 Publish ke Google Play Store

Sudah saatnya aplikasi buatanmu naik panggung utama! Google Play Store adalah tempat terbaik untuk menjangkau jutaan pengguna Android di seluruh dunia. Berikut langkah demi langkah biar proses publikasi lancar tanpa drama. 🎭

---

## 🧾 Syarat & Persiapan Awal

1. Akun Google Play Console (biaya satu kali: $25)
2. File `.aab` (Android App Bundle), bukan `.apk`
3. Ikon aplikasi ukuran besar (512x512 px)
4. Screenshot aplikasi (minimal 2)
5. Deskripsi aplikasi (pendek & panjang)
6. Kategori dan rating konten
7. Link kebijakan privasi (jika diperlukan)

---

## 🎯 Langkah 1: Buat Akun Google Play Console

1. Kunjungi [https://play.google.com/console](https://play.google.com/console)
2. Login dengan akun Google
3. Bayar $25 (sekali seumur hidup)
4. Lengkapi profil developer (nama, email, dll.)

---

## 🆕 Langkah 2: Buat Aplikasi Baru

1. Klik **"Create app"**
2. Pilih:
   - Nama aplikasi
   - Bahasa default
   - Aplikasi atau game
   - Gratis atau berbayar
3. Centang persetujuan & lanjut

---

## 📝 Langkah 3: Isi Info Aplikasi

- **Deskripsi Singkat**
- **Deskripsi Panjang**
- **Kategori** (misalnya: Productivity, Education, dll.)
- **Kontak Developer**: Email wajib, website opsional

---

## 📷 Langkah 4: Upload Aset Visual

1. **Ikon aplikasi** (512x512 px, max 1MB, format PNG)
2. **Screenshot**: Minimal 2 untuk HP, opsional untuk tablet
3. (Opsional) Video YouTube preview

---

## 🛡️ Langkah 5: Tentukan Rating & Kebijakan

1. **Rating Konten**: Isi kuesioner agar aplikasi kamu dinilai cocok untuk umur berapa
2. **Kebijakan Privasi**: Upload link ke halaman kebijakan (wajib kalau ada login/data user)

---

## 📦 Langkah 6: Upload AAB (Bundle)

1. Di bagian **Release > Production**
2. Klik **"Create new release"**
3. Upload file `.aab` dari hasil build Android Studio:
   ```bash
   ./gradlew bundleRelease
   ```
4. Tambahkan changelog (catatan versi)

---

## 🔒 Langkah 7: Setup App Signing by Google

Biasanya otomatis aktif. Google bakal simpan private key dan nge-sign aplikasimu biar aman dan valid.

---

## 🔎 Langkah 8: Review & Kirim untuk Peninjauan

1. Cek semua checklist di bagian Dashboard
2. Pastikan tidak ada tanda ❌ merah
3. Klik **"Publish"** → Google akan meninjau aplikasi (biasanya 3–7 hari kerja untuk rilis pertama)

---

## ✅ Tips Lolos Review

- Jangan pakai permission aneh-aneh (kayak akses lokasi, SMS, dll) kalau nggak jelas fungsinya
- Pastikan semua halaman bisa diakses dan tidak crash
- Uji aplikasi di emulator dan device asli
- Tambahkan kebijakan privasi jika kamu mengumpulkan data apa pun

---

## 🔁 Update Aplikasi?

Gampang! Cukup:

1. Naikkan versi di `build.gradle`:
   ```gradle
   versionCode 2
   versionName "1.1"
   ```
2. Build ulang `.aab`
3. Upload versi baru via **"Create new release"**

---

## 🏁 Penutup

🎉 Selamat! Setelah ini, kamu tinggal tunggu email dari Google bahwa aplikasimu sudah live.

> 📣 *"Build it, test it, deploy it, and flex it on Play Store."*

Kalau kamu butuh bantuin bikin deskripsi yang marketing-ready atau nyiapin gambar Play Store kece, tinggal bilang ya!