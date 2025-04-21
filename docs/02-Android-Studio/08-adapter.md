# 🔁 Adapter di Android (RecyclerView Adapter)

Adapter adalah jembatan antara **data** dan **UI**. Dia yang "nyuapin" data ke komponen seperti RecyclerView. Tanpa adapter, RecyclerView nggak bisa nampilin apa-apa!

---

## 🧠 Pengertian Adapter

Secara umum:
> Adapter = penghubung antara sumber data (Array, List, dsb.) dan tampilan visual (View di layout).

Di RecyclerView:
- Adapter bertugas:
  - Membuat ViewHolder (item UI)
  - Menghubungkan data ke setiap item
  - Memberi tahu RecyclerView berapa banyak data yang harus ditampilkan

---

## ⚙️ Struktur Dasar RecyclerView.Adapter

```java
public class MyAdapter extends RecyclerView.Adapter<MyAdapter.MyViewHolder> {
    private List<String> dataList;

    public MyAdapter(List<String> dataList) {
        this.dataList = dataList;
    }

    public class MyViewHolder extends RecyclerView.ViewHolder {
        TextView myText;

        public MyViewHolder(View itemView) {
            super(itemView);
            myText = itemView.findViewById(R.id.myText);
        }
    }

    @Override
    public MyViewHolder onCreateViewHolder(ViewGroup parent, int viewType) {
        View v = LayoutInflater.from(parent.getContext()).inflate(R.layout.item_layout, parent, false);
        return new MyViewHolder(v);
    }

    @Override
    public void onBindViewHolder(MyViewHolder holder, int position) {
        String item = dataList.get(position);
        holder.myText.setText(item);
    }

    @Override
    public int getItemCount() {
        return dataList.size();
    }
}
```

---

## 📦 Penjelasan Fungsi Penting

| Fungsi | Penjelasan |
|--------|------------|
| `onCreateViewHolder` | Buat layout item (inflate) |
| `onBindViewHolder` | Pasang data ke tampilan item |
| `getItemCount` | Jumlah data yang akan ditampilkan |
| `ViewHolder` | Menyimpan referensi view untuk tiap item (biar gak inflate ulang) |

---

## 🚀 Contoh Kasus: List Nama Mahasiswa

**Model:**

```java
public class Mahasiswa {
    String nama;
    public Mahasiswa(String nama) { this.nama = nama; }
    public String getNama() { return nama; }
}
```

**Layout item_mahasiswa.xml:**

```xml
<TextView
    android:id="@+id/textNama"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Nama Mahasiswa" />
```

**Adapter-nya:**

```java
public class MahasiswaAdapter extends RecyclerView.Adapter<MahasiswaAdapter.ViewHolder> {
    private List<Mahasiswa> list;

    public MahasiswaAdapter(List<Mahasiswa> list) {
        this.list = list;
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
        Mahasiswa m = list.get(position);
        holder.textNama.setText(m.getNama());
    }

    @Override
    public int getItemCount() {
        return list.size();
    }
}
```

---

## 🎯 Tips Pro

- Adapter bisa di-*reuse*, tinggal ganti model data.
- Gunakan `notifyDataSetChanged()` jika data berubah.
- Untuk klik item, tambahkan `setOnClickListener` di `onBindViewHolder`.

---

## 🔥 Challenge

Buat `ProductAdapter` yang menampilkan:
- Nama produk
- Harga produk
- Gambar produk (gunakan ImageView)
- Tombol "Beli" → kasih aksi Toast

---

## 🧭 Kesimpulan

Adapter itu kayak waiternya RecyclerView. Dia yang ambil data dari dapur (model), terus nyajiin ke meja makan (UI). Tanpa adapter, UI-mu bakal kelaparan! 🍽️📱

Yuk lanjut belajar `Fragments` atau `Room Database` di bagian lanjut! 🛠️🔥

--- 

Semakin mahir Adapter = makin fleksibel bikin UI Android!