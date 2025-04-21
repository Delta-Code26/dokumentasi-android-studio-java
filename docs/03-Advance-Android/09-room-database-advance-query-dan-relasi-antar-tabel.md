# 🗃️ Room Database: Advanced Query dan Relasi Antar Tabel

> **Room Database** adalah library untuk mengakses database SQLite secara efisien di Android. Dalam dokumentasi ini, kita akan menggali lebih dalam tentang query lanjutan dan relasi antar tabel untuk mengoptimalkan penggunaan Room.

---

## 📚 Pengantar

Room menyediakan cara yang lebih aman dan efisien untuk mengakses database SQLite. Selain mendukung operasi dasar seperti `INSERT`, `UPDATE`, dan `DELETE`, Room juga memungkinkan kita untuk membuat query kompleks dan menangani relasi antar tabel dengan mudah.

---

## 🔍 Advanced Queries di Room

### 1. **Query dengan @Query**

`@Query` memungkinkan kita menulis query SQL yang lebih kompleks. Kita bisa menulis berbagai jenis query seperti `SELECT`, `UPDATE`, `DELETE`, dan lainnya.

#### a. **Contoh Query SELECT dengan Kondisi**

```java
@Dao
public interface UserDao {

    @Query("SELECT * FROM users WHERE age > :age")
    List<User> getUsersOlderThan(int age);
}
```

Pada contoh ini, kita menggunakan parameter `age` untuk mencari pengguna yang lebih tua dari nilai yang diberikan.

#### b. **Query untuk Menghitung Data**

```java
@Dao
public interface UserDao {

    @Query("SELECT COUNT(*) FROM users")
    int getUserCount();
}
```

Dengan query di atas, kita dapat menghitung jumlah baris di tabel `users`.

### 2. **Query dengan Join**

Room memungkinkan kita untuk membuat query dengan `JOIN` antara dua tabel. Misalnya, kita ingin menggabungkan data dari dua tabel `users` dan `orders`:

```java
@Dao
public interface UserOrderDao {

    @Transaction
    @Query("SELECT * FROM users WHERE userId = :userId")
    public UserWithOrders getUserWithOrders(int userId);
}
```

Pada query di atas, kita menggunakan anotasi `@Transaction` untuk memastikan transaksi berjalan dengan baik. Kelas `UserWithOrders` adalah model data yang menggabungkan hasil dari tabel `users` dan `orders`.

---

## 🏗️ Relasi Antar Tabel

Room mendukung dua jenis relasi utama:

- **One-to-Many**: Satu entitas berhubungan dengan banyak entitas lainnya.
- **Many-to-Many**: Banyak entitas saling berhubungan satu sama lain.

### 1. **One-to-Many Relation**

Misalkan kita memiliki dua tabel: `User` dan `Order`. Setiap pengguna bisa memiliki banyak pesanan (orders).

#### a. **Entity User**

```java
@Entity(tableName = "users")
public class User {

    @PrimaryKey(autoGenerate = true)
    public int userId;

    public String name;
}
```

#### b. **Entity Order**

```java
@Entity(tableName = "orders", foreignKeys = @ForeignKey(entity = User.class, parentColumns = "userId", childColumns = "userId"))
public class Order {

    @PrimaryKey(autoGenerate = true)
    public int orderId;

    public int userId;
    public String orderDetails;
}
```

#### c. **Mengambil Data Relasi One-to-Many**

```java
public class UserWithOrders {

    @Embedded
    public User user;

    @Relation(
        parentColumn = "userId",
        entityColumn = "userId"
    )
    public List<Order> orders;
}
```

Dengan relasi ini, kita dapat mengambil data pengguna beserta daftar pesanan yang terkait dengan pengguna tersebut.

---

### 2. **Many-to-Many Relation**

Untuk relasi many-to-many, kita memerlukan tabel penghubung yang menyimpan relasi antara dua tabel.

#### a. **Entity Product**

```java
@Entity(tableName = "products")
public class Product {

    @PrimaryKey(autoGenerate = true)
    public int productId;

    public String productName;
}
```

#### b. **Entity User**

```java
@Entity(tableName = "users")
public class User {

    @PrimaryKey(autoGenerate = true)
    public int userId;

    public String name;
}
```

#### c. **Tabel Penghubung (Junction Table)**

```java
@Entity(primaryKeys = {"userId", "productId"})
public class UserProductCrossRef {

    public int userId;
    public int productId;
}
```

#### d. **Mengambil Data Relasi Many-to-Many**

```java
public class UserWithProducts {

    @Embedded
    public User user;

    @Relation(
        parentColumn = "userId",
        entityColumn = "productId",
        associateBy = @Junction(UserProductCrossRef.class)
    )
    public List<Product> products;
}
```

Dengan relasi ini, kita bisa mendapatkan data pengguna beserta produk-produk yang terkait dengannya.

---

## ⚡ Query Asinkron dengan Room

Penggunaan Room secara langsung di thread utama bisa menyebabkan aplikasi terasa lambat atau bahkan macet. Untuk itu, penting untuk menggunakan query secara asinkron menggunakan `LiveData` atau `RxJava`.

### 1. **Menggunakan LiveData untuk Asynchronous Query**

```java
@Dao
public interface UserDao {

    @Query("SELECT * FROM users")
    LiveData<List<User>> getAllUsers();
}
```

`LiveData` akan mengamati perubahan data dan mengupdate UI secara otomatis ketika data berubah.

### 2. **Menggunakan Kotlin Coroutines untuk Asynchronous Query**

```java
@Dao
public interface UserDao {

    @Query("SELECT * FROM users")
    suspend fun getAllUsers(): List<User>;
}
```

Dengan menggunakan `suspend` function, kita dapat menjalankan query Room secara asinkron di dalam coroutine, tanpa memblokir thread utama.

---

## 🔧 Tips dan Trik untuk Mengoptimalkan Query Room

- **Indeks di Kolom Pencarian**: Gunakan anotasi `@Index` di kolom yang sering dicari untuk meningkatkan kinerja query.
- **Gunakan `@Transaction` untuk Mengelola Transaksi**: `@Transaction` memastikan bahwa semua operasi dalam metode tersebut dieksekusi sebagai satu transaksi yang konsisten.
- **Gunakan `LiveData` dan `Flow` untuk Observasi**: Untuk aplikasi berbasis UI, gunakan `LiveData` atau `Flow` untuk mengamati perubahan data dengan cara reaktif.

---

## 🎯 Kesimpulan

Room memberikan kemudahan dalam mengelola dan melakukan query pada database SQLite di Android. Dengan memanfaatkan query lanjutan dan pengelolaan relasi antar tabel, kita dapat membuat aplikasi Android yang lebih efisien, terstruktur, dan mudah dikembangkan lebih lanjut.

> **"Database bukanlah hal yang menakutkan, Room hadir untuk mempermudahmu!"** 🗃️