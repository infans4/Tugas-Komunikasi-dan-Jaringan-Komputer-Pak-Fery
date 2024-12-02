# **Penjelasan Lengkap Tentang Cara Kerja DNS (Domain Name System)**

DNS adalah sistem terdistribusi yang memungkinkan perangkat di jaringan seperti internet untuk mengonversi nama domain menjadi alamat IP. Komputer tidak memahami nama domain seperti `www.google.com`; mereka bekerja dengan alamat IP untuk menemukan server yang tepat.

![Cara Kerja](https://github.com/infans4/Tugas-Komunikasi-dan-Jaringan-Komputer-Pak-Fery/blob/main/Tugas-4_DNS/assets/DNS-Query.jpeg)

###### Src: https://cloudraya.com/blog/apa-itu-dns/
---

## **1. Struktur dan Komponen DNS**

DNS dirancang seperti pohon hierarki terbalik, dengan beberapa level yang memainkan peran berbeda:

### a. **Root DNS Server**  
- Root server adalah titik awal dalam proses pencarian DNS.
- Hanya ada 13 set **root server** yang diidentifikasi dengan label dari A hingga M, tetapi masing-masing memiliki banyak salinan di seluruh dunia untuk redundansi.

### b. **Top-Level Domain (TLD) Server**  
- Server yang bertanggung jawab atas domain tingkat atas seperti `.com`, `.org`, `.net`, atau domain kode negara seperti `.id` (Indonesia).

### c. **Authoritative Name Server**  
- Server yang menyimpan informasi DNS lengkap untuk domain tertentu. Misalnya, untuk `example.com`, authoritative server memiliki semua catatan DNS terkait.

### d. **Recursive Resolver (DNS Resolver)**  
- Klien (komputer atau router) yang memulai permintaan DNS akan meminta bantuan resolver untuk menemukan informasi DNS.

---

## **2. Langkah-langkah Resolusi DNS (Proses Penerjemahan Nama Domain)**

Ketika Anda mengetikkan nama domain seperti `www.example.com` di browser:

1. **Permintaan DNS Dikirim oleh Klien**  
   Komputer mengirimkan permintaan DNS ke resolver, yang biasanya dioperasikan oleh ISP atau penyedia layanan DNS seperti Google (8.8.8.8) atau Cloudflare (1.1.1.1).

2. **Pemeriksaan Cache Lokal**  
   Resolver akan memeriksa apakah hasil pencarian sudah ada di cache (lokal). Jika ada dan masih valid (dalam periode TTL), alamat IP segera dikembalikan.

3. **Menghubungi Root DNS Server**  
   Jika cache kosong, resolver menghubungi **Root DNS Server**. Root server tidak memberikan IP langsung tetapi mengarahkan resolver ke **TLD Server** yang relevan.

4. **Menghubungi TLD Server**  
   Resolver menghubungi TLD server yang sesuai dengan domain, misalnya `.com`. TLD server kemudian mengarahkan ke **Authoritative Name Server**.

5. **Menghubungi Authoritative Name Server**  
   Resolver meminta catatan DNS dari authoritative server. Server ini memberikan alamat IP sebenarnya untuk domain tersebut.

6. **Mengembalikan Alamat IP ke Klien**  
   Resolver mengembalikan alamat IP ke komputer klien, dan browser menggunakan alamat tersebut untuk menghubungi server tujuan.

7. **Koneksi ke Server Tujuan**  
   Browser membuat koneksi HTTP/HTTPS dengan server menggunakan alamat IP yang diperoleh.

---

## **3. Jenis-jenis Catatan DNS (DNS Records)**

DNS memiliki berbagai jenis catatan, masing-masing dengan fungsi tertentu:

- **A Record:** Menghubungkan nama domain dengan alamat IPv4.
- **AAAA Record:** Menghubungkan nama domain dengan alamat IPv6.
- **CNAME Record:** Alias atau nama lain untuk domain yang mengarah ke domain utama.
- **MX Record:** Menentukan server yang menangani email untuk domain tertentu.
- **TXT Record:** Menyimpan data teks yang sering digunakan untuk verifikasi kepemilikan domain atau pengaturan keamanan seperti SPF, DKIM.
- **NS Record:** Menentukan authoritative name server untuk domain.
- **PTR Record:** Menyediakan pencarian terbalik (reverse DNS lookup).

---

## **4. Konsep Cache dan TTL (Time To Live)**

- **Cache:** Resolver dan komputer menyimpan hasil pencarian DNS sementara untuk mempercepat pencarian di masa depan.
- **TTL:** Setiap catatan DNS memiliki waktu hidup tertentu yang disebut TTL. Setelah TTL berakhir, catatan harus diperbarui dari server DNS.

---

## **5. Mode Kerja DNS: Recursive vs Iterative Queries**

- **Recursive Query:** Resolver melakukan seluruh proses pencarian (dari root hingga authoritative server) dan mengembalikan hasil akhir ke klien.
- **Iterative Query:** Resolver memberikan hasil secara bertahap, meminta klien untuk melanjutkan pencarian ke server berikutnya.

---

## **6. Keamanan DNS dan Protokol Modern**

- **DNSSEC (DNS Security Extensions):**  
  Menyediakan validasi digital untuk memastikan catatan DNS tidak diubah oleh pihak ketiga selama pengiriman.

- **DNS over HTTPS (DoH):**  
  Mengamankan permintaan DNS dengan mengenkripsi lalu lintas melalui protokol HTTPS.

- **DNS over TLS (DoT):**  
  Menggunakan protokol TLS untuk mengenkripsi lalu lintas DNS, memberikan keamanan tambahan.

---

## **7. Contoh Praktis**

Misalnya, Anda ingin mengakses `www.example.com`:

1. **Langkah 1:**  
   Klien mengirimkan permintaan DNS ke resolver.

2. **Langkah 2:**  
   Resolver memeriksa cache lokal. Jika tidak ada, resolver menghubungi root server.

3. **Langkah 3:**  
   Root server mengarahkan resolver ke TLD server untuk `.com`.

4. **Langkah 4:**  
   TLD server mengarahkan resolver ke authoritative server untuk `example.com`.

5. **Langkah 5:**  
   Resolver menerima alamat IP dan mengembalikannya ke klien.

---

## **8. Tools untuk Menganalisis DNS:**

- **`nslookup` (Command Line):**  
  Untuk memeriksa informasi DNS.  
  Contoh:  
  ```bash
  nslookup www.google.com
  ```

- **`dig` (Command Line):**  
  Tool canggih untuk analisis DNS.  
  Contoh:  
  ```bash
  dig example.com +trace
  ```

---

Apakah Anda ingin penjelasan lebih lanjut tentang konfigurasi DNS server atau cara menggunakan tools tertentu untuk menganalisis DNS?
