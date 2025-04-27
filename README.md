# Big Data Hive - Single Node Cluster with Docker

Praktikum ini membuat sebuah *single-node Hive cluster* menggunakan Docker dengan integrasi MySQL untuk penyimpanan data Hive Metastore. Anda dapat melakukan percobaan atau pembelajaran Big Data lokal di Windows.

## Prasyarat

Sebelum memulai, pastikan Anda telah menginstal dan menyiapkan hal-hal berikut:

1. **Install Docker Desktop**  
   Unduh dan instal dari [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop).

2. **Login atau Daftar Akun Docker**  
   Buka Docker Desktop dan login menggunakan akun Docker Anda. Jika belum punya, silakan daftar terlebih dahulu.

3. **Install WSL dan Ubuntu 22.04 di Windows**  
   Buka PowerShell (Run as Administrator) dan jalankan:
   ```bash
   wsl --install -d Ubuntu-24.04
   ```

4. **Buka Terminal Ubuntu (WSL)**  
   Posisikan terminal di direktori `C:\`:
   ```bash
   cd /mnt/c
   ```

   Atau alternatif lain, gunakan terminal di Windows:
   ```bash
   cd C:\
   ```

## Langkah Instalasi

Setelah prasyarat selesai, ikuti langkah-langkah berikut:

5. **Clone Repo**
   ```bash
   git clone https://github.com/sains-data/bigdata-hive-mysql.git
   ```

6. **Buka folder di VS Code**  
   Buka folder `bigdata-hive-mysql` di VS Code, lalu ubah semua baris dengan format `CRLF` ke `LF`.  
   - Di VS Code: Klik `CRLF` di kanan bawah, lalu pilih `LF`.

7. **Arahkan Terminal ke Folder Repo**
   ```bash
   cd /mnt/c/bigdata-hive-mysql
   ```

   Atau pada terminal Windows:
   ```bash
   cd C:\bigdata-hive-mysql
   ```

8. **Salin file `hadoop-3.4.1.tar.gz` ke folder ini**  
   File ini *tidak* diunduh otomatis oleh Dockerfile.  
   - Unduh dari: [https://downloads.apache.org/hadoop/common/hadoop-3.4.1/hadoop-3.4.1.tar.gz](https://downloads.apache.org/hadoop/common/hadoop-3.4.1/hadoop-3.4.1.tar.gz)  
   - Pindahkan ke folder `bigdata-hadoop`

   > 💡 **Catatan:** Jika ingin Docker otomatis mengunduh file, bisa tambahkan perintah `curl` ke dalam `Dockerfile` seperti:
   ```Dockerfile
   RUN curl -O https://downloads.apache.org/hadoop/common/hadoop-3.4.1/hadoop-3.4.1.tar.gz
   ```

9. **Salin file `hive-4.0.1-bin.tar.gz` dan `tez-0.10.4-bin.tar.gz` ke folder ini**  
   File-file ini *tidak* diunduh otomatis oleh Dockerfile.  
   - Unduh dari:
     - [Apache Hive 4.0.1](https://downloads.apache.org/hive/hive-4.0.1/apache-hive-4.0.1-bin.tar.gz)  
     - [Apache Tez 0.10.4](https://downloads.apache.org/tez/tez-0.10.4/apache-tez-0.10.4-bin.tar.gz)

   - Pindahkan file-file tersebut ke folder `bigdata-hive-mysql`.

   > 💡 **Catatan:** Jika ingin Docker otomatis mengunduh file, bisa tambahkan perintah `wget` ke dalam `Dockerfile` seperti:
   ```Dockerfile
   RUN wget https://downloads.apache.org/hive/hive-4.0.1/apache-hive-4.0.1-bin.tar.gz
   RUN wget https://downloads.apache.org/tez/tez-0.10.4/apache-tez-0.10.4-bin.tar.gz
   ```

10. **Bangun Docker Image**
   ```bash
   bash build.sh
   ```

11. **Jalankan Container**
   ```bash
   bash start.sh
   ```

12. **Cek Apakah Container Jalan**
   ```bash
   docker ps -a
   ```

13. **Login ke Container**
   ```bash
   bash login.sh
   ```

14. **Cek Aktivitas Hive dan Port yang Tersedia**
   Cek port apakah sudah aktif untuk `hivemetastore` di port 10000 dan `hiveserver2` di port 10001 dengan perintah:
   ```bash
   netstat -nlpt
   ```

   Atau cek satu-satu dengan perintah:
   ```bash
   netstat -nlpt | grep 10000
   netstat -nlpt | grep 10001
   ```

   Jika belum muncul, tunggu beberapa menit dan cek kembali. Jika sudah muncul, lanjutkan ke langkah berikutnya.

15. **Koneksi ke Hive dengan Beeline**
   Setelah port 10001 aktif, lanjutkan dengan membuka koneksi Hive menggunakan Beeline:
   ```bash
   beeline -u jdbc:hive2://localhost:10001/ -n hive -p hive
   ```

   Di sini:
   - `-n` adalah username Hive (misalnya `hive`).
   - `-p` adalah password Hive (misalnya `hive`).

   Jika berhasil terkoneksi, Anda siap untuk menggunakan Hive.

16. **Akses GUI Hiveserver**
   Cek juga antarmuka web GUI Hiveserver di:  
   [http://localhost:10002](http://localhost:10002).

17. **Latihan Hive**
   Setelah terkoneksi dengan Beeline, lanjutkan latihan Hive di folder yang sudah disediakan di dalam container.

18. **Keluar dari Koneksi Hive**
   Setelah selesai, tekan `Ctrl + C` untuk keluar dari koneksi Beeline.

19. **Keluar dari Container**
   Setelah keluar dari Beeline, ketik:
   ```bash
   exit
   ```

20. **Hentikan Container**
   Hentikan container dengan menjalankan:
   ```bash
   bash stop.sh
   ```

   Tunggu hingga container benar-benar berhenti.

## Kontak

Untuk pertanyaan atau kontribusi, silakan buka *Issue* di repo ini atau hubungi Asisten Praktikum Analisis Big Data.