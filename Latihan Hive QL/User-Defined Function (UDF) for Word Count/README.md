# Latihan: Membuat Hive User-Defined Function (UDF)

## Tujuan
Memahami cara membuat dan menggunakan UDF di Hive untuk memproses data.

## Petunjuk
Jawablah pertanyaan-pertanyaan berikut, lalu praktikkan pembuatan UDF sederhana berdasarkan panduan.


### 1. Membuat Kode UDF
**Pertanyaan:**
- Apa package utama yang harus di-import saat membuat UDF di Hive?
- Jelaskan fungsi dari method `evaluate()` di dalam UDF!

**Praktik:**
- Buatlah sebuah Java class `WordCountUDF` yang menerima `Text` dan mengembalikan jumlah kata.


### 2. Kompilasi UDF
**Pertanyaan:**
- Mengapa kita perlu meng-compile Java code menjadi `.jar` sebelum digunakan di Hive?
- Sebutkan dua library penting yang perlu ada di classpath saat compile UDF Hive!

**Praktik:**
- Compile `WordCountUDF.java` menjadi file `WordCountUDF.jar`.


### 3. Registrasi UDF di Hive
**Praktik:**
- Jalankan perintah untuk menambahkan JAR ke Hive session:
  ```sql
  ADD JAR /path/to/WordCountUDF.jar;
  ```

**Pertanyaan:**
- Apa yang terjadi jika file JAR tidak ditemukan saat ADD JAR?


### 4. Menggunakan UDF dalam Query
**Praktik:**
- Jalankan query berikut (ubah sesuai nama tabelmu):
  ```sql
  SELECT text_column, WordCountUDF(text_column) AS word_count
  FROM your_table;
  ```

**Pertanyaan:**
- Jika input `text_column` berisi NULL, berapa nilai `word_count` yang dihasilkan oleh UDF ini?


### 5. Challenge Bonus 🌟
**Challenge:**
- Modifikasi UDF `WordCountUDF` agar **menghitung hanya kata-kata unik** dalam teks (bukan jumlah semua kata).


# Catatan
Dengan latihan ini kamu akan:
- Mampu membuat **UDF** sederhana di Hive.
- Memahami alur **compile - register - use** untuk Java UDFs.
- Siap membuat UDF lebih kompleks untuk kebutuhan analisis data di Hive.
