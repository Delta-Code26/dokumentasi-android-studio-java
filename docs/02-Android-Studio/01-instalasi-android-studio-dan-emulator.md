# 📥 Instalasi Android Studio dan Emulator

## Apa Itu Android Studio?

**Android Studio** adalah IDE (Integrated Development Environment) resmi dari Google untuk membangun aplikasi Android.  
Dengan Android Studio, kamu bisa:
- Menulis kode Java/Kotlin untuk Android
- Mendesain UI dengan XML
- Menjalankan emulator Android
- Melihat log dan debug aplikasi

Pokoknya, ini **senjatanya Android Developer** 🔥

---

## 🧰 Persiapan Sebelum Instalasi

Sebelum install Android Studio, pastikan:
- 💻 Laptop/PC kamu punya minimal:
  - RAM 8GB (4GB bisa, tapi bakal lemot)
  - Storage kosong minimal 10GB
  - OS: Windows 10/11, macOS, atau Linux
- ☕ Java Development Kit (JDK) sudah terinstall (biasanya Android Studio nyediain sendiri)

---

## 🔽 Langkah-Langkah Instalasi Android Studio

1. **Download Android Studio**  
   Kunjungi: [https://developer.android.com/studio](https://developer.android.com/studio)  
   Pilih versi terbaru dan sistem operasi kamu, lalu klik **Download**.

2. **Install Android Studio**  
   - Jalankan file installer
   - Klik Next terus sampai selesai
   - Pastikan centang **Android Virtual Device (AVD)** saat proses instalasi

3. **Buka Android Studio pertama kali**  
   - Pilih **Standard Setup**
   - Biarkan Android Studio download semua tools yang diperlukan (butuh internet!)

---

## 🤖 Membuat Emulator (Android Virtual Device)

Emulator = HP Android virtual di dalam laptop.

### Langkah Buat Emulator:
1. Buka Android Studio
2. Klik **"More Actions" → AVD Manager**
3. Klik **"Create Virtual Device"**
4. Pilih perangkat (misal: Pixel 4 atau Nexus 5X)
5. Pilih versi Android (disarankan: **API 30 atau lebih baru**)
6. Klik **Next → Finish**

💡 Emulator bisa dijalankan dari tombol ▶ di AVD Manager.

---

## 🧪 Jalankan Emulator Pertama Kali

1. Setelah emulator dibuat, klik tombol **Play (▶)** di AVD Manager
2. Emulator akan muncul seperti HP virtual
3. Waktunya mulai ngoding dan testing apps kamu!

---

## ❗ Troubleshooting Umum

- **Emulator lambat?**
  - Aktifkan **Intel HAXM** atau **Hyper-V** (Windows)
  - Kurangi resolusi/fitur emulator

- **Error SDK?**
  - Buka Android Studio → SDK Manager → Periksa apakah semua SDK dan Tools sudah diinstall

---

## ✅ Kesimpulan

Kalau kamu sampai di tahap ini, artinya kamu sudah siap tempur sebagai Android Developer! 🧑‍💻  
Next step: kita bakal bahas struktur proyek Android dan mulai bikin aplikasi pertamamu!
