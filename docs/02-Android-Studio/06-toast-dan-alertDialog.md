# 🔔 Toast & AlertDialog di Android

Saat bikin aplikasi Android, penting banget untuk bisa memberi feedback ke user. Dua cara paling umum dan simpel adalah menggunakan **Toast** dan **AlertDialog**. Yuk, kita bahas!

---

## 🥯 Apa Itu Toast?

> **Toast** adalah pesan singkat yang muncul sementara di layar dan akan hilang sendiri.

### ✅ Contoh Sederhana

```java
Toast.makeText(this, "Halo dunia!", Toast.LENGTH_SHORT).show();
```

### ⚙️ Penjelasan Parameter:
- `this` → Context (biasanya activity saat ini)
- `"Halo dunia!"` → Pesan yang ditampilkan
- `Toast.LENGTH_SHORT` → Durasi tampil (`SHORT` atau `LONG`)

---

## 📦 Toast Custom

Kamu bisa bikin Toast yang lebih kece dengan layout sendiri:

```java
LayoutInflater inflater = getLayoutInflater();
View layout = inflater.inflate(R.layout.custom_toast, null);

Toast toast = new Toast(getApplicationContext());
toast.setDuration(Toast.LENGTH_LONG);
toast.setView(layout);
toast.show();
```

> Pastikan punya file `custom_toast.xml` di folder `res/layout`.

---

## 💬 Apa Itu AlertDialog?

> **AlertDialog** adalah popup interaktif yang menampilkan pesan dan bisa punya tombol aksi.

---

## 📋 Contoh AlertDialog Sederhana

```java
new AlertDialog.Builder(this)
    .setTitle("Konfirmasi")
    .setMessage("Apakah kamu yakin ingin keluar?")
    .setPositiveButton("Ya", (dialog, which) -> {
        // aksi ketika klik Ya
        finish();
    })
    .setNegativeButton("Batal", null)
    .show();
```

---

## 🧠 Fungsi Tombol:
- `.setPositiveButton()` → Tombol utama (biasanya "Ya", "OK", dsb)
- `.setNegativeButton()` → Tombol batal
- `.setNeutralButton()` → Tombol tambahan (jika ada)

---

## 🔐 AlertDialog dengan Input

```java
EditText input = new EditText(this);

new AlertDialog.Builder(this)
    .setTitle("Input Nama")
    .setView(input)
    .setPositiveButton("OK", (dialog, which) -> {
        String nama = input.getText().toString();
        Toast.makeText(this, "Halo, " + nama, Toast.LENGTH_SHORT).show();
    })
    .setNegativeButton("Batal", null)
    .show();
```

---

## 🔄 Kapan Pakai Apa?

| Kondisi                           | Gunakan          |
|-----------------------------------|------------------|
| Tampilkan info singkat            | **Toast**        |
| Butuh aksi dari user (ya/tidak)   | **AlertDialog**  |
| Butuh konfirmasi penting          | **AlertDialog**  |
| Notifikasi background             | 🔔 Gunakan **NotificationManager**

---

## 🔥 Mini Challenge

Buat tombol "Keluar" di aplikasimu. Saat ditekan, munculkan `AlertDialog` yang meminta konfirmasi sebelum keluar.  
Kalau user pilih "Ya", aplikasi ditutup. Kalau "Tidak", dialog ditutup aja.

