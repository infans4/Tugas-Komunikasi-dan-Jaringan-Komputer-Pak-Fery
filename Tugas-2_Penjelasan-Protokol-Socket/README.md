
# Tugas 2 Protocol Socket

Pada tugas ini menjelaskan terkait dari cara kerja protokol socket

Pada tugas ini mereferensi pada pemrograman socket simpel menggunakan terminal yang ada pada link dibawah ini:
https://github.com/kusdavletov/socket-programming-simple-server-and-client/blob/master/README.md. Adapun pembahasan yang dibahas adalah:


## Aspek Teknis

- Cara Kerja Protokol Socket
- Jumlah Paket dalam Capture
- Flow Graph


## 1. Cara Kerja Protokol Socket

- Socket: Klien membuka soket TCP ke alamat IP server pada port yang ditentukan, lalu mengirimkan permintaan koneksi. Koneksi TCP ini menggunakan mekanisme three-way handshake, yaitu SYN, SYN-ACK, dan ACK untuk memulai komunikasi.

### Hasil tangkapan layar
![3WayHandShake](https://github.com/infans4/Tugas-2_Penjelasan-Protokol-Socket/blob/main/assets/3HandShake.png)

## 2. Jumlah Paket dalam Capture

Jumlah paket yang dikirimkan dalam komunikasi bergantung pada jenis dan ukuran permintaan serta respons. Berikut ini adalah beberapa jenis paket yang dapat ditemukan dalam tangkapan:

**Permintaan Klien ke Server**:
- Satu paket untuk membuka koneksi TCP (three-way handshake).
**Respons Server ke Klien**:
- Paket data yang berisi konten atau file yang diminta.
**Penutupan Koneksi**:
- Koneksi ditutup setelah respons selesai.
Total jumlah paket dapat bervariasi, namun untuk satu permintaan dasar (misalnya, sebuah permintaan `GET` sederhana yang menerima respons kecil), biasanya diperlukan sekitar 4-6 paket, tergantung pada ukuran konten.
### Hasil tangkapan layar
![3WayHandShake](https://github.com/infans4/Tugas-2_Penjelasan-Protokol-Socket/blob/main/assets/3HandShake.png)
![SendClient](https://github.com/infans4/Tugas-2_Penjelasan-Protokol-Socket/blob/main/assets/SendClientnServer.png))
![ClientOut](https://github.com/infans4/Tugas-2_Penjelasan-Protokol-Socket/blob/main/assets/ClientOut.png)
## 3. Flow Graph di Wireshark

Untuk melihat grafik alur, dapat menggunakan fitur Flow Graph di Wireshark yang menampilkan aliran komunikasi antara klien dan server, termasuk handshakes dan paket yang dikirim. Flow Graph menunjukkan langkah-langkah komunikasi berikut:

1. **YN, SYN-ACK, ACK**: Koneksi TCP diinisiasi oleh klien.
2. **Pengiriman Data**: Pengiriman data konten dari server ke klien.
3. **Penutupan Koneksi**: Jika tidak ada permintaan lebih lanjut, koneksi TCP akan ditutup.

### Hasil tangkapan layar
![FlowGraph](https://github.com/infans4/Tugas-2_Penjelasan-Protokol-Socket/blob/main/assets/FlowGraph.png)
