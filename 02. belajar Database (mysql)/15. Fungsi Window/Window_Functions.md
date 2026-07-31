📘 30 Hari SQL: Hari ke 16 - Fungsi Jendela di SQL

Hari ini, kita akan menjelajahi Fungsi Jendela, sebuah fitur canggih yang memungkinkan Anda melakukan analisis data tingkat lanjut di seluruh baris sambil mempertahankan perincian tingkat baris.Bersiaplah untuk membuka kemungkinan baru dalam SQL!

### 🔍 Ikhtisar
Fungsi Jendela adalah fungsi SQL yang beroperasi pada sekumpulan baris yang terkait dengan baris saat ini.Tidak seperti fungsi agregat, fungsi ini tidak menciutkan baris melainkan menambahkan nilai terhitung ke setiap baris.Fungsi Jendela sangat berguna untuk:

- Baris peringkat.
- Menghitung rata-rata bergerak.
- Mengambil nilai dari baris lain.
- Melakukan perhitungan kumulatif.

### 📘 Fungsi Jendela Utama
Berikut rincian Fungsi Jendela yang paling umum digunakan:

|Fungsi |Deskripsi |
|----------------------------------|------------------------------------------------------------------------------|
|ROW_NUMBER |Menetapkan bilangan bulat berurutan unik ke baris dalam partisi.|
|PERINGKAT |Menetapkan peringkat ke baris dalam partisi, dengan kesenjangan peringkat untuk ikatan.|
|DENSE_RANK |Mirip dengan RANK tetapi tanpa kesenjangan peringkat untuk ikatan.|
|NTILE |Membagi baris menjadi sejumlah grup tertentu dan menetapkan ID grup pada setiap baris.|
|LEAD dan LAG |Ambil nilai dari baris berikutnya atau sebelumnya dalam sebuah partisi.|
|FIRST_VALUE |Mengambil nilai pertama dalam sebuah partisi.|
|TERAKHIR_VALUE |Mengambil nilai terakhir dalam sebuah partisi.|

### Sintaks 🔧
Setiap Fungsi Jendela digunakan dengan klausa `OVER`:

```sql
SELECT column_name,
       window_function() OVER ([PARTITION BY column_name] [ORDER BY column_name]) AS alias_name
FROM table_name;
```

### 💡 Contoh Praktis

#### 1. ROW_NUMBER
Tetapkan nomor unik untuk setiap karyawan dalam departemen mereka:

```sql
SELECT employee_id, department_id, salary,
       ROW_NUMBER() OVER (PARTITION BY department_id ORDER BY salary DESC) AS row_num
FROM employees;
```

#### 2. PERINGKAT dan DENSE_RANK
Beri peringkat karyawan berdasarkan gaji dalam departemen mereka:

```sql
-- RANK Example
SELECT employee_id, department_id, salary,
       RANK() OVER (PARTITION BY department_id ORDER BY salary DESC) AS rank
FROM employees;

-- DENSE_RANK Example
SELECT employee_id, department_id, salary,
       DENSE_RANK() OVER (PARTITION BY department_id ORDER BY salary DESC) AS dense_rank
FROM employees;
```

#### 3. NTILE
Bagilah karyawan menjadi 4 kuartil gaji:

```sql
SELECT employee_id, department_id, salary,
       NTILE(4) OVER (PARTITION BY department_id ORDER BY salary) AS quartile
FROM employees;
```

#### 4. LEAD dan LAG
Ambil gaji karyawan sebelumnya dan berikutnya:

```sql
SELECT employee_id, salary,
       LAG(salary) OVER (ORDER BY salary) AS prev_salary,
       LEAD(salary) OVER (ORDER BY salary) AS next_salary
FROM employees;
```

#### 5. FIRST_VALUE dan LAST_VALUE
Dapatkan gaji pertama dan terakhir di setiap departemen:

```sql
SELECT employee_id, department_id, salary,
       FIRST_VALUE(salary) OVER (PARTITION BY department_id ORDER BY salary) AS min_salary,
       LAST_VALUE(salary) OVER (PARTITION BY department_id ORDER BY salary ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING) AS max_salary
FROM employees;
```

#### 6. Klausa OVER
Klausa `OVER` mendefinisikan jendela atau kumpulan baris tempat fungsi jendela beroperasi.Ini dapat mencakup komponen-komponen berikut:

1. **PARTITION BY**: Membagi kumpulan hasil menjadi beberapa partisi.
2. **ORDER BY**: Menentukan urutan baris dalam setiap partisi.
3. **ROWS atau RANGE**: Mendefinisikan kerangka baris untuk perhitungan.

```sql
SELECT employee_id, salary,
       SUM(salary) OVER (PARTITION BY department_id ORDER BY salary) AS cumulative_salary
FROM employees;

```

### 🔧 Praktik Terbaik
- **Gunakan PARTITION BY Wisely**: Mempartisi data secara bermakna untuk mendapatkan hasil yang akurat.
- **Optimalkan Kinerja**: Gabungkan Fungsi Jendela dengan kolom yang diindeks untuk meningkatkan kecepatan kueri.
- **Pahami ROWS vs RANGE**: Perjelas bagaimana bingkai jendela memengaruhi penghitungan.
- **Hindari Perhitungan yang Tumpang Tindih**: Kurangi redundansi dengan meminimalkan jumlah Fungsi Jendela dalam kueri.

### 🎯 Tantangan Praktis

1. Gunakan ROW_NUMBER untuk mengidentifikasi 3 penerima teratas di setiap departemen.
2. Gunakan RANK dan DENSE_RANK untuk menentukan peringkat karyawan berdasarkan skor kinerja mereka.
3. Hitung total penjualan berjalan menggunakan Fungsi Jendela.
4. Gunakan LEAD dan LAG untuk membandingkan penjualan produk dengan kinerja bulan sebelumnya dan bulan depan.
5. Ambil jumlah transaksi pertama dan terakhir untuk setiap pelanggan menggunakan FIRST_VALUE dan LAST_VALUE.

## 💻 Latihan - Hari ke-16

#### ✅ Latihan: Tingkat 1
1. Tuliskan query untuk memberikan nomor baris kepada siswa di setiap kelas berdasarkan nilai mereka.
2. Beri peringkat produk berdasarkan pendapatan penjualan dalam setiap kategori.
3. Ambil jumlah pesanan sebelumnya dan berikutnya untuk setiap pelanggan.

#### 🚀 Latihan: Tingkat 2
1. Bagilah karyawan menjadi 3 kelompok berdasarkan gajinya dan berikan ID kelompok.
2. Hitung jumlah kumulatif penjualan untuk setiap kategori produk.
3. Ambil jumlah pembelian pertama dan terakhir untuk setiap wilayah di tabel penjualan.

### 📝 Ringkasan Hari ke-16
Hari ini, Anda menguasai Fungsi Jendela di SQL, termasuk ROW_NUMBER, RANK, NTILE, dan FIRST_VALUE.Alat-alat ini memungkinkan analisis data yang canggih sambil mempertahankan detail tingkat baris.Bereksperimenlah dengan menggabungkan fungsi-fungsi ini untuk mendapatkan wawasan yang kuat.

Nantikan Hari ke-17, di mana kita akan menjelajahi Common Table Expressions (CTEs) dalam SQL!🚀
