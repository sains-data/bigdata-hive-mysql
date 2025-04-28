# Latihan: Memahami Hive Services

## Tujuan
Memahami berbagai layanan (**services**) yang disediakan oleh **Hive** dan bagaimana menggunakannya.

## Petunjuk
Jawablah pertanyaan-pertanyaan berikut dengan mengacu pada materi tentang Hive Services.  
Beberapa soal juga meminta kamu untuk **praktik langsung** menjalankan perintah.

### 1. Menampilkan Daftar Service Hive
**Praktik:**  
Gunakan perintah Hive untuk melihat daftar semua services yang tersedia.

```bash
hive --service
```

**Tugas:**  
- Tuliskan minimal 5 nama layanan yang kamu temukan.



### 2. Hive Command-Line Interface (CLI)
**Pertanyaan:**
- Apa fungsi utama **Hive CLI**?
- Berikan contoh satu perintah dasar yang bisa kamu jalankan di dalam CLI.



### 3. HiveServer2
**Pertanyaan:**
- Apa kelebihan **HiveServer2** dibandingkan HiveServer versi lama?
- Untuk koneksi JDBC atau ODBC ke Hive, service mana yang harus aktif?
- Di port berapa HiveServer2 berjalan secara default?



### 4. Beeline
**Pertanyaan:**
- Jelaskan perbedaan antara **Beeline** dan **Hive CLI**.
- Bagaimana cara Beeline menghubungkan diri ke HiveServer2?



### 5. Hive Web Interface (HWI) dan Hue
**Pertanyaan:**
- Apa keuntungan menggunakan **Hive Web Interface (HWI)**?
- Apa nama platform web lain selain HWI yang mendukung menjalankan query Hive?



### 6. Jar Service
**Pertanyaan:**
- Apa fungsi **jar service** di Hive?
- Mengapa jar service lebih mudah digunakan dibandingkan menjalankan aplikasi Java manual?



### 7. Metastore Service
**Praktik:**  
Gunakan opsi `-p` atau environment variable `METASTORE_PORT` untuk mengatur port baru untuk metastore.

**Pertanyaan:**
- Default port untuk metastore service adalah berapa?
- Apa keuntungan menjalankan **metastore** sebagai **proses terpisah** dari Hive utama?



# Bonus Challenge 🌟
- Coba jalankan HiveServer2 di background.
- Coba konek ke HiveServer2 menggunakan Beeline.
- Coba setting Hive metastore agar jalan di port berbeda dari 9083.



# Catatan
Materi tentang Hive Services ini penting karena:
- Membantu kamu **mengakses Hive** dari berbagai cara (CLI, Web, JDBC).
- Membantu **mengatur koneksi multi-user**.
- Membuka peluang **menghubungkan Hive dengan aplikasi eksternal**.