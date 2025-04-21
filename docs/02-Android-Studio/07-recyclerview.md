# 🌀 RecyclerView di Android Studio

`RecyclerView` adalah salah satu komponen UI paling powerful di Android. Ini digunakan untuk menampilkan list data yang panjang secara efisien.

Kalau kamu pernah lihat daftar chat di WhatsApp atau feed di Instagram — yep, itu pakai RecyclerView!

---

## 🤔 Kenapa RecyclerView?

RecyclerView adalah versi upgrade dari `ListView`. Dibanding `ListView`, RecyclerView:
- Lebih fleksibel dan customizable
- Lebih efisien (recycle item view yang keluar dari layar)
- Dukungan layout yang lebih variatif (grid, linear, staggered, dll)

---

## 🧱 Komponen Utama RecyclerView

1. **RecyclerView** → View utama yang nampilin list
2. **LayoutManager** → Menentukan tampilan list (vertikal, grid, dll)
3. **Adapter** → Menghubungkan data dengan tampilan
4. **ViewHolder** → Menyimpan view tiap item agar tidak inflate ulang

---

## 🧪 Langkah Implementasi RecyclerView

### 1️⃣ Tambahkan RecyclerView di layout XML

```xml
<androidx.recyclerview.widget.RecyclerView
    android:id="@+id/recyclerView"
    android:layout_width="match_parent"
    android:layout_height="match_parent"/>
```

---

### 2️⃣ Buat layout untuk item list

Contoh: `item_mahasiswa.xml`

```xml
<TextView
    android:id="@+id/textNama"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Nama Mahasiswa" />
```

---

### 3️⃣ Buat kelas data (model)

```java
public class Mahasiswa {
    String nama;

    public Mahasiswa(String nama) {
        this.nama = nama;
    }

    public String getNama() {
        return nama;
    }
}
```

---

### 4️⃣ Buat ViewHolder + Adapter

```java
public class MahasiswaAdapter extends RecyclerView.Adapter<MahasiswaAdapter.ViewHolder> {
    List<Mahasiswa> listMahasiswa;

    public MahasiswaAdapter(List<Mahasiswa> list) {
        this.listMahasiswa = list;
    }

    public class ViewHolder extends RecyclerView.ViewHolder {
        TextView textNama;

        public ViewHolder(View itemView) {
            super(itemView);
            textNama = itemView.findViewById(R.id.textNama);
        }
    }

    @Override
    public ViewHolder onCreateViewHolder(ViewGroup parent, int viewType) {
        View v = LayoutInflater.from(parent.getContext()).inflate(R.layout.item_mahasiswa, parent, false);
        return new ViewHolder(v);
    }

    @Override
    public void onBindViewHolder(ViewHolder holder, int position) {
        Mahasiswa mhs = listMahasiswa.get(position);
        holder.textNama.setText(mhs.getNama());
    }

    @Override
    public int getItemCount() {
        return listMahasiswa.size();
    }
}
```

---

### 5️⃣ Pasang RecyclerView di Activity

```java
RecyclerView recyclerView = findViewById(R.id.recyclerView);
recyclerView.setLayoutManager(new LinearLayoutManager(this));

List<Mahasiswa> data = new ArrayList<>();
data.add(new Mahasiswa("Budi"));
data.add(new Mahasiswa("Siti"));
data.add(new Mahasiswa("Ahmad"));

MahasiswaAdapter adapter = new MahasiswaAdapter(data);
recyclerView.setAdapter(adapter);
```

---

## 💡 Tips Tambahan

- Gunakan `GridLayoutManager` untuk tampilan grid (seperti galeri).
- Bisa tambahkan fitur klik item pakai `itemView.setOnClickListener(...)` di ViewHolder.
- RecyclerView sangat cocok untuk data dari database atau API!

---

## 🔥 Challenge

Buat daftar produk dengan RecyclerView. Setiap item menampilkan nama, harga, dan tombol "Beli".

Bonus: Tampilkan `Toast` saat tombol "Beli" diklik!

