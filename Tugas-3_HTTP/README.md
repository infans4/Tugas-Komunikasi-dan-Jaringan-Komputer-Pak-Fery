
# Tugas 3 Protocol HTTP

Pada tugas ini menjelaskan terkait dari cara kerja protokol HTTP/1.1 2.0 dan 3.0

## Aspek Teknis

- Kelebihan Masing-Masing HTTP 
- Cara Kerja Masing-Masing Protokol HTTP
- Flow Graph Masing-Masing Protokol

## HTTP 1.1
## Kelebihan HTTP 1.1
1. **Persistent Connections (Keep-Alive)**: HTTP 1.1 memungkinkan koneksi tetap terbuka untuk beberapa request, mengurangi overhead waktu koneksi ulang dibanding HTTP 1.0.
2. **Chunked Transfer Encoding**: Server dapat mulai mengirim data sebelum seluruh respons selesai diproses, meningkatkan efisiensi untuk pengiriman data dinamis.
3. **Host Header**: HTTP 1.1 mendukung virtual hosting dengan header `Host`, memungkinkan beberapa domain berbagi satu alamat IP.
4. **Pipelining**: HTTP 1.1 mendukung pengiriman beberapa request tanpa harus menunggu respons sebelumnya selesai (walaupun jarang digunakan di dunia nyata karena keterbatasan implementasi di klien).
5. **Caching yang Lebih Baik**: HTTP 1.1 memperkenalkan header tambahan seperti `Cache-Control` dan `ETag`, yang meningkatkan kontrol caching.

## **Cara Kerja HTTP 1.1**
- **Proses Komunikasi**:
1. **Klien** (browser) membuka koneksi ke server menggunakan protokol TCP/IP.
2. Klien mengirimkan request HTTP, termasuk metode (GET, POST), URL, dan header.
3. **Server** memproses request dan mengirimkan respons HTTP yang mencakup header   (status, tipe konten, dsb.) dan body (konten seperti HTML atau JSON).
4. Jika `Keep-Alive` diaktifkan, koneksi tidak ditutup setelah respons, memungkinkan klien mengirim request berikutnya melalui koneksi yang sama.

- **Fitur-Fitur Utama**:
1. Header `Host` diperlukan untuk mendukung banyak domain di satu server.
2. Dukungan untuk koneksi persistent mengurangi waktu delay untuk request yang sering.
### Hasil tangkapan layar
![HTTP1.1](https://github.com/infans4/Tugas-3_HTTP-1.1/blob/main/assets/HTTP1.1.png)
## Flow Graph di Wireshark

Untuk melihat grafik alur, dapat menggunakan fitur Flow Graph di Wireshark yang menampilkan aliran komunikasi antara klien dan server, termasuk handshakes dan paket yang dikirim. Flow Graph menunjukkan langkah-langkah komunikasi berikut:

1. **YN, SYN-ACK, ACK**: Koneksi TCP diinisiasi oleh klien.
2. **Pengiriman Data**: Pengiriman data konten dari server ke klien.
3. **Penutupan Koneksi**: Jika tidak ada permintaan lebih lanjut, koneksi TCP akan ditutup.

### Hasil tangkapan layar
![FlowGraph]([https://github.com/infans4/Tugas-2_Penjelasan-Protokol-Socket/blob/main/assets/FlowGraph.png](https://github.com/infans4/Tugas-3_HTTP-1.1/blob/main/assets/HTTP1.1Flow.png))


## HTTP 2.0
## Kelebihan HTTP 2.0
1. **Multiplexing**:
   HTTP/2 memungkinkan pengiriman beberapa request dalam satu koneksi TCP tanpa blocking. Ini mengatasi kelemahan HTTP/1.1 yang harus menunggu antrian (head-of-line blocking).
2. **Header Compression**:
   HTTP/2 menggunakan kompresi header dengan algoritma HPACK, sehingga mengurangi ukuran data yang dikirim.
3. **Binary Protocol**:
   HTTP/2 menggunakan protokol biner (bukan teks), yang lebih cepat diproses oleh server dan klien.
4. **Prioritization**:
   HTTP/2 memungkinkan prioritas pada request tertentu, sehingga elemen penting (seperti CSS dan JavaScript) dapat dimuat lebih cepat.
5. **Server Push**:
   Server dapat mengirimkan data yang kemungkinan dibutuhkan klien sebelum diminta, mengurangi waktu round-trip.

## **Cara Kerja HTTP 2.0**
1. **Koneksi HTTPS**:
   HTTP/2 berjalan di atas TLS untuk keamanan, memastikan enkripsi dan integritas data.
2. **Penggunaan Stream**:
   - Setiap koneksi terdiri dari beberapa *stream* yang independen.
   - Data dikirim sebagai *frames* kecil, yang kemudian direkonstruksi di klien.
3. **Header Compression**:
   Header yang sering digunakan (seperti `User-Agent` atau `Host`) dikompresi untuk efisiensi.
4. **Server Push**:
   Server menganalisis permintaan klien dan mengirimkan data tambahan (seperti file CSS/JS) sebelum klien memintanya.
   
### Hasil tangkapan layar
![HTTP](https://github.com/infans4/Tugas-3_HTTP-1.1/blob/main/assets/HTTP2.0.png)
## Flow Graph di Wireshark

Untuk melihat grafik alur, dapat menggunakan fitur Flow Graph di Wireshark yang menampilkan aliran komunikasi antara klien dan server, termasuk handshakes dan paket yang dikirim. Flow Graph menunjukkan langkah-langkah komunikasi berikut:

1. **YN, SYN-ACK, ACK**: Koneksi TCP diinisiasi oleh klien.
2. **Pengiriman Data**: Pengiriman data konten dari server ke klien.
3. **Penutupan Koneksi**: Jika tidak ada permintaan lebih lanjut, koneksi TCP akan ditutup.

### Hasil tangkapan layar
![FlowGraph](https://github.com/infans4/Tugas-3_HTTP-1.1/blob/main/assets/HTTP2.0Flow.png)
