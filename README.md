# Big Data Hadoop - Single Node Cluster with Docker

Proyek ini membuat sebuah *single-node Hadoop cluster* menggunakan Docker dengan mode pseudo-distributed. Dapat dilakukan percobaan atau pembelajaran big data lokal di Windows.

## Prasyarat

Sebelum memulai, pastikan Anda telah menginstal dan menyiapkan hal-hal berikut:

1. **Install Docker Desktop**  
   Unduh dan instal dari [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)

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
   atau alternatif lain gunakan terminal di windows
   ```bash
   cd C:\
   ```

## Langkah Instalasi

Setelah prasyarat selesai, ikuti langkah-langkah berikut:

5. **Clone Repo**
   ```bash
   git clone https://github.com/sains-data/bigdata-hadoop.git
   ```

6. **Buka folder di VS Code**  
   Buka folder `bigdata-hadoop` di VS Code, lalu ubah semua baris dengan format `CRLF` ke `LF`.  
   - Di VS Code: Klik `CRLF` di kanan bawah, lalu pilih `LF`.

7. **Arahkan Terminal ke Folder Repo**
   ```bash
   cd /mnt/c/bigdata-hadoop
   ```
   atau pada terminal windows
   ```bash
   cd C:\bigdata-hadoop
    ```
8. **Salin file `hadoop-3.4.1.tar.gz` ke folder ini**  
   File ini *tidak* diunduh otomatis oleh Dockerfile.  
   - Unduh dari: [https://downloads.apache.org/hadoop/common/hadoop-3.4.1/hadoop-3.4.1.tar.gz](https://downloads.apache.org/hadoop/common/hadoop-3.4.1/hadoop-3.4.1.tar.gz)  
   - Pindahkan ke folder `bigdata-hadoop`

   > 💡 **Catatan:** Jika ingin Docker otomatis mengunduh file, bisa tambahkan perintah `curl` ke dalam `Dockerfile` seperti:
   ```Dockerfile
   RUN curl -O https://downloads.apache.org/hadoop/common/hadoop-3.4.1/hadoop-3.4.1.tar.gz
   ```

9. **Bangun Docker Image**
   ```bash
   bash build.sh
   ```

10. **Jalankan Container**
   ```bash
   bash start.sh
   ```

11. **Cek Apakah Container Jalan**
   ```bash
   docker ps -a
   ```

12. **Login ke Container**
   ```bash
   bash login.sh
   ```

13. **Cek Aktivitas Hadoop**
   ```bash
   jps
   ```

14. **Cek Web UI**
   - Hadoop Namenode: [http://localhost:9870](http://localhost:9870)
   - Hadoop Resource Manager: [http://localhost:8088](http://localhost:8088)

15. **Keluar dari Container**
   ```bash
   exit
   ```

16. **Hentikan Container**
   ```bash
   bash stop.sh
   ```

## Kontak

Untuk pertanyaan atau kontribusi, silakan buka *Issue* di repo ini atau hubungi Asisten Praktikum Analisis Big Data
