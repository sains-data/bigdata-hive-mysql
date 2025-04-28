# Latihan Hive dengan MySQL di Hadoop

## Pendahuluan
Bagian ini membahas secara mendalam tentang penggunaan **SQL di Hive**, sebuah alat powerful untuk **data warehousing** dan **query** di atas **Hadoop**.  
Hive mendukung operasi **retrieval data**, **modifikasi data** (DML), serta **definisi struktur data** (DDL).  

Kamu akan belajar:
- Mengambil data dengan **SELECT**
- Memodifikasi data dengan **INSERT**, **UPDATE**, **DELETE**, **MERGE**
- Mengubah struktur tabel dengan **CREATE**, **ALTER**, **RENAME**, **DROP**, dan **TRUNCATE**
- Membuat **View** dan **Subquery**

Hive SQL mempermudah pengguna dalam mengelola big data menggunakan sintaks SQL yang sudah familiar.

## Operasi Dasar SQL di Hive

### 1. Membuat Tabel
```sql
CREATE TABLE employees (
  emp_id INT,
  emp_name STRING,
  emp_salary DOUBLE
);
```
**Penjelasan:**  
Membuat tabel baru `employees` dengan tiga kolom:  
- `emp_id` bertipe **integer**
- `emp_name` bertipe **string**
- `emp_salary` bertipe **double**  

Tabel ini akan menyimpan data karyawan.

### 2. Memasukkan Data
```sql
INSERT INTO TABLE employees VALUES 
(1, 'Alice', 65000.0), 
(2, 'Bob', 75000.0), 
(3, 'Charlie', 60000.0);
```
**Penjelasan:**  
Memasukkan tiga baris data ke dalam tabel `employees` dengan ID, nama, dan gaji masing-masing karyawan.



### 3. Mengambil Data
```sql
SELECT emp_name, emp_salary FROM employees;
```
**Penjelasan:**  
Mengambil kolom `emp_name` dan `emp_salary` dari tabel `employees` untuk melihat nama dan gaji karyawan.



### 4. Memperbarui Data
```sql
UPDATE employees 
SET emp_salary = 70000.0 
WHERE emp_id = 3;
```
**Penjelasan:**  
Memperbarui gaji karyawan dengan `emp_id = 3` menjadi 70.000.



### 5. Menghapus Data
```sql
DELETE FROM employees 
WHERE emp_id = 2;
```
**Penjelasan:**  
Menghapus data karyawan dengan `emp_id = 2`.



### 6. Mengurutkan Data
```sql
SELECT emp_name, emp_salary 
FROM employees 
ORDER BY emp_salary DESC;
```
**Penjelasan:**  
Mengambil nama dan gaji karyawan dan mengurutkannya berdasarkan gaji dari yang terbesar ke yang terkecil.



### 7. Mengagregasi Data
```sql
SELECT 
  AVG(emp_salary) AS avg_salary, 
  MAX(emp_salary) AS max_salary 
FROM employees;
```
**Penjelasan:**  
Menghitung rata-rata (`AVG`) dan gaji maksimum (`MAX`) dari seluruh karyawan.



### 8. Menggabungkan (Join) Tabel
```sql
CREATE TABLE departments (
  dept_id INT,
  dept_name STRING
);

INSERT INTO TABLE departments VALUES 
(1, 'HR'), 
(2, 'IT');

SELECT 
  e.emp_name, 
  d.dept_name 
FROM employees e
JOIN departments d 
ON e.emp_id = d.dept_id;
```
**Penjelasan:**  
- Membuat tabel `departments`
- Memasukkan data ke `departments`
- Melakukan **INNER JOIN** antara `employees` dan `departments` berdasarkan `emp_id = dept_id` untuk mengambil nama karyawan beserta departemennya.



### 9. Subquery
```sql
SELECT emp_name 
FROM employees 
WHERE emp_salary > (
  SELECT AVG(emp_salary) FROM employees
);
```
**Penjelasan:**  
Mengambil nama karyawan yang gajinya lebih besar dari rata-rata seluruh karyawan.



### 10. Membuat View
```sql
CREATE VIEW high_earners AS 
SELECT emp_name, emp_salary 
FROM employees 
WHERE emp_salary > 60000.0;
```
**Penjelasan:**  
Membuat **view** bernama `high_earners`, yang berisi karyawan dengan gaji lebih dari 60.000. View ini berfungsi seperti tabel virtual.



## Data Manipulation Language (DML) Lanjutan

### 11. Menyisipkan Data dengan SELECT
```sql
INSERT INTO TABLE employees 
SELECT 4, 'David', 72000.0;
```
**Penjelasan:**  
Menyisipkan data baru dengan mengambil nilai dari hasil seleksi lain (bisa berupa query lain atau tabel lain).



### 12. Menggabungkan dan Memperbarui Data (MERGE)
```sql
MERGE INTO employees AS target 
USING temp_employees AS source 
ON target.emp_id = source.emp_id 
WHEN MATCHED THEN 
  UPDATE SET target.emp_salary = source.emp_salary 
WHEN NOT MATCHED THEN 
  INSERT VALUES (source.emp_id, source.emp_name, source.emp_salary);
```
**Penjelasan:**  
- Jika `emp_id` ditemukan di kedua tabel, maka gaji akan diperbarui.
- Jika tidak ada, maka baris baru akan dimasukkan.



## Data Definition Language (DDL) Lanjutan

### 13. Mengganti Nama Tabel
```sql
ALTER TABLE employees 
RENAME TO staff;
```
**Penjelasan:**  
Mengubah nama tabel `employees` menjadi `staff`.



### 14. Menambahkan Kolom
```sql
ALTER TABLE employees 
ADD COLUMNS (emp_department STRING);
```
**Penjelasan:**  
Menambahkan kolom baru `emp_department` ke tabel `employees`.



### 15. Menghapus Tabel
```sql
DROP TABLE IF EXISTS employees;
```
**Penjelasan:**  
Menghapus tabel `employees` jika ada.  
Penggunaan `IF EXISTS` mencegah error jika tabel tidak ditemukan.



### 16. Mengosongkan Tabel (TRUNCATE)
```sql
TRUNCATE TABLE staff;
```
**Penjelasan:**  
Menghapus semua data di tabel `staff` tanpa menghapus struktur tabelnya.



# Penutup
DML dan DDL di Hive memberikan kekuatan besar untuk:
- Memanipulasi data (INSERT, UPDATE, DELETE, MERGE)
- Mengelola struktur tabel (CREATE, ALTER, RENAME, DROP, TRUNCATE)

Pemahaman operasi-operasi ini penting untuk bekerja secara efektif dengan big data di Hadoop menggunakan Hive.