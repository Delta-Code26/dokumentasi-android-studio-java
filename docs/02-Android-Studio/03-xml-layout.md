# 🖼️ XML Layout di Android Studio

XML layout adalah bahasa markup (bukan coding logic) yang dipakai untuk mendesain **UI (User Interface)** di Android. Jadi, kalo kamu mau bikin tampilan tombol, teks, inputan, dll, semuanya diatur di file XML ini.

---

## 🧱 Struktur Dasar XML Layout

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <TextView
        android:id="@+id/text_hello"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Halo Dunia!" />

</LinearLayout>
```

### Penjelasan:
- `LinearLayout` → layout utama (bisa horizontal/vertical)
- `TextView` → komponen teks
- `android:` → atribut-atribut dari komponen

---

## 📐 Ukuran Layout

| Atribut            | Fungsi                             |
|--------------------|-------------------------------------|
| `match_parent`     | Mengisi ruang sebanyak mungkin      |
| `wrap_content`     | Menyesuaikan ukuran kontennya      |
| `dp`               | Density Pixel (ukuran elemen)       |
| `sp`               | Scale Pixel (ukuran teks)           |

---

## 🔤 Komponen Umum di XML

| Komponen      | Keterangan                            |
|---------------|----------------------------------------|
| `TextView`    | Menampilkan teks                      |
| `EditText`    | Input teks dari user                  |
| `Button`      | Tombol untuk aksi                     |
| `ImageView`   | Menampilkan gambar                   |
| `RecyclerView`| Daftar dinamis (mirip list)          |

---

## 🧩 Jenis Layout Populer

### 1. `LinearLayout`
- Menyusun komponen **secara vertikal/horizontal**
```xml
android:orientation="vertical"
```

### 2. `RelativeLayout`
- Menyusun elemen **berdasarkan posisi relatif antar elemen**

### 3. `ConstraintLayout` ✅ (Paling fleksibel!)
- Menyusun UI secara **dinamis dan efisien**
- Cocok untuk layout kompleks

---

## 🛠️ Tools Pendukung di Android Studio

- **Design View**: Drag & drop UI
- **Code View**: Edit langsung XML-nya
- **Split View**: Lihat keduanya barengan (rekomendasi!)

---

## ⚡ Contoh UI Sederhana

```xml
<LinearLayout
    android:orientation="vertical"
    android:padding="16dp"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:text="Nama"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"/>

    <EditText
        android:id="@+id/edit_nama"
        android:hint="Masukkan nama"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"/>

    <Button
        android:text="Simpan"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"/>
</LinearLayout>
```

---

## 🧪 Quiz Cepat

> Q: Apa perbedaan `match_parent` dan `wrap_content`?  
> A: `match_parent` mengisi ruang maksimal, `wrap_content` menyesuaikan isi.

> Q: Layout apa yang paling fleksibel di Android?  
> A: `ConstraintLayout`.
