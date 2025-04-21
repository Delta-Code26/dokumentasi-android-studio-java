# 🧩 Fragment & Navigation Component

> Fragment itu kayak "sub-Activity" yang fleksibel dan modular. Cocok buat bikin UI dinamis. Dan biar makin mantep, kita pakai **Navigation Component** buat navigasinya! 🧭

---

## 🧱 Apa Itu Fragment?

Fragment adalah bagian dari UI atau perilaku aplikasi yang dapat ditempatkan dalam Activity. Bisa dianggap sebagai **"mini activity"**.

### Kenapa Pakai Fragment?

- Mempermudah penggunaan UI di banyak ukuran layar
- Modular, jadi bisa reuse komponen
- Bisa dikelola lebih dinamis dibanding Activity

---

## 🛠 Struktur Dasar Fragment

### 1. Buat Kelas Fragment:

```java
public class HomeFragment extends Fragment {
    public HomeFragment() {
        // Required empty public constructor
    }

    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {
        return inflater.inflate(R.layout.fragment_home, container, false);
    }
}
```

### 2. XML Layout Fragment

```xml
<!-- res/layout/fragment_home.xml -->
<LinearLayout ... >
    <TextView android:text="Ini Fragment Home"/>
</LinearLayout>
```

### 3. Pasang Fragment di Activity

```xml
<fragment
    android:name="com.example.app.HomeFragment"
    android:id="@+id/homeFragment"
    android:layout_width="match_parent"
    android:layout_height="match_parent" />
```

Atau secara dinamis:

```java
FragmentManager fm = getSupportFragmentManager();
FragmentTransaction ft = fm.beginTransaction();
ft.replace(R.id.fragment_container, new HomeFragment());
ft.commit();
```

---

## 🧭 Navigation Component

Navigation Component mempermudah pengelolaan fragment & navigasi antar halaman, terutama dengan banyak fragment.

### Keunggulan:

- Navigasi lebih rapi & aman
- Ada visual editor di Android Studio
- Bisa handle argument antar fragment

---

## ⚙️ Langkah Setup Navigation Component

### 1. Tambahkan Dependency di `build.gradle`:

```gradle
implementation "androidx.navigation:navigation-fragment:2.7.0"
implementation "androidx.navigation:navigation-ui:2.7.0"
```

### 2. Buat `nav_graph.xml`

- Klik kanan → New → Navigation → Navigation Resource File
- Tambahkan semua fragment sebagai destination
- Atur hubungan antar fragment (arrow)

### 3. Tambahkan NavHostFragment ke `activity_main.xml`

```xml
<androidx.fragment.app.FragmentContainerView
    android:id="@+id/nav_host_fragment"
    android:name="androidx.navigation.fragment.NavHostFragment"
    app:navGraph="@navigation/nav_graph"
    app:defaultNavHost="true"
    android:layout_width="match_parent"
    android:layout_height="match_parent" />
```

---

## 🎯 Navigasi Antar Fragment

### Dari Java/Kotlin:

```java
NavController navController = Navigation.findNavController(view);
navController.navigate(R.id.action_homeFragment_to_detailFragment);
```

---

## 📤 Kirim Data Antar Fragment

### 1. Kirim dari Fragment A:

```java
Bundle bundle = new Bundle();
bundle.putString("nama", "Marno");
navController.navigate(R.id.action_A_to_B, bundle);
```

### 2. Ambil di Fragment B:

```java
String nama = getArguments().getString("nama");
```

---

## 🛑 Back Stack & Navigasi Mundur

Navigation Component secara default akan otomatis mengatur back stack. Tapi bisa dikustomisasi sesuai kebutuhan.

---

## 📚 Best Practice

- Gunakan `ViewModel` kalau data harus bertahan antar fragment
- Jangan over-fragment! Gunakan fragment hanya jika memang perlu
- Gunakan SafeArgs plugin untuk kirim data antar fragment lebih aman

---

## 🧠 Kesimpulan

- Fragment bantu modularisasi UI
- Navigation Component bikin navigasi fragment lebih clean & aman
- Cocok banget untuk aplikasi kompleks, multi-screen, tab, dll

> Fragment + Navigation itu kayak relationship sehat: jelas arahnya, tahu kemana harus pergi, dan bisa saling kirim pesan dengan aman 😆💌
