# 🗂 Shared Preferences di Android

> Mau simpan data kecil seperti username, dark mode on/off, atau status login user? Pakai **SharedPreferences** aja! Simpel, cepat, cocok buat penyimpanan ringan. ⚡

---

## 📌 Apa Itu SharedPreferences?

SharedPreferences adalah mekanisme penyimpanan data key-value yang bersifat **persisten** (tetap ada meski aplikasi ditutup), dan cocok untuk:

- Menyimpan data primitive: `String`, `int`, `boolean`, dll.
- Tidak cocok untuk data besar atau kompleks (gunakan Room/SQLite untuk itu).

---

## ✅ Contoh Kasus Penggunaan

- Menyimpan status login (user sudah login atau belum)
- Menyimpan setting aplikasi seperti tema, bahasa
- Menyimpan nama user atau token auth

---

## 🛠 Cara Menggunakan SharedPreferences

### 1. Menyimpan Data

```java
SharedPreferences sharedPreferences = getSharedPreferences("MyPrefs", MODE_PRIVATE);
SharedPreferences.Editor editor = sharedPreferences.edit();

editor.putString("username", "marno123");
editor.putBoolean("isLoggedIn", true);
editor.apply(); // atau editor.commit();
```

> `apply()` menyimpan secara async, `commit()` secara sync.

---

### 2. Mengambil Data

```java
SharedPreferences sharedPreferences = getSharedPreferences("MyPrefs", MODE_PRIVATE);

String username = sharedPreferences.getString("username", "Guest");
boolean isLoggedIn = sharedPreferences.getBoolean("isLoggedIn", false);
```

---

### 3. Menghapus Data

```java
SharedPreferences sharedPreferences = getSharedPreferences("MyPrefs", MODE_PRIVATE);
SharedPreferences.Editor editor = sharedPreferences.edit();

editor.remove("username"); // hapus satu key
editor.clear();            // hapus semua data
editor.apply();
```

---

## 📦 Lokasi Penyimpanan

Data SharedPreferences disimpan di:
```
/data/data/<nama.package.aplikasi>/shared_prefs/MyPrefs.xml
```
Dan bersifat **private**, tidak bisa diakses oleh aplikasi lain.

---

## 🧠 Tips & Best Practice

- Gunakan satu file prefs untuk satu kategori (misal `userPrefs`, `settingPrefs`)
- Hindari menyimpan data sensitif seperti password mentah! (gunakan encryption)
- Hindari menyimpan data terlalu besar

---

## 📋 Contoh Skenario Login Sederhana

### LoginActivity.java

```java
if (username.equals("admin") && password.equals("123")) {
    SharedPreferences sharedPref = getSharedPreferences("loginPrefs", MODE_PRIVATE);
    sharedPref.edit().putBoolean("isLoggedIn", true).apply();
    
    startActivity(new Intent(this, DashboardActivity.class));
    finish();
}
```

### DashboardActivity.java

```java
SharedPreferences sharedPref = getSharedPreferences("loginPrefs", MODE_PRIVATE);
boolean isLoggedIn = sharedPref.getBoolean("isLoggedIn", false);

if (!isLoggedIn) {
    startActivity(new Intent(this, LoginActivity.class));
    finish();
}
```

---

## 💬 Kesimpulan

- SharedPreferences = solusi simpel buat simpan data kecil
- Mudah dipakai dan cocok buat setting, login, dan state ringan
- Kalau data makin kompleks, pindahlah ke database (Room, SQLite)

---

> Simpan data kecil? SharedPreferences siap bantu. Tapi kalau kamu nyimpen daftar panen sawit full bulan Desember di sini, siap-siap HP-nya meledak 😆🌴💥
