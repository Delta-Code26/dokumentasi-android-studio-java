# 🧭 Intent & Navigasi Antar Activity

## 🎯 Apa Itu Intent?

> **Intent** adalah pesan yang digunakan untuk berpindah antar komponen Android. Biasanya digunakan untuk:
- Navigasi antar **Activity**
- Kirim data antar halaman
- Buka app lain (kamera, maps, dsb.)

---

## 📦 Jenis-Jenis Intent

| Jenis       | Keterangan                                |
|-------------|--------------------------------------------|
| Explicit    | Navigasi ke Activity tertentu dalam app    |
| Implicit    | Meminta sistem Android untuk pilih app     |

---

## 🚀 Contoh Explicit Intent

```java
Intent intent = new Intent(MainActivity.this, SecondActivity.class);
startActivity(intent);
```

💡 *Digunakan untuk pindah dari `MainActivity` ke `SecondActivity`.*

---

## 🎁 Kirim Data Antar Activity

```java
Intent intent = new Intent(this, SecondActivity.class);
intent.putExtra("username", "delta_code");
startActivity(intent);
```

Lalu di `SecondActivity`:

```java
String username = getIntent().getStringExtra("username");
```

🧠 **Catatan:** Data yang dikirim bisa `String`, `int`, `boolean`, bahkan objek dengan `Parcelable`.

---

## 🔄 Menerima Data Balik (`startActivityForResult`)

> Untuk menerima data balik dari activity lain:

```java
Intent intent = new Intent(this, EditProfileActivity.class);
startActivityForResult(intent, 1);
```

Lalu override `onActivityResult`:

```java
@Override
protected void onActivityResult(int requestCode, int resultCode, Intent data) {
    if (requestCode == 1 && resultCode == RESULT_OK) {
        String hasil = data.getStringExtra("nama_baru");
    }
}
```

---

## 🧩 Contoh Implicit Intent

```java
Intent intent = new Intent(Intent.ACTION_VIEW);
intent.setData(Uri.parse("https://google.com"));
startActivity(intent);
```

💡 Bisa juga untuk:
- Membuka maps
- Kirim email
- Ambil foto dari kamera

---

## 🧠 Best Practice

- Gunakan **Intent** hanya untuk navigasi ringan
- Gunakan **Jetpack Navigation Component** jika aplikasi besar dan kompleks
- Jangan kirim data terlalu besar via intent, pakai `SharedPreferences` atau `Database`

---

## 🔥 Mini Quiz

**Q:** Apa beda `putExtra()` dan `startActivityForResult()`?

**A:**  
- `putExtra()` → Kirim data ke activity lain  
- `startActivityForResult()` → Kirim dan tunggu balasan

