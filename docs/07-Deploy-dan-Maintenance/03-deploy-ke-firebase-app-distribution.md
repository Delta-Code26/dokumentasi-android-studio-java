# ☁️ Deploy ke Firebase App Distribution

Firebase App Distribution bikin proses **uji coba aplikasi sebelum rilis** jadi gampang banget! Kamu bisa kirim APK/AAB langsung ke tester tanpa perlu upload ke Play Store. Praktis banget buat tim kecil atau tester internal. 🚀

---

## 🔧 Syarat & Persiapan

1. Akun Firebase
2. Proyek Android terhubung ke Firebase
3. File `.apk` atau `.aab` hasil build
4. Firebase CLI terinstal

---

## 🔌 Langkah 1: Hubungkan Project ke Firebase

1. Buka [Firebase Console](https://console.firebase.google.com/)
2. Pilih atau buat project baru
3. Tambahkan aplikasi Android
4. Download `google-services.json`, dan letakkan di folder `app/`
5. Tambahkan Firebase SDK di `build.gradle`

```gradle
// root build.gradle
classpath 'com.google.gms:google-services:4.3.15'

// app/build.gradle
apply plugin: 'com.google.gms.google-services'
```

---

## 🛠️ Langkah 2: Build Aplikasi (APK atau AAB)

Via Android Studio:

```
Build > Build Bundle(s) / APK(s) > Build APK(s) atau Bundle
```

Atau via terminal:

```bash
./gradlew assembleRelease
```

---

## 📥 Langkah 3: Instal Firebase CLI

```bash
npm install -g firebase-tools
```

Login ke akun Firebase:

```bash
firebase login
```

---

## 📤 Langkah 4: Deploy ke Firebase App Distribution

Contoh perintah untuk mengirim `.apk`:

```bash
firebase appdistribution:distribute app-release.apk \
  --app <APP_ID> \
  --groups "tester-android" \
  --release-notes "Versi beta 1.0"
```

Ganti `app-release.apk` dengan nama file kamu, dan `APP_ID` bisa kamu temukan di Firebase Console di bagian **General Settings**.

Untuk `.aab`, sama aja:

```bash
firebase appdistribution:distribute app-release.aab \
  --app <APP_ID> \
  --groups "tester-android" \
  --release-notes "Versi AAB uji coba"
```

---

## 👥 Kelola Tester

Bisa dari CLI:

```bash
firebase appdistribution:add-testers email1@email.com,email2@email.com --app <APP_ID>
```

Atau dari Firebase Console:

- Masuk ke Firebase > App Distribution
- Tambahkan grup / email tester

---

## 📲 Notifikasi ke Tester

Setelah kamu deploy:

✅ Tester akan dapat email untuk download aplikasi

📱 Aplikasi bisa diinstal langsung dari link yang dikirim Firebase

---

## 🔁 Integrasi CI/CD

Kalau kamu pakai GitHub Actions atau GitLab CI/CD, Firebase App Distribution bisa diintegrasikan buat auto-deploy setiap kali push. Bisa aku bantu setup kalau kamu mau!

---

## 🎯 Kesimpulan

| Tools            | Fungsi                         |
|------------------|--------------------------------|
| Firebase Console | Pengaturan tester & release    |
| Firebase CLI     | Deploy APK/AAB ke tester       |
| AppDistribution  | Solusi uji coba sebelum rilis  |

Firebase App Distribution = *Play Store internal*, tapi versi kilat dan fleksibel. Cocok buat tim kecil yang mau cepet ngetes app-nya tanpa ribet nunggu review. ⚡

Kalau kamu mau lanjut ke **setup CI/CD (misal pakai GitHub Actions)** buat auto-deploy ke Firebase, tinggal bilang aja ya! 🎯