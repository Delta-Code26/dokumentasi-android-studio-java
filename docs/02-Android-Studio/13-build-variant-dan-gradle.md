# 🏗️ Build Variant & Gradle di Android Studio

Welcome ke dunia di balik layar Android Studio — tempat sihir-sihir build terjadi! 🔮 Di sinilah Gradle dan Build Variant berperan penting buat ngebuild, ngetes, dan ngatur versi aplikasi kamu.

---

## 📦 Apa Itu Build Variant?

Build Variant adalah kombinasi dari:
- **Build Types**: debug, release
- **Product Flavors**: versi-varian dari app (misal: free vs pro)

> Jadi kamu bisa bikin versi app dengan setting, icon, atau API endpoint yang beda-beda. Gak perlu ngoprek satu-satu 😎

---

### Contoh Build Variant

Misalnya kamu punya:
- Build Type: `debug`, `release`
- Product Flavor: `free`, `pro`

Berarti akan ada 4 variant:
- `freeDebug`
- `freeRelease`
- `proDebug`
- `proRelease`

---

## ⚙️ Cara Setup di `build.gradle (Module: app)`

```groovy
android {
    ...

    buildTypes {
        debug {
            applicationIdSuffix ".debug"
            debuggable true
        }
        release {
            minifyEnabled true
            proguardFiles getDefaultProguardFile('proguard-android-optimize.txt'), 'proguard-rules.pro'
        }
    }

    flavorDimensions "tier"
    productFlavors {
        free {
            dimension "tier"
            applicationIdSuffix ".free"
            versionNameSuffix "-free"
        }
        pro {
            dimension "tier"
            applicationIdSuffix ".pro"
            versionNameSuffix "-pro"
        }
    }
}
```

---

## 📁 Struktur Folder Khusus

Kamu bisa punya file Java/layout khusus per flavor atau per variant.

Contoh:
```
src/
  free/
    java/
    res/
  pro/
    java/
    res/
  debug/
    java/
    res/
```

---

## ⚡ Gradle: Otaknya Build System

Gradle adalah sistem build powerful yang:
- Compile kode
- Generate APK
- Download dependencies
- Run test, dll

### Contoh Dependency:
```groovy
dependencies {
    implementation 'androidx.appcompat:appcompat:1.6.1'
    implementation 'com.squareup.retrofit2:retrofit:2.9.0'
}
```

### Tambah Plugin:
```groovy
plugins {
    id 'com.android.application'
    id 'kotlin-android'
}
```

---

## 🧪 Build Versi Tertentu

Pilih Build Variant di:
📍 Android Studio → kiri bawah → tab "Build Variants"

Atau pakai command line:
```bash
./gradlew assembleProRelease
```

---

## 🔐 Tips Tambahan

- Simpan API key yang beda di masing-masing `buildConfigField`
- Gunakan ProGuard di release build untuk proteksi
- Pakai `BuildConfig.DEBUG` buat bedain log debug vs release

---

## 🚀 Kesimpulan

- Build Variant bikin hidup lebih fleksibel: satu codebase, banyak versi app
- Gradle = dalang yang nyulap semua itu jadi APK siap install
- Kuasai ini, kamu udah masuk ke level developer yang lebih "pro" 🔥

---

Selanjutnya: Kita masuk ke **Testing & Debugging**, karena developer sejati gak takut sama error 😎🛠️

