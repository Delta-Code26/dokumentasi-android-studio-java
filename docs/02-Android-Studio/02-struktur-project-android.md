# 🏗️ Struktur Project Android

Saat kamu membuat project baru di Android Studio, kamu bakal lihat banyak folder dan file yang kelihatannya ribet banget. Tapi tenang, kita bakal bedah satu per satu!

---

## 🗂️ Struktur Folder Utama

```
MyApplication/
├── .idea/
├── app/
│   ├── build/
│   ├── libs/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/
│   │   │   ├── res/
│   │   │   └── AndroidManifest.xml
├── build/
├── gradle/
├── build.gradle (Project level)
├── build.gradle (App level)
└── settings.gradle
```

---

## 📂 Penjelasan Folder-Folder Penting

### 1. `app/src/main/java/`

Di sinilah **kode Java (atau Kotlin)** kamu berada.  
Biasanya terdiri dari:
- Class `MainActivity.java` (entry point aplikasi)
- Class-class tambahan (misalnya adapter, helper, dsb.)

> 📌 Semua logika aplikasi kamu ditulis di folder ini!

---

### 2. `app/src/main/res/`

Berisi semua **resource (sumber daya)** non-kode seperti:

| Folder         | Isi                                                |
|----------------|-----------------------------------------------------|
| `layout/`      | File XML untuk UI (tampilan antarmuka)             |
| `drawable/`    | Gambar, ikon, background, dll                      |
| `mipmap/`      | Icon aplikasi di berbagai resolusi                 |
| `values/`      | Warna, dimensi, string, dan style (dalam XML)      |

---

### 3. `AndroidManifest.xml`

File penting yang menjelaskan:
- Nama package aplikasi
- Activity utama (launcher)
- Permission (akses kamera, internet, dll)

> 🔒 Wajib paham file ini kalau mau publish app atau pakai fitur tertentu.

---

## 📄 File Konfigurasi Penting

### ✅ `build.gradle` (Project Level)

Mengatur konfigurasi umum, seperti:
- Versi Gradle
- Repositori (misal: jcenter, maven)

### ✅ `build.gradle` (App Level)

Tempat atur:
- Compile SDK version
- Dependencies (library yang kamu pakai)
- Versi aplikasi (versionCode & versionName)

### ✅ `settings.gradle`

Mengatur module apa aja yang ada di project.

---

## 💡 Tips Developer

- Jangan asal hapus file di folder `res` dan `java`
- Kalau error, cek `Gradle Console` dulu
- Selalu **sync Gradle** setelah mengubah konfigurasi `build.gradle`

---

## 🧪 Quick Quiz!

> Q: Dimana letak file untuk desain UI di Android Studio?  
> A: `res/layout/`

> Q: Di file apa kamu mendaftarkan permission kamera?  
> A: `AndroidManifest.xml`
