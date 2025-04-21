# 📦 Build APK di Android Studio

Mau APK-mu siap diinstal atau dibagiin ke teman satu tim (atau calon investor 👀)? Yuk, kita bahas cara build APK di Android Studio dari yang paling dasar sampai pro!

---

## 🛠 Persiapan Project

Sebelum build APK, pastikan:

- Aplikasi tidak error (🚫 merah-merah di IDE).
- Sudah tes fitur utama (jangan sampai tombol "Login" malah bikin aplikasi meledak 💥).
- Versi dan nama paket sudah sesuai.

---

## 🧱 Build APK via Android Studio (Tanpa Signing)

Langkah-langkah:

1. Buka Android Studio.
2. Klik menu: **Build > Build Bundle(s) / APK(s) > Build APK(s)**.
3. Tunggu proses selesai.
4. Lihat notifikasi di kanan bawah, lalu klik **Locate**.

📁 APK kamu akan muncul di folder:

```
project-folder/app/build/outputs/apk/debug/app-debug.apk
```

> APK ini hanya untuk testing karena belum signed.

---

## 🔐 Build APK dengan Signed (Siap Rilis)

Kalau mau upload ke Play Store atau pakai APK untuk produksi, **harus signed!**

### Langkah-langkah:

1. **Buat file keystore (jika belum punya)**:
   - **Build > Generate Signed Bundle / APK**
   - Pilih **APK**
   - Klik **Next**
   - Pilih "Create new..."
   - Isi semua form dan simpan file `.jks` dengan aman.

2. **Generate Signed APK**:
   - Isi detail keystore
   - Pilih build type: `release`
   - Klik **Finish**

📁 APK akan muncul di:

```
project-folder/app/release/app-release.apk
```

---

## ⚙️ Tips Tambahan

- **Minify** kode untuk mengurangi ukuran APK:
  ```gradle
  buildTypes {
      release {
          minifyEnabled true
          proguardFiles getDefaultProguardFile('proguard-android-optimize.txt'), 'proguard-rules.pro'
      }
  }
  ```

- Jangan share file `.jks` ke orang lain. Itu kunci rumahmu! 🏠🔑

---

## 🔄 Otomatis Build via Command Line

```bash
./gradlew assembleDebug      # APK untuk debug
./gradlew assembleRelease    # APK untuk produksi
```

---

## 🎯 Penamaan APK Otomatis (Optional)

Pakai script custom untuk otomatis kasih nama file berdasarkan versi:

```groovy
android.applicationVariants.all { variant ->
    variant.outputs.all {
        outputFileName = "MyApp-v${variant.versionName}-${variant.buildType.name}.apk"
    }
}
```

---

## 🧼 Bersihkan Build Lama

```bash
./gradlew clean
```

---

## 🏁 Kesimpulan

Build APK itu proses penting sebelum distribusi. Pastikan kamu:

✅ Sudah tes  
✅ Sign APK  
✅ Simpan keystore dengan aman  
✅ Jangan lupa ngopi ☕ sambil nunggu build

---

Kalau kamu butuh panduan deploy ke Play Store atau Firebase App Distribution, tinggal bilang ya! Kita lanjut ke level "senior developer 😎" bareng!