# 📡 Broadcast Receiver di Android

> Broadcast Receiver memungkinkan aplikasi Android untuk mendengarkan dan merespons berbagai jenis event atau perubahan sistem, seperti perubahan status jaringan atau penerimaan pesan.

---

## 📚 Apa Itu Broadcast Receiver?

`BroadcastReceiver` adalah komponen aplikasi Android yang memungkinkan aplikasi menerima **broadcast** (pemberitahuan) dari sistem atau aplikasi lain. Broadcast ini bisa berupa event yang terjadi di sistem atau aplikasi, seperti perubahan status jaringan, baterai rendah, atau bahkan pesan dari aplikasi lain.

---

## 🚀 Jenis-Jenis Broadcast

1. **Normal Broadcast**  
   - Dikirim secara asynchronous dan tidak teratur. Broadcast ini tidak mengganggu eksekusi aplikasi lainnya dan dapat diterima oleh semua aplikasi yang mendengarkan.
   - Cocok untuk event yang tidak memerlukan respons cepat.

2. **Ordered Broadcast**  
   - Dikirimkan secara berurutan. Aplikasi yang menerima broadcast dapat memilih untuk menangguhkan atau menghentikan broadcast ke aplikasi lainnya.
   - Cocok untuk mengontrol aliran data atau ketika urutan penting.

3. **Sticky Broadcast**  
   - Broadcast yang tidak segera hilang setelah diproses. Broadcast ini tetap ada di memori dan bisa diterima oleh aplikasi yang memintanya di kemudian waktu.
   - Cocok untuk pengiriman data yang masih relevan meskipun broadcast sudah selesai.

---

## 🔧 Cara Menggunakan Broadcast Receiver

### 1. **Membuat BroadcastReceiver**

Untuk membuat `BroadcastReceiver`, kamu perlu membuat kelas yang meng-extend `BroadcastReceiver` dan mengoverride metode `onReceive()`.

#### Contoh Implementasi:

```java
public class MyBroadcastReceiver extends BroadcastReceiver {

    @Override
    public void onReceive(Context context, Intent intent) {
        // Tugas yang dilakukan saat menerima broadcast
        Log.d("MyBroadcastReceiver", "Broadcast diterima!");
    }
}
```

### 2. **Mendaftarkan BroadcastReceiver**

Ada dua cara untuk mendaftarkan `BroadcastReceiver`:

- **Melalui Manifest** (Untuk Broadcast System)
  
  Jika kamu ingin aplikasi mendengarkan broadcast yang dikirim oleh sistem atau aplikasi lain secara otomatis, kamu bisa mendaftarkan receiver di file `AndroidManifest.xml`.

  Contoh pendaftaran di manifest untuk menerima perubahan status jaringan:

  ```xml
  <receiver android:name=".MyBroadcastReceiver">
      <intent-filter>
          <action android:name="android.net.conn.CONNECTIVITY_CHANGE"/>
      </intent-filter>
  </receiver>
  ```

- **Melalui Kode (Runtime)** (Untuk Broadcast Dinamis)
  
  Kamu juga bisa mendaftarkan `BroadcastReceiver` secara dinamis menggunakan kode Java dengan `registerReceiver()`.

  Contoh implementasi:

  ```java
  IntentFilter filter = new IntentFilter(Intent.ACTION_BATTERY_LOW);
  MyBroadcastReceiver receiver = new MyBroadcastReceiver();
  registerReceiver(receiver, filter);
  ```

### 3. **Menerima Broadcast**

Setelah mendaftarkan receiver, aplikasi akan mendengarkan event yang dikirim. Misalnya, kita ingin mendengarkan perubahan status baterai:

```java
public class MyBatteryReceiver extends BroadcastReceiver {

    @Override
    public void onReceive(Context context, Intent intent) {
        if (Intent.ACTION_BATTERY_LOW.equals(intent.getAction())) {
            Log.d("MyBatteryReceiver", "Baterai rendah!");
        }
    }
}
```

### 4. **Unregister Receiver**

Jangan lupa untuk melepas pendaftaran receiver saat aplikasi tidak lagi membutuhkannya atau pada saat aplikasi dihentikan, untuk menghindari memory leaks.

```java
unregisterReceiver(myReceiver);
```

---

## 🎯 Contoh Kasus Penggunaan

### 1. **Mendengarkan Perubahan Koneksi Jaringan**

Kamu bisa menggunakan `BroadcastReceiver` untuk memonitor status koneksi jaringan, sehingga aplikasi bisa merespons jika koneksi internet terputus atau terhubung kembali.

```java
public class ConnectivityReceiver extends BroadcastReceiver {

    @Override
    public void onReceive(Context context, Intent intent) {
        ConnectivityManager cm = (ConnectivityManager) context.getSystemService(Context.CONNECTIVITY_SERVICE);
        NetworkInfo activeNetwork = cm.getActiveNetworkInfo();
        
        if (activeNetwork != null && activeNetwork.isConnected()) {
            Log.d("ConnectivityReceiver", "Koneksi internet tersedia");
        } else {
            Log.d("ConnectivityReceiver", "Koneksi internet terputus");
        }
    }
}
```

### 2. **Menerima Pesan dari Aplikasi Lain**

Jika aplikasi lain mengirimkan pesan atau event tertentu, kamu bisa membuat aplikasi Android untuk merespons event tersebut menggunakan `BroadcastReceiver`.

---

## ⚡ Tips & Best Practices

- **Gunakan Filter yang Tepat:** Gunakan `IntentFilter` untuk hanya mendengarkan jenis broadcast yang relevan agar aplikasi kamu tidak menerima broadcast yang tidak perlu.
- **Hindari Broadcast yang Berlebihan:** Menggunakan `BroadcastReceiver` secara terus-menerus, terutama untuk broadcast yang tidak dibutuhkan, bisa menguras daya baterai. Batasi penggunaan receiver untuk kebutuhan yang memang penting.
- **Keamanan:** Periksa siapa yang mengirim broadcast dan pastikan receiver kamu hanya menerima broadcast dari sumber yang terpercaya.

---

## 💬 Kesimpulan

- `BroadcastReceiver` memungkinkan aplikasi untuk mendengarkan dan merespons perubahan atau event di sistem atau aplikasi lain.
- Gunakan receiver dengan bijak, baik melalui manifest atau runtime, dan selalu ingat untuk mendaftarkan dan meng-unregister receiver sesuai kebutuhan.
- Receiver sangat berguna dalam aplikasi yang perlu merespons event seperti perubahan status jaringan atau penerimaan pesan.

> "Dengan `BroadcastReceiver`, aplikasi kamu bisa bereaksi terhadap event yang terjadi di sistem dan memberikan respons yang tepat, kapan saja!" 📡