Jawaban no 1
<?php
$servername = "localhost";
$database = "niagahos_namadatabase";
$username = "niagahos_user";
$password = "passworddatabase";

// untuk tulisan bercetak tebal silakan sesuaikan dengan detail database Anda
// membuat koneksi
$conn = mysqli_connect($servername, $username, $password, $database);
// mengecek koneksi
if (!$conn) {
    die("Koneksi gagal: " . mysqli_connect_error());
}
echo "Koneksi berhasil";
mysqli_close($conn);
?>

Jawaban no 2
1. Untuk membuat database melalui phpmyadmin, pastikan sudah terlebih dahulu menginstall XAMPP
2. Jika sudah terinstall pastikan APACHE dan MYSQL sudah anda jalankan
3. Sekarang buka browser anda lalu ketikkan http://localhost/phpmyadmin 
4. Pada menu Database, masukkan nama database yang diinginkan, kemudian klik Create
5. Setelah di create sekarang buat table pada database tersebut. masukkan nama table yang anda inginkan, lalu masukkan jumlah kolom yang ingin dibuat. Lalu klik GO
6. Pada langkah ini kita akan memasukkan nama kolom yang ingin kita masukkan
7. Jika sudah terisi field-field yang di perlukan, sekarang klik SAVE pada pojok kanan bawah
8. Kalau sudah, sekarang kita berhasil membuat database

Jawaban no 3
mysql> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mahasiswa          |
| mysql              |
| performance_schema |
| test               |
+--------------------+
5 rows in set (0.13 sec)
 
mysql> USE mahasiswa;
Database changed
 
mysql> CREATE TABLE daftar_dosen (NIP CHAR(10) PRIMARY KEY,
nama_dosen VARCHAR(50) NOT NULL, no_hp CHAR(13),
alamat VARCHAR(100));
Query OK, 0 rows affected (0.10 sec)
 
mysql> DESC daftar_dosen;
+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| NIP        | char(10)     | NO   | PRI | NULL    |       |
| nama_dosen | varchar(50)  | NO   |     | NULL    |       |
| no_hp      | char(13)     | YES  |     | NULL    |       |
| alamat     | varchar(100) | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
4 rows in set (0.08 sec)
 
mysql> CREATE TABLE mata_kuliah (kode_matkul CHAR(6) PRIMARY KEY,
nama_matkul VARCHAR(50) NOT NULL,
jumlah_SKS TINYINT UNSIGNED DEFAULT '2',
semester TINYINT,NIP_dosen CHAR(10));
Query OK, 0 rows affected (0.04 sec)
 
mysql> DESC mata_kuliah;
+-------------+---------------------+------+-----+---------+-------+
| Field       | Type                | Null | Key | Default | Extra |
+-------------+---------------------+------+-----+---------+-------+
| kode_matkul | char(6)             | NO   | PRI | NULL    |       |
| nama_matkul | varchar(50)         | NO   |     | NULL    |       |
| jumlah_SKS  | tinyint(3) unsigned | YES  |     | 2       |       |
| semester    | tinyint(4)          | YES  |     | NULL    |       |
| NIP_dosen   | char(10)            | YES  |     | NULL    |       |
+-------------+---------------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

Jawaban no 4 
mysql> SELECT * FROM daftar_dosen WHERE nama_dosen='Sabrina Sari';
+------------+--------------+------------+-----------+
| NIP_dosen  | nama_dosen   | no_hp      | alamat    |
+------------+--------------+------------+-----------+
| 0160436012 | Sabrina Sari | 0812349900 | Pekanbaru |
+------------+--------------+------------+-----------+
1 row in set (0.08 sec)
 
mysql> UPDATE daftar_dosen SET no_hp ='085298710065'
WHERE nama_dosen='Sabrina Sari';
Query OK, 1 row affected (0.07 sec)
Rows matched: 1  Changed: 1  Warnings: 0
 
mysql> SELECT * FROM daftar_dosen WHERE nama_dosen='Sabrina Sari';
+------------+--------------+--------------+-----------+
| NIP_dosen  | nama_dosen   | no_hp        | alamat    |
+------------+--------------+--------------+-----------+
| 0160436012 | Sabrina Sari | 085298710065 | Pekanbaru |
+------------+--------------+--------------+-----------+
1 row in set (0.00 sec)

Jawaban no 5
mysql> DELETE from daftar_dosen WHERE nama_dosen = 'Maya Ari Putri'
OR nama_dosen='Tia Santrini';
Query OK, 2 rows affected (0.15 sec)
 
mysql> SELECT * FROM daftar_dosen;
+------------+---------------+------------+---------+
| NIP_dosen  | nama_dosen    | no_hp      | alamat  |
+------------+---------------+------------+---------+
| 0275430005 | Susi Indriani | 0812656532 | Bogor   |
| 0576431001 | M. Siddiq     | 0812979005 | Jakarta |
| 0770435006 | Rubin Hadi    | 0812567678 | Papua   |
| 0869437003 | Mustalifah    | 0812338877 | Aceh    |
| 1080432007 | Arif Budiman  | 0812456345 | Makasar |
+------------+---------------+------------+---------+
5 rows in set (0.06 sec)
