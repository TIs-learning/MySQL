# Hari 2: BUAT Pernyataan dan Pernyataan Dasar SELECT 🎉

Hari ini, kita akan membahas pernyataan dasar SQL `CREATE` yang digunakan untuk mendefinisikan dan membuat tabel, dan pernyataan `SELECT` untuk mengambil data dari database.🚀

### Apa yang dimaksud dengan Pernyataan CREATE?🏗

Pernyataan `CREATE` digunakan untuk mendefinisikan objek database baru seperti tabel, tampilan, indeks, atau database.Untuk hari ini, kami akan fokus pada pembuatan tabel.

### Sintaks Dasar CREATE TABLE 🛠️

```sql
CREATE TABLE table_name (
    column1 datatype constraints,
    column2 datatype constraints,
    ...
);
```

- **`column1, column2`**: Nama kolom.
- **`datatype`**: Tipe data untuk setiap kolom (misalnya, `INT`, `VARCHAR`, `DATE`).
- **`constraints`**: Aturan opsional seperti `PRIMARY KEY` atau `NOT NULL`.

### Membuat Tabel Pertama Anda 🎓

Mari buat tabel bernama `students`:

```sql
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    age INT,
    enrollment_date DATE
);
```

- **`student_id`**: Bilangan bulat yang mengidentifikasi setiap siswa secara unik.
- **`name`**: String hingga 100 karakter.
- **`age`**: Bilangan bulat yang mewakili usia siswa.
- **`enrollment_date`**: Tanggal yang menunjukkan kapan siswa mendaftar.

### Apa yang dimaksud dengan Pernyataan SELECT?🧐

Pernyataan `SELECT` adalah tulang punggung query SQL.Ini memungkinkan Anda mengambil data dari satu atau lebih tabel dalam database.Dengan menentukan kolom atau menggunakan simbol khusus seperti `*`, Anda dapat menentukan dengan tepat data apa yang ingin Anda ambil.

### Sintaks Dasar SELECT 🛠

```sql
SELECT column1, column2, ...
FROM table_name;
```

- **`column1, column2, ...`**: Kolom yang ingin Anda ambil.
- **`table_name`**: Tabel tempat Anda ingin mengambil datanya.

Untuk mengambil semua kolom, gunakan `*`:

```sql
SELECT *
FROM table_name;
```

### Menggunakan SELECT dengan Kueri Sederhana 🤓

Bayangkan sebuah tabel bernama `employees`:

|identitas |nama |usia |departemen |
|-- |---------- |--- |---------- |
|1 |John Doe |30 |SDM |
|2 |Jane Smith |25 |itu |
|3 |Sam Coklat |35 |Pemasaran |

1. Ambil semua kolom:

```sql
SELECT *
FROM employees;
```

2. Ambil kolom tertentu:

```sql
SELECT name, age
FROM employees;
```

### Latihan Latihan 📝

1. Tulis pernyataan `CREATE TABLE` untuk membuat tabel baru bernama `products` dengan struktur berikut:
- `product_id` (integer, kunci utama)
- `product_name` (string, maksimal 50 karakter, tidak boleh null)
- `price` (desimal dengan 2 tempat desimal)
- `stock_quantity` (bilangan bulat)
2. Masukkan beberapa contoh data ke dalam tabel `students` yang Anda buat.
3. Tulis kueri `SELECT` untuk mengambil kolom `name` dan `department` saja dari tabel `employees`.
4. Gunakan `SELECT` untuk mengambil semua baris dari tabel `students` Anda.

## Ringkasan 🏁

Hari ini, Anda belajar tentang:

- Pernyataan `CREATE` untuk mendefinisikan dan membuat tabel.
- Menulis pertanyaan dasar `CREATE TABLE`.
- Pernyataan `SELECT` dan sintaksnya untuk mengambil data.
- Menggunakan `SELECT` dengan kolom tertentu dan `*`.

Besok, kita akan mendalami **memfilter data dengan klausa WHERE**.🌟
