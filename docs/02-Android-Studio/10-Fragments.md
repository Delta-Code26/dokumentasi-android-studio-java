# 🧩 Fragments di Android

**Fragment** adalah bagian dari antarmuka pengguna atau perilaku aplikasi yang bisa digunakan ulang di dalam beberapa activity. Bisa dibilang Fragment adalah **“mini Activity”** yang hidup di dalam Activity.

Bayangin Fragment kayak puzzle: kecil, modular, bisa dicopot-pasang sesuka hati! 🧩📱

---

## 🎯 Kapan Menggunakan Fragment?

- Ketika kamu ingin membagi tampilan menjadi bagian-bagian modular.
- Untuk navigasi antar tab (ViewPager, BottomNav).
- Untuk menyesuaikan UI di layar besar (tablet) dan kecil (ponsel).

---

## 🏗️ Struktur Fragment

### 1. Buat Kelas Fragment
```java
public class MyFragment extends Fragment {
    @Nullable
    @Override
    public View onCreateView(LayoutInflater inflater,
                             ViewGroup container,
                             Bundle savedInstanceState) {
        return inflater.inflate(R.layout.fragment_my, container, false);
    }
}
```

### 2. Tambahkan Fragment ke Activity
```java
FragmentManager fragmentManager = getSupportFragmentManager();
FragmentTransaction transaction = fragmentManager.beginTransaction();

MyFragment fragment = new MyFragment();
transaction.replace(R.id.fragment_container, fragment);
transaction.commit();
```

> Pastikan `fragment_container` adalah ID dari `FrameLayout` di XML Activity kamu.

---

## ⚙️ Fragment Lifecycle

Sama kayak Activity, tapi dengan alur sendiri:

```
onAttach() → onCreate() → onCreateView() → onViewCreated()
→ onStart() → onResume()
← onPause() ← onStop() ← onDestroyView() ← onDestroy() ← onDetach()
```

> Penting banget paham lifecycle biar nggak terjadi memory leak atau error pas rotasi layar.

---

## 🧪 Komunikasi antara Fragment dan Activity

### Dari Fragment ke Activity
```java
((MainActivity)getActivity()).doSomething();
```

### Dari Activity ke Fragment
```java
MyFragment fragment = new MyFragment();
Bundle bundle = new Bundle();
bundle.putString("data", "Halo Fragment!");
fragment.setArguments(bundle);
```

Lalu ambil datanya di dalam fragment:
```java
String data = getArguments().getString("data");
```

---

## 🧭 Fragment vs Activity

| Activity | Fragment |
|---------|----------|
| Mandiri | Butuh Activity |
| Lebih berat | Lebih ringan |
| Navigasi penuh | Navigasi dalam UI |
| Cocok untuk layar penuh | Modular, fleksibel |

---

## 🧠 Tips Profesional

- Gunakan `FragmentManager` dengan hati-hati, terutama saat menumpuk Fragment.
- Jangan lupa panggil `commit()` di akhir transaksi Fragment!
- Pakai `ViewBinding` biar ngoding jadi lebih aman dan ringkas.

---

## 🚀 Latihan

1. Buat Fragment `ProfileFragment` dan `SettingsFragment`.
2. Tambahkan dua tombol di `MainActivity` untuk menampilkan Fragment tersebut saat ditekan.

---

## 📌 Kesimpulan

Fragment = Solusi modular untuk membangun UI dinamis di Android.  
Dengan fragment, kamu bisa bikin UI yang fleksibel, ringan, dan bisa di-reuse.  
Biar aplikasimu nggak cuma jalan, tapi *ngelaju!*

---

Next: Yuk belajar **Navigation Component** biar pindah antar Fragment makin mudah tanpa ribet manual!

