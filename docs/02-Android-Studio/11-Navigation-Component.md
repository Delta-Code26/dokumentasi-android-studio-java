# 🧭 Navigation Component

Navigation Component adalah bagian dari Android Jetpack yang bikin kamu bisa **pindah antar Fragment dengan mudah dan rapi**, tanpa ribet coding manual pakai `FragmentTransaction`.

Bayangin Navigation Component kayak **Google Maps-nya aplikasi kamu** — ngatur rute dari satu layar ke layar lain, dengan safety & auto-backstack built-in. 🚗🗺️

---

## ✨ Fitur Utama

- Navigasi antar Fragment jadi lebih mudah.
- Backstack otomatis.
- Bisa pakai Safe Args (ngirim data antar fragment dengan aman).
- Mendukung Bottom Navigation, Drawer Navigation, dan Deep Link.

---

## 🧰 Instalasi dan Setup

### 1. Tambahkan dependency di `build.gradle (app)`

```gradle
// Navigation Component
implementation "androidx.navigation:navigation-fragment-ktx:2.7.7"
implementation "androidx.navigation:navigation-ui-ktx:2.7.7"

// Safe Args Plugin (di level project)
classpath "androidx.navigation:navigation-safe-args-gradle-plugin:2.7.7"
```

> Jangan lupa apply plugin di `build.gradle (app)`:
```gradle
apply plugin: 'androidx.navigation.safeargs'
```

---

## 🏗️ Membuat Navigation Graph

1. Klik kanan folder `res` → New → Android Resource File.
2. File name: `nav_graph.xml`
3. Resource type: `navigation`

### Isi contoh:
```xml
<?xml version="1.0" encoding="utf-8"?>
<navigation xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    app:startDestination="@id/homeFragment">

    <fragment
        android:id="@+id/homeFragment"
        android:name="com.example.app.HomeFragment"
        android:label="Home" >
        <action
            android:id="@+id/action_home_to_detail"
            app:destination="@id/detailFragment" />
    </fragment>

    <fragment
        android:id="@+id/detailFragment"
        android:name="com.example.app.DetailFragment"
        android:label="Detail" />
</navigation>
```

---

## 🧩 Tambahkan NavHost di `activity_main.xml`

```xml
<androidx.fragment.app.FragmentContainerView
    android:id="@+id/nav_host_fragment"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    app:navGraph="@navigation/nav_graph"
    android:name="androidx.navigation.fragment.NavHostFragment"
    app:defaultNavHost="true" />
```

---

## 🔀 Navigasi antar Fragment

### Dengan ID Action:
```java
NavController navController = Navigation.findNavController(view);
navController.navigate(R.id.action_home_to_detail);
```

### Menggunakan Safe Args:
```java
HomeFragmentDirections.ActionHomeToDetail action =
    HomeFragmentDirections.actionHomeToDetail();
action.setUserId(5);
navController.navigate(action);
```

Lalu di DetailFragment:
```java
int userId = DetailFragmentArgs.fromBundle(getArguments()).getUserId();
```

---

## 📦 Integrasi dengan BottomNavigationView

```java
NavController navController = Navigation.findNavController(this, R.id.nav_host_fragment);
NavigationUI.setupWithNavController(bottomNavigationView, navController);
```

---

## 💡 Tips Pro

- Gunakan Safe Args biar ngirim data antar Fragment aman dari typo.
- Jangan hardcode action! Gunakan ID dari `nav_graph.xml`.
- Manfaatkan fitur `popUpTo` dan `popUpToInclusive` untuk kontrol backstack.

---

## 🧪 Latihan

1. Buat `LoginFragment` dan `DashboardFragment`.
2. Tambahkan tombol "Login" → navigasikan ke dashboard.
3. Kirim nama user menggunakan Safe Args.

---

## ✅ Kesimpulan

Navigation Component = solusi modern buat pindah antar Fragment tanpa ribet.  
Lebih rapi, lebih aman, dan lebih Android Jetpack banget. 🚀

---

Selanjutnya: Yuk lanjut ke **SharedPreferences**, biar data kecil (seperti login state) bisa disimpan dengan aman dan mudah!

