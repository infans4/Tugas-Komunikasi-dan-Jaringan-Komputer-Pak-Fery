# **Penjelasan Lengkap Cara Kerja SMTP (Simple Mail Transfer Protocol)**  

SMTP adalah protokol standar yang digunakan untuk mengirim email melalui internet. Protokol ini bertanggung jawab atas pengiriman pesan dari klien pengirim ke server email penerima dan antar server email. SMTP bekerja pada **port 25**, **port 465** (untuk SSL), dan **port 587** (untuk TLS).

![Cara Kerja](https://github.com/infans4/Tugas-Komunikasi-dan-Jaringan-Komputer-Pak-Fery/blob/main/Tugas-5_SMTP/assets/Cara-Kerja-SMTP.jpg)

###### Src: https://blogs.powercode.id/mengenal-apa-itu-smtp-dan-cara-kerjanya/

---

## **1. Arsitektur dan Komponen SMTP**  

SMTP bekerja dalam model **klien-server**, dengan beberapa komponen utama:

### a. **Mail User Agent (MUA)**  
- Ini adalah klien email yang digunakan oleh pengguna untuk menulis dan mengirim email (contoh: Outlook, Thunderbird, Gmail).

### b. **Mail Transfer Agent (MTA)**  
- Server yang menerima pesan dari MUA dan meneruskannya ke MTA lain atau MDA. Ini adalah perantara dalam proses pengiriman email.

### c. **Mail Delivery Agent (MDA)**  
- Komponen yang menerima email dari MTA dan menyimpannya di kotak surat penerima.

---

## **2. Alur Kerja SMTP (Tahapan Pengiriman Email)**  

### **Tahap 1: Penulisan dan Pengiriman Email**  
- Pengguna menulis email menggunakan klien email (MUA) dan menekan tombol "Kirim".
- MUA menghubungi server SMTP untuk mengirimkan email.

### **Tahap 2: Koneksi ke Server SMTP**  
- MUA membangun koneksi dengan server SMTP menggunakan protokol TCP/IP pada port yang sesuai (25, 465, atau 587).
- Server SMTP menerima permintaan koneksi dan memulai sesi SMTP.

### **Tahap 3: Proses Pengiriman Email**  
Proses komunikasi antara klien dan server SMTP terjadi melalui perintah dan respon:

1. **HELO/EHLO:**  
   Klien memperkenalkan dirinya ke server.  
   Contoh:  
   ```bash
   HELO example.com
   ```

2. **MAIL FROM:**  
   Klien menginformasikan alamat pengirim.  
   Contoh:  
   ```bash
   MAIL FROM:<pengirim@example.com>
   ```

3. **RCPT TO:**  
   Klien menginformasikan alamat penerima.  
   Contoh:  
   ```bash
   RCPT TO:<penerima@example.com>
   ```

4. **DATA:**  
   Klien mengirimkan isi email, termasuk header (subject, tanggal, dll.) dan body email. Setelah selesai, diakhiri dengan tanda titik (`.`) pada baris kosong.  
   Contoh:  
   ```bash
   DATA  
   Subject: Tes Email  
   Ini adalah email uji coba.  
   .
   ```

5. **QUIT:**  
   Mengakhiri koneksi dengan server.

### **Tahap 4: Transfer Antar Server SMTP**  
- Jika penerima menggunakan domain yang berbeda, server SMTP mengirimkan email ke MTA lain hingga mencapai server penerima.

### **Tahap 5: Penyimpanan dan Pengambilan Email**  
- Setelah mencapai server penerima, email disimpan oleh MDA.  
- Penerima mengambil email melalui protokol POP3 atau IMAP.

---

## **3. Protokol yang Berhubungan dengan SMTP**  

- **POP3 (Post Office Protocol v3):**  
  Mengambil email dari server dan mengunduhnya ke klien email.

- **IMAP (Internet Message Access Protocol):**  
  Mengakses email di server tanpa mengunduhnya ke klien email.

---

## **4. Format Email dalam SMTP**

- **Header:** Berisi informasi seperti pengirim, penerima, subjek, dan metadata lainnya.
- **Body:** Isi pesan utama yang dikirim.

Contoh format header email:  
```text
From: pengirim@example.com  
To: penerima@example.com  
Subject: Contoh Email  
Date: Wed, 28 Nov 2024 10:00:00 +0000  
```

---

## **5. Mode Autentikasi dan Keamanan SMTP**  

- **Autentikasi SMTP:**  
  Pengguna harus memberikan kredensial (username dan password) agar dapat mengirim email.

- **Enkripsi:**  
  - **STARTTLS:** Mengubah koneksi dari tidak terenkripsi menjadi terenkripsi.
  - **SSL/TLS:** Koneksi langsung yang dienkripsi sejak awal.

---

## **6. Masalah Umum SMTP dan Penyelesaiannya**  

- **Relay Denied:** Server SMTP menolak untuk meneruskan email karena konfigurasi relay tidak diizinkan.
- **Authentication Failed:** Kredensial login salah atau tidak sesuai.
- **Spam Filtering:** Email ditandai sebagai spam oleh server penerima.

---

## **7. Tools untuk Menguji SMTP**  

- **Telnet:**  
  Menguji koneksi ke server SMTP.  
  Contoh:  
  ```bash
  telnet smtp.example.com 25
  ```

- **OpenSSL:**  
  Menguji koneksi SSL/TLS ke server SMTP.  
  Contoh:  
  ```bash
  openssl s_client -connect smtp.example.com:465
  ```

- **`swaks`:** Tool khusus untuk menguji email.  
  Contoh:  
  ```bash
  swaks --to penerima@example.com --from pengirim@example.com --server smtp.example.com
  ```

---

Apakah Anda membutuhkan penjelasan tambahan tentang pengaturan server SMTP atau cara mengkonfigurasi klien email tertentu?
