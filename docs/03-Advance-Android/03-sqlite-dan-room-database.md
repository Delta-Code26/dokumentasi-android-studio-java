# 💾 SQLite & Room Database di Android

> Mau nyimpen data lebih kompleks dan terstruktur? Waktunya upgrade dari SharedPreferences ke SQLite atau Room! 📊

---

## 🧱 Apa Itu SQLite?

SQLite adalah **embedded database** bawaan Android yang ringan dan powerful. Cocok buat menyimpan data lokal seperti:

- Data user
- Catatan
- Riwayat transaksi
- Data panen sawit (🔥 cocok banget buat kamu nih!)

Namun, pengelolaan SQLite **cukup ribet** (bikin helper, query manual). Nah, makanya ada...

---

## 🧠 Room Database: Versi Lebih Modern

Room adalah **abstraksi** di atas SQLite. Dia bikin kita bisa:

- Gunakan **annotation + interface** → auto generate SQL-nya
- Hindari typo query SQL
- Terintegrasi dengan LiveData dan ViewModel

---

## 🔧 Struktur Room

1. **Entity**: Representasi tabel
2. **DAO (Data Access Object)**: Interface berisi query
3. **Database**: Abstraksi database

---

## 🧪 Contoh Implementasi Room

### 1. Tambahkan Dependency

```groovy
dependencies {
    implementation "androidx.room:room-runtime:2.6.1"
    annotationProcessor "androidx.room:room-compiler:2.6.1"
}
```

---

### 2. Entity (Tabel)

```java
@Entity
public class Panen {
    @PrimaryKey(autoGenerate = true)
    public int id;

    public String namaPekerja;
    public int jumlahKg;
    public String tanggal;
}
```

---

### 3. DAO (Query Interface)

```java
@Dao
public interface PanenDao {
    @Insert
    void insert(Panen panen);

    @Query("SELECT * FROM Panen")
    List<Panen> getAll();

    @Delete
    void delete(Panen panen);
}
```

---

### 4. Database

```java
@Database(entities = {Panen.class}, version = 1)
public abstract class AppDatabase extends RoomDatabase {
    public abstract PanenDao panenDao();
}
```

---

### 5. Gunakan di Activity

```java
AppDatabase db = Room.databaseBuilder(
        getApplicationContext(),
        AppDatabase.class, "panen-db"
).allowMainThreadQueries().build();

Panen panen = new Panen();
panen.namaPekerja = "Marno";
panen.jumlahKg = 85;
panen.tanggal = "2025-04-20";

db.panenDao().insert(panen);
```

> ⚠️ Jangan gunakan `.allowMainThreadQueries()` di project asli. Gunakan background thread!

---

## ⚔ SQLite Manual vs Room

| Fitur               | SQLite Manual | Room              |
|--------------------|---------------|-------------------|
| Menulis Query SQL  | Manual        | Otomatis (Annotation) |
| Validasi Query     | Tidak ada     | Ada (Compile time) |
| Error-prone        | Tinggi        | Rendah            |
| Boilerplate        | Banyak        | Lebih sedikit     |

---

## 📌 Tips

- Simpan database besar atau penting seperti data gaji, rekap panen, dan blok kebun di Room.
- Untuk data besar, gunakan `Paging3` dan `Flow`.
- Gunakan `ViewModel` + `LiveData` untuk menghubungkan ke UI.

---

## 🎯 Studi Kasus: Aplikasi Panen Sawit

Buat database `rekap_panen`, tabel `Panen`, dengan kolom:
- `id`
- `id_pekerja`
- `nama`
- `berat_kg`
- `tanggal`

CRUD-nya bisa langsung dijalankan dari Room! Cocok banget buat proyek Android + backend Python kamu nanti 🚀

---

## 💬 Kesimpulan

- SQLite = powerful tapi ribet
- Room = modern, aman, dan lebih praktis
- Room cocok banget buat aplikasi skala kecil hingga menengah
- Gunakan SQLite manual hanya jika kamu pengen nostalgia dan ingin merasakan derita 😅

---

> “Kalau SharedPreferences itu kayak catatan tempel, Room itu kayak buku kas harian lengkap.” 🧾📘

Gas lanjut ke background task: Handler, AsyncTask, dan kawan-kawan 💡🧵