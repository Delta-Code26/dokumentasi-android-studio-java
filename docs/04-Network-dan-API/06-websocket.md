# 🌐 Implementasi WebSocket di Android

WebSocket adalah protokol komunikasi yang menyediakan saluran komunikasi full-duplex (dua arah) melalui koneksi TCP. Ini sangat cocok untuk aplikasi yang memerlukan komunikasi secara real-time, seperti aplikasi chat, game online, atau aplikasi monitoring data secara langsung. Di Android, kita bisa menggunakan WebSocket untuk berkomunikasi dengan server secara efisien.

---

## 🔑 Apa itu WebSocket?

WebSocket adalah protokol komunikasi yang bekerja melalui saluran TCP yang terjaga untuk komunikasi dua arah antara klien dan server. Keunggulannya dibandingkan HTTP adalah WebSocket memungkinkan data dikirimkan dalam waktu nyata tanpa perlu membuka koneksi baru setiap kali data dikirim.

WebSocket sangat ideal untuk aplikasi yang membutuhkan komunikasi secara terus-menerus atau secara real-time, seperti aplikasi chatting atau aplikasi dengan data yang terus diperbarui.

---

## 🛠️ Persiapan Backend untuk WebSocket

Sebelum kamu bisa menggunakan WebSocket di Android, pastikan server backend kamu sudah mendukung WebSocket. Biasanya, server WebSocket menggunakan pustaka atau framework khusus, seperti **Spring WebSocket** (untuk Java) atau **Socket.IO** (untuk Node.js).

Backend akan menginisialisasi WebSocket server yang dapat menerima koneksi dari klien (Android) dan mengirimkan data secara real-time.

---

## 📲 Implementasi WebSocket di Android Studio

Untuk menggunakan WebSocket di Android, kita bisa memanfaatkan pustaka pihak ketiga seperti **okhttp-websocket** atau **Java-WebSocket**. Di sini kita akan menggunakan **okhttp-websocket** karena integrasinya yang mudah dengan Retrofit dan OkHttp, yang sudah banyak digunakan dalam aplikasi Android.

### 1. **Menambahkan Dependensi di `build.gradle`**

Untuk memulai, kamu perlu menambahkan dependensi **okhttp-websocket** di file `build.gradle` (Module: app) proyek Android kamu.

```gradle
dependencies {
    implementation 'com.squareup.okhttp3:okhttp:4.9.3'
    implementation 'com.squareup.okhttp3:okhttp-urlconnection:4.9.3'
}
```

Setelah menambahkan dependensi ini, klik **Sync Now** di Android Studio.

---

### 2. **Membuat Koneksi WebSocket**

Sekarang kita akan mengimplementasikan WebSocket di Android untuk berkomunikasi dengan server. Pertama-tama, kita perlu membuat instance **OkHttpClient** dan **WebSocketListener**.

#### a. **Membuat Kelas WebSocketListener**

`WebSocketListener` akan menangani berbagai event yang terjadi selama koneksi WebSocket, seperti saat menerima pesan atau saat koneksi terputus.

```java
import okhttp3.*;

public class WebSocketClient extends WebSocketListener {

    private static final String TAG = "WebSocketClient";
    private WebSocket webSocket;

    // URL WebSocket server
    private static final String SERVER_URL = "ws://example.com/socket";

    private OkHttpClient client;

    public WebSocketClient() {
        client = new OkHttpClient();
    }

    // Membuka koneksi WebSocket
    public void start() {
        Request request = new Request.Builder().url(SERVER_URL).build();
        webSocket = client.newWebSocket(request, this);
    }

    // Mengirim pesan ke server WebSocket
    public void sendMessage(String message) {
        if (webSocket != null) {
            webSocket.send(message);
        }
    }

    // Menangani pesan yang diterima
    @Override
    public void onMessage(WebSocket webSocket, String text) {
        super.onMessage(webSocket, text);
        // Proses pesan yang diterima dari server
        Log.d(TAG, "Message received: " + text);
    }

    // Menangani saat koneksi terhubung
    @Override
    public void onOpen(WebSocket webSocket, Response response) {
        super.onOpen(webSocket, response);
        Log.d(TAG, "WebSocket connected.");
    }

    // Menangani saat terjadi kesalahan
    @Override
    public void onFailure(WebSocket webSocket, Throwable t, Response response) {
        super.onFailure(webSocket, t, response);
        Log.e(TAG, "WebSocket error: " + t.getMessage());
    }

    // Menangani saat koneksi WebSocket tertutup
    @Override
    public void onClosing(WebSocket webSocket, int code, String reason) {
        super.onClosing(webSocket, code, reason);
        Log.d(TAG, "WebSocket closing: " + reason);
    }

    @Override
    public void onClosed(WebSocket webSocket, int code, String reason) {
        super.onClosed(webSocket, code, reason);
        Log.d(TAG, "WebSocket closed.");
    }
}
```

#### b. **Menggunakan WebSocketClient di `Activity`**

Di `Activity`, kamu dapat membuat instance `WebSocketClient` dan menghubungkannya ke server. Kamu juga bisa mengirim pesan ke server WebSocket.

```java
public class MainActivity extends AppCompatActivity {

    private WebSocketClient webSocketClient;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        webSocketClient = new WebSocketClient();
        webSocketClient.start();

        // Mengirim pesan ke server setelah WebSocket terhubung
        Button sendButton = findViewById(R.id.sendButton);
        sendButton.setOnClickListener(view -> {
            webSocketClient.sendMessage("Hello, server!");
        });
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
        // Pastikan WebSocket ditutup saat Activity dihancurkan
        webSocketClient.sendMessage("disconnect");
    }
}
```

#### c. **Menangani Event WebSocket**

Di `WebSocketListener`, kamu bisa menangani berbagai event, seperti pesan yang diterima, kesalahan, dan penutupan koneksi. Ini memungkinkan kamu untuk berinteraksi dengan aplikasi secara real-time.

---

### 3. **Menutup Koneksi WebSocket**

Saat aplikasi dihancurkan, pastikan koneksi WebSocket ditutup dengan benar untuk mencegah kebocoran sumber daya.

```java
@Override
protected void onDestroy() {
    super.onDestroy();
    if (webSocketClient != null) {
        webSocketClient.sendMessage("disconnect");
        // Menutup WebSocket
        webSocketClient.close();
    }
}
```

---

## 🔒 Keamanan WebSocket

Untuk memastikan koneksi WebSocket aman, gunakan URL yang dimulai dengan `wss://` (WebSocket Secure) daripada `ws://`, yang mirip dengan `https` pada protokol HTTP. Pastikan server WebSocket kamu mendukung `wss` agar data yang dikirimkan melalui WebSocket tetap terenkripsi.

```java
private static final String SERVER_URL = "wss://example.com/socket";
```

---

## 🔑 Kesimpulan

WebSocket adalah solusi ideal untuk komunikasi real-time dalam aplikasi Android. Dengan menggunakan pustaka seperti **okhttp-websocket**, kamu dapat dengan mudah mengimplementasikan koneksi WebSocket untuk aplikasi chat, game online, atau aplikasi yang membutuhkan pembaruan data secara real-time.

Dengan memahami cara membuat koneksi, mengirim dan menerima pesan, serta menangani event WebSocket di Android, kamu dapat menciptakan pengalaman pengguna yang lebih interaktif dan responsif.