# 🎨 Custom Dialog dan Bottom Sheet di Android

> Custom Dialog dan Bottom Sheet adalah komponen antarmuka yang digunakan untuk menampilkan informasi atau meminta input pengguna tanpa mengganggu tampilan utama aplikasi.

---

## 📚 Apa Itu Custom Dialog dan Bottom Sheet?

- **Custom Dialog**: Dialog yang dikustomisasi oleh pengembang untuk memenuhi desain dan fungsionalitas aplikasi. Ini lebih fleksibel dibandingkan dialog bawaan Android.
- **Bottom Sheet**: Komponen UI yang muncul dari bawah layar, sering digunakan untuk menampilkan lebih banyak opsi atau informasi tanpa menutupi seluruh layar. Bottom Sheet dapat berupa modal (harus ditutup) atau tidak modal (dapat disembunyikan dengan swipe).

---

## 🚀 Implementasi Custom Dialog

Custom Dialog memungkinkan kamu untuk menyesuaikan tampilan dan fungsionalitas dialog sesuai kebutuhan aplikasi. Kamu bisa menambahkan berbagai elemen UI seperti EditText, Button, TextView, dan lainnya di dalam dialog.

### 1. **Membuat Custom Dialog**

Berikut adalah langkah-langkah untuk membuat custom dialog di Android.

#### a. **Buat Layout untuk Dialog**

Buat file XML untuk layout dialog. Misalnya, `dialog_custom.xml`:

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:padding="16dp"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content">

    <TextView
        android:id="@+id/dialog_title"
        android:text="Masukkan Nama"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textSize="18sp"
        android:paddingBottom="8dp"/>

    <EditText
        android:id="@+id/edt_name"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Nama" />

    <Button
        android:id="@+id/btn_ok"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="OK"
        android:layout_gravity="end"
        android:paddingTop="16dp"/>
</LinearLayout>
```

#### b. **Membuat Dialog di Activity atau Fragment**

Setelah membuat layout, sekarang kamu bisa menampilkan dialog di dalam activity atau fragment.

```java
AlertDialog.Builder builder = new AlertDialog.Builder(this);
View customLayout = getLayoutInflater().inflate(R.layout.dialog_custom, null);
builder.setView(customLayout);

EditText edtName = customLayout.findViewById(R.id.edt_name);
Button btnOk = customLayout.findViewById(R.id.btn_ok);

btnOk.setOnClickListener(v -> {
    String name = edtName.getText().toString();
    Toast.makeText(getApplicationContext(), "Nama: " + name, Toast.LENGTH_SHORT).show();
});

builder.create().show();
```

Dialog ini akan menampilkan input form dengan `EditText` dan tombol `OK` yang dapat di-klik untuk mengambil input pengguna.

---

## 🚀 Implementasi Bottom Sheet

Bottom Sheet adalah komponen UI yang muncul dari bawah layar dan dapat digunakan untuk menampilkan menu atau informasi tambahan.

### 1. **Membuat Bottom Sheet**

Untuk membuat Bottom Sheet, kamu bisa menggunakan `BottomSheetDialogFragment`, yang memungkinkan tampilan bottom sheet lebih fleksibel.

#### a. **Buat Layout untuk Bottom Sheet**

Buat layout untuk bottom sheet, misalnya `bottom_sheet_layout.xml`:

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="wrap_content">

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Pilih Opsi"
        android:textSize="18sp"
        android:padding="16dp"
        android:background="?android:attr/windowBackground" />

    <Button
        android:id="@+id/btn_option_1"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Opsi 1" />

    <Button
        android:id="@+id/btn_option_2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Opsi 2" />
</LinearLayout>
```

#### b. **Buat BottomSheetDialogFragment**

Sekarang buat kelas `BottomSheetFragment` yang meng-extend `BottomSheetDialogFragment`:

```java
public class BottomSheetFragment extends BottomSheetDialogFragment {

    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {
        View view = inflater.inflate(R.layout.bottom_sheet_layout, container, false);
        
        Button btnOption1 = view.findViewById(R.id.btn_option_1);
        Button btnOption2 = view.findViewById(R.id.btn_option_2);
        
        btnOption1.setOnClickListener(v -> {
            Toast.makeText(getContext(), "Opsi 1 dipilih", Toast.LENGTH_SHORT).show();
            dismiss();
        });
        
        btnOption2.setOnClickListener(v -> {
            Toast.makeText(getContext(), "Opsi 2 dipilih", Toast.LENGTH_SHORT).show();
            dismiss();
        });
        
        return view;
    }
}
```

#### c. **Menampilkan Bottom Sheet**

Untuk menampilkan bottom sheet, cukup panggil `show()` dari `BottomSheetDialogFragment`.

```java
BottomSheetFragment bottomSheetFragment = new BottomSheetFragment();
bottomSheetFragment.show(getSupportFragmentManager(), bottomSheetFragment.getTag());
```

---

## 🎨 Perbedaan Antara Custom Dialog dan Bottom Sheet

- **Custom Dialog**: Digunakan untuk menampilkan informasi atau meminta input pengguna dalam bentuk jendela pop-up.
- **Bottom Sheet**: Menampilkan menu atau informasi tambahan dari bawah layar. Biasanya digunakan untuk opsi atau data yang tidak terlalu mendesak dan lebih cocok ditampilkan di bagian bawah layar.

---

## ⚡ Tips & Best Practices

- **Gunakan Dialog dengan Bijak**: Pastikan kamu menggunakan custom dialog dan bottom sheet hanya ketika diperlukan. Penggunaan yang berlebihan dapat membuat aplikasi terasa penuh dengan interupsi.
- **Sesuaikan Tampilan dengan Desain Aplikasi**: Kedua komponen ini harus disesuaikan dengan tema aplikasi dan desain antarmuka untuk pengalaman pengguna yang lebih baik.
- **Animasi**: Gunakan animasi transisi untuk membuat perubahan antara tampilan utama dan dialog atau bottom sheet lebih halus dan tidak mengganggu.

---

## 💬 Kesimpulan

- **Custom Dialog** memberi kontrol penuh terhadap tampilan dan fungsi dialog, memungkinkan kamu membuat antarmuka yang lebih interaktif dan kaya fitur.
- **Bottom Sheet** memberikan cara untuk menampilkan informasi atau menu tambahan dengan cara yang lebih modern dan elegan.
- Keduanya adalah komponen UI yang penting dalam membuat aplikasi Android lebih interaktif dan responsif terhadap kebutuhan pengguna.

> "Dengan Custom Dialog dan Bottom Sheet, aplikasi kamu bisa menawarkan pengalaman pengguna yang lebih interaktif tanpa mengganggu navigasi utama!" 🎨