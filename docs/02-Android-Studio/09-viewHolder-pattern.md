# 🧱 ViewHolder Pattern di Android

**ViewHolder Pattern** adalah teknik yang digunakan untuk mengoptimalkan performa list atau RecyclerView dengan cara **menghindari pemanggilan `findViewById()` berulang-ulang**.

Kalau RecyclerView ibarat restoran, maka ViewHolder adalah pelayan yang hafal letak sendok, garpu, dan menu—jadi nggak perlu cari-cari lagi. 🔍🍴

---

## ❓ Kenapa Harus Pakai ViewHolder?

Tanpa ViewHolder:
- `findViewById()` dipanggil setiap kali item dibuat ulang.
- Ini boros waktu dan performa, terutama kalau list panjang.

Dengan ViewHolder:
- Semua komponen UI disimpan 1x di objek ViewHolder.
- Reuse view lama → hemat memori & waktu render.

---

## 🏗️ Struktur ViewHolder di RecyclerView.Adapter

```java
public class MyAdapter extends RecyclerView.Adapter<MyAdapter.MyViewHolder> {

    public class MyViewHolder extends RecyclerView.ViewHolder {
        TextView myText;

        public MyViewHolder(View itemView) {
            super(itemView);
            myText = itemView.findViewById(R.id.myText);
        }
    }

    @Override
    public MyViewHolder onCreateViewHolder(ViewGroup parent, int viewType) {
        View v = LayoutInflater.from(parent.getContext())
                .inflate(R.layout.item_layout, parent, false);
        return new MyViewHolder(v);
    }

    @Override
    public void onBindViewHolder(MyViewHolder holder, int position) {
        holder.myText.setText("Item ke-" + position);
    }

    @Override
    public int getItemCount() {
        return 10;
    }
}
```

---

## 📊 Perbandingan Tanpa vs Dengan ViewHolder

| Tanpa ViewHolder | Dengan ViewHolder |
|------------------|-------------------|
| `findViewById()` dipanggil terus | Dipanggil sekali saja |
| Lebih lambat | Lebih cepat |
| Lebih banyak konsumsi memori | Lebih hemat memori |
| Bisa lag saat scroll | Scroll lebih smooth 🚀 |

---

## 💡 Tips Optimalisasi Tambahan

- Gunakan `ViewBinding` agar lebih aman dan modern daripada `findViewById()`.
- Hindari melakukan operasi berat (misal hitung bitmap) di `onBindViewHolder()`.
- Gunakan `DiffUtil` untuk list dinamis biar nggak reload semua data.

---

## 🧪 Challenge

Buat list item dengan komponen:
- Gambar (ImageView)
- Nama barang (TextView)
- Harga (TextView)

Implementasikan `ViewHolder` agar tiap elemen hanya dicari 1x!

---

## 🧭 Kesimpulan

ViewHolder Pattern = Salah satu pondasi performa tinggi di Android.
Tanpa ini? RecyclerView-mu bakal lemot, boros, dan bikin user manyun. 🐌

Dengan ini? Scroll smooth, user senyum. 😎📱

--- 

Selanjutnya: Yuk lanjut ke **Fragments**, **Navigation Component**, atau **SharedPreferences** buat simpan data lokal!

