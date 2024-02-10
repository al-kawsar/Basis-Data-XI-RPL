# Install XAMPP

# Database

## Membuat Database

## Menampilkan Database

## Menghapus Database

## Menggunakan Database

# Tipe Data

## ANGKA

- ==INT:== Untuk menyimpan nilai bilangan bulat (integer). Misalnya, INT dapat digunakan untuk menyimpan angka seperti 1, 100, -10, dan sebagainya.

- ==DECIMAL: ==Digunakan untuk menyimpan nilai desimal presisi tinggi, cocok untuk perhitungan finansial atau keuangan.
-
- ==FLOAT dan DOUBLE: ==Digunakan untuk menyimpan nilai desimal dengan presisi floating-point. DOUBLE memiliki presisi lebih tinggi dibandingkan FLOAT.

- ==TINYINT, SMALLINT,== ==MEDIUMINT==, dan ==BIGINT: ==Tipe data ini menyimpan bilangan bulat dengan ukuran yang berbeda-beda.
  Contoh :

```sql
CREATE TABLE contoh_tabel (
    id INT,
    harga DECIMAL(10, 2),
    jumlah_barang TINYINT
);
```

Dalam contoh tersebut, id menggunakan tipe data INT, harga menggunakan tipe data `DECIMAL `dengan presisi 10 digit dan 2 angka di belakang koma, dan jumlah_barang menggunakan tipe data `TINYINT`.

## TEKS

- ==CHAR(N) ==Menyimpan string karakter tetap dengan panjang N. Contoh: ==CHAR(10) ==akan menyimpan string dengan panjang tepat 10 karakter.

- ==VARCHAR(N):== Menyimpan string karakter dengan panjang variabel maksimal N. Misalnya, ==VARCHAR(255) ==dapat menyimpan string hingga 255 karakter, tetapi sebenarnya hanya menyimpan panjang yang diperlukan plus beberapa overhead.

- ==TEXT: ==Digunakan untuk menyimpan teks dengan panjang variabel, tanpa batasan panjang tertentu. Cocok untuk data teks yang panjangnya tidak terduga.

- ==ENUM: ==Memungkinkan Anda mendefinisikan set nilai yang mungkin dan membatasi kolom hanya dapat mengambil salah satu dari nilai tersebut.

- ==SET: ==Mirip dengan ENUM, namun dapat menyimpan satu atau lebih nilai dari himpunan yang telah ditentukan.

Contoh :

```sql
CREATE TABLE contoh_tabel (
    nama CHAR(50),
    alamat VARCHAR(100),
    catatan TEXT,
    status ENUM('Aktif', 'Non-Aktif')
);
```

## TANGGAL

- ==DATE== : Menyimpan nilai tanggal dengan format YYYY-MM-DD.
- ==TIME==: Menyimpan nilai waktu dengan format HH:MM:SS.

- ==DATETIME: ==Menggabungkan nilai tanggal dan waktu dengan format YYYY-MM-DD HH:MM:SS.

- ==TIMESTAMP: ==Sama seperti DATETIME, tetapi dengan kelebihan diatur secara otomatis saat data dimasukkan atau diubah.

```sql
CREATE TABLE ContohTabel (
    tanggal DATE,
    waktu TIME,
    datetimekolom DATETIME,
    timestampkolom TIMESTAMP
);
```

Dalam contoh ini, kolom _==tanggal==_ akan menyimpan nilai tanggal, _==waktu==_ menyimpan nilai waktu, ==_datetimekolom== menyimpan kombinasi tanggal dan waktu, dan \*\*==timestampkolom==_ akan secara otomatis diatur saat data dimasukkan atau diubah.

## Boolean

- ==BOOL / BOOLEAN / TINYINT(1):== Digunakan untuk menyimpan nilai boolean, yang dapat mewakili kebenaran atau kesalahan. Representasi nilai benar adalah 1, sedangkan nilai salah direpresentasikan sebagai 0. Meskipun nilai selain 0 dianggap benar, secara umum, ketiganya seringkali digunakan secara bergantian. Seringkali, ketika Anda mendeklarasikan kolom sebagai BOOL atau BOOLEAN, MySQL mengonversinya secara otomatis menjadi TINYINT(1), yang juga dapat digunakan untuk menyimpan nilai boolean dengan 0 untuk false dan 1 untuk true.

1. Menggunakan `BOOLEAN`

````sql
CREATE TABLE contohTabel (
    title VARCHAR(255),
    completed BOOLEAN
);```
Dalam contoh diatas, kita mendefinisikan kolom `completed` sebagai tipe data `BOOLEAN`. Ini merupakan cara yang sah dan umum digunakan di MySQL. Nilai yang dapat disimpan dalam kolom ini adalah `TRUE` atau `FALSE`, atau dalam representasi angka, 1 atau 0.

2. Menggunakan `BOOL`
```sql
CREATE TABLE contohTabel (
    title VARCHAR(255),
    completed BOOL
);
````

Dalam contoh ini, kita menggunakan `BOOL` sebagai tipe data untuk kolom `completed`. Perlu dicatat bahwa MySQL secara otomatis mengonversi `BOOL` menjadi `TINYINT(1)`. Oleh karena itu, pada dasarnya, ini setara dengan contoh pertama. Namun, beberapa pengembang lebih suka menggunakan `BOOLEAN` untuk kejelasan.

3. Menggunakan `TINYINT(1)`

```sql
CREATE TABLE contohTabel (
    title VARCHAR(255),
    completed TINYINT(1)
);
```

Dalam contoh ini, kita menggunakan `TINYINT(1)` sebagai tipe data untuk kolom `completed`. Ini adalah pendekatan yang valid karena MySQL mengonversi `BOOL` menjadi `TINYINT(1)` secara otomatis. Dalam hal ini, nilai yang dapat disimpan adalah 1 untuk `TRUE` dan 0 untuk `FALSE`.

# Tabel

Tabel adalah struktur data terorganisir secara tabular yang terdiri dari baris dan kolom, di mana setiap baris menyimpan satu set data lengkap yang terkait dengan entitas tertentu, dan setiap kolom mewakili atribut atau field dari data tersebut. Setiap sel dalam tabel berisi nilai spesifik untuk kombinasi baris dan kolom, dan tabel biasanya memiliki kunci utama yang unik untuk mengidentifikasi setiap catatan. Dengan menggunakan SQL, kita dapat membuat dan mengelola tabel dengan menentukan tipe data untuk setiap kolom, serta menentukan kunci utama dan indeks untuk meningkatkan kinerja pencarian data. Tabel memainkan peran kunci dalam manajemen basis data relasional, memungkinkan penyimpanan data yang terstruktur dan efisien.

## Membuat Tabel

Struktur Query :

```mysql
CREATE TABLE [nama_table] (
nama_kolom1 tipe_data(ukuran) cons,
nama_kolom2 tipe_data(ukuran) cons
)
```

Contoh Query :

```mysql
CREATE TABLE pelanggan (
id_pelanggan INT(4) PRIMARY KEY NOT NULL,
nama_depan VARCHAR(25) NOT NULL,
nama_belakang VARCHAR(25) NOT NULL,
no_telp CHAR(12) UNIQUE
);
```

Hasil :
![](../../assets/desc%20tabel.png)
Analisis :

1. **CREATE TABLE pelanggan:** Ini adalah perintah utama yang digunakan untuk membuat tabel baru dengan nama "pelanggan".
2. **id_pelanggan INT(4) PRIMARY KEY NOT NULL:**
   - ==id_pelanggan== : Nama kolom pertama dalam tabel yang merupakan identifikasi unik untuk setiap pelanggan.
   - ==INT(4)==: Tipe data kolom adalah bilangan bulat (integer) dengan panjang 4 digit.
   - ==PRIMARY KEY==: Menandakan bahwa kolom ini adalah kunci utama (primary key) untuk tabel. Artinya, setiap nilai di kolom ini harus unik dan tidak boleh NULL.
   - ==NOT NULL==: Menandakan bahwa kolom ini tidak dapat memiliki nilai NULL, sehingga setiap entri harus memiliki nilai untuk kolom ini.
3. **nama_depan VARCHAR(25) NOT NULL:**
   - ==nama_depan==: Nama kolom kedua yang menyimpan bagian depan dari nama pelanggan.
   - ==VARCHAR(25)==: Tipe data kolom adalah karakter variable dengan panjang maksimal 25 karakter.
   - ==NOT NULL==: Seperti pada kolom pertama, menunjukkan bahwa kolom ini tidak dapat memiliki nilai NULL.
4. **nama_belakang VARCHAR(25) NOT NULL:**
   - ==nama_belakang==: Nama kolom ketiga yang menyimpan bagian belakang dari nama pelanggan.
   - ==VARCHAR(25)==: Tipe data kolom adalah karakter variable dengan panjang maksimal 25 karakter.
   - ==NOT NULL==: Menandakan bahwa kolom ini tidak dapat memiliki nilai NULL.
5. **no_telp CHAR(12) UNIQUE:** - ==no_telp==: Nama kolom keempat yang menyimpan nomor telepon pelanggan. - ==CHAR(12)==: Tipe data kolom adalah karakter dengan panjang tetap 12 karakter. - ==UNIQUE==: Menandakan bahwa setiap nilai di kolom ini harus unik dalam tabel. Dengan kata lain, tidak ada dua pelanggan yang dapat memiliki nomor telepon yang sama.
   Kesimpulan :
   Query tersebut membuat sebuah tabel bernama "pelanggan" dengan empat kolom. Kolom pertama, "id_pelanggan", adalah kunci utama (primary key) yang berisi bilangan bulat dengan panjang 4 digit dan tidak boleh bernilai NULL. Kolom kedua, "nama_depan", dan kolom ketiga, "nama_belakang", masing-masing berupa karakter variable dengan panjang maksimal 25 karakter dan keduanya tidak boleh bernilai NULL. Kolom terakhir, "no_telp", berisi karakter tetap dengan panjang 12 karakter dan memiliki constraint UNIQUE, sehingga setiap nomor telepon yang dimasukkan harus unik dalam tabel. Dengan demikian, struktur tabel ini dirancang untuk menyimpan informasi tentang pelanggan dengan kunci unik, serta menghindari duplikasi nomor telepon.

## Tampilkan Struktur Tabel

Struktur Query :

```mysql
DESC [nama_tabel];
atau
DESCRIBE [nama_tabel];
```

Contoh Query :

```mysql
DESC pelanggan
```

Hasil :
![](../../assets/desc%20tabel.png)
Analisis :

1. ==DESC pelanggan==: Query ini digunakan untuk mendeskripsikan (describe) struktur tabel yang disebut **"pelanggan"**. Query ini memberikan informasi rinci tentang kolom-kolom yang ada dalam tabel tersebut.

Kesimpulan :
Perintah "DESC pelanggan" memberikan deskripsi lengkap tentang struktur tabel "pelanggan". Tabel ini terdiri dari empat kolom, yaitu `id_pelanggan`, `nama_depan`, `nama_belakang`, dan `no_telp`. Kolom `id_pelanggan` diidentifikasi sebagai kunci utama (PRIMARY KEY) dengan tipe data integer, sementara `nama_depan` dan `nama_belakang` menggunakan tipe data karakter variable dengan panjang maksimal 25 karakter dan tidak boleh bernilai NULL. Kolom `no_telp` menggunakan tipe data karakter tetap dengan panjang 12 karakter dan diberi constraint UNIQUE, yang mengindikasikan bahwa setiap nomor telepon harus unik dalam tabel. Tidak ada nilai default yang ditetapkan, dan deskripsi ini memberikan pandangan komprehensif tentang struktur dan aturan yang diterapkan pada setiap kolom dalam tabel "pelanggan".

## Menampilkan Daftar Tabel

Struktur Query :

```mysql
SHOW TABLES;
```

Contoh Query :

```mysql
SHOW TABLES;
```

Hasil :
![](../../assets/daftar%20tabel.png)
Analisis :

Kesimpulan :

## Q & A

> [! FAQ] Soal 1
> Apa Perbedaan PK Dan Unique ?
>
> **PRIMARY KEY (PK):** Kolom yang dinyatakan sebagai PRIMARY KEY tidak dapat memiliki nilai NULL dan harus berisi nilai yang unik untuk setiap baris dalam tabel. Primary Key digunakan untuk mengidentifikasi secara unik setiap baris dalam tabel.
>
> **UNIQUE:** Kolom yang dinyatakan sebagai UNIQUE juga harus memiliki nilai yang unik untuk setiap baris, tetapi mereka diizinkan memiliki nilai NULL (kecuali jika Anda menetapkan NOT NULL secara eksplisit). Unique digunakan untuk memastikan bahwa setiap nilai dalam kolom tersebut adalah unik.

> [! FAQ] Soal 2
> Mengapa hanya kolom id_pelanggan yang menggunakan constraint PRIMARY KEY?
>
> Kolom `id_pelanggan` menggunakan PRIMARY KEY karena itu adalah kolom yang diidentifikasi sebagai kunci utama atau kunci utama tabel. Ini memberikan cara unik untuk mengidentifikasi setiap baris pelanggan dalam tabel.

> [! FAQ] Soal 3
> Mengapa pada kolom no_telp yang menggunakan tipe data char bukan varchar?
>
> Pemilihan antara CHAR dan VARCHAR tergantung pada karakteristik data yang akan disimpan. CHAR menyimpan string dengan panjang tetap, sementara VARCHAR menyimpan string dengan panjang variabel. Dalam kasus nomor telepon, panjangnya tetap (12 karakter), jadi CHAR digunakan untuk mengoptimalkan penyimpanan.

> [! FAQ] Soal 4
> Mengapa hanya kolom no_telp yang menggunakan contraint UNIQUE?
>
> nomor telepon dianggap sebagai informasi yang harus unik untuk setiap pelanggan. Dengan menetapkan UNIQUE pada kolom `no_telp`, database memastikan bahwa tidak ada nomor telepon yang sama yang dapat dihubungkan dengan lebih dari satu pelanggan.

> [! FAQ] Soal 5
> Mengapa kolom no_telp tidak memakai constraint NOT NULL, sementara kolom lainnya menggunakan constraint tersebut?
>
> Keputusan untuk menggunakan atau tidak menggunakan constraint NOT NULL pada kolom `no_telp` mungkin tergantung pada persyaratan aplikasi. Jika nomor telepon tidak wajib diisi pada saat pendaftaran pelanggan, constraint NOT NULL tidak digunakan pada kolom tersebut. Constraints NOT NULL biasanya digunakan pada kolom yang harus memiliki nilai (tidak boleh NULL) agar data dapat dianggap lengkap dan dapat diandalkan.

# Insert

## Insert 1 data

### Struktur

```mysql
INSERT INTO [nama_tabel]
VALUES (nilai1, nilai2, nilai2, ...);
```

### Contoh

```mysql
INSERT INTO pelanggan
VALUES (1, "Raihan", "Alkawsar", '085xxxxxxxxx');
```

## Insert > 1 data

### Contoh

```mysql
INSERT INTO pelanggan
VALUES
(2, "Nafan", "nabil", '081xxxxxxxxx'),
(3, "", "nabil", '082xxxxxxxxx'),
(4, "Fadhil", "A", '083xxxxxxxxx');
```

## Menyebut Kolom

### Struktur

```mysql
INSERT INTO [nama_tabel]
(kolom1, kolom2, kolom3, ...)
VALUES
(nilai1, nilai2, nilai3, ...);
```

### Contoh

```mysql
INSERT INTO pelanggan
(nama_depan, id_pelanggan)
VALUES
("Hansar", 5);
```

# SELECT

## Seluruh data

### Struktur

```mysql
SELECT * FROM [nama_tabel];
```

### Contoh

```mysql
SELECT * FROM pelanggan;
```

## Data Kolom Tertentu

### Struktur

```mysql
SELECT [nama_kolom1], [nama_kolom2], ..., [nama_kolom_n]
FROM [nama_tabel];
```

### Contoh

```mysql
SELECT nama_depan FROM pelanggan;
```

## Klausa WHERE

### Struktur

```mysql
SELECT [nama_kolom / *] FROM [nama_tabel]
WHERE [kondisi];
```

### Contoh

```mysql
SELECT nama_depan FROM pelanggan
WHERE id_pelanggan = 2;
```

==Format Kondisi== : `[nama_kolom]` `[operator]` `[nilai]`

Operator = `=, >, >=, <, <=, !=,  <>, dst`

==Contoh Kondisi== : id_pelanggan > 1
