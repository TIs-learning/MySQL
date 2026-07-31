# Hari 7: Latihan dan Kuis SQL 🎯

Hari ini, kami akan menggabungkan pembelajaran kami dari enam hari terakhir dengan latihan soal dan kuis.Mari pertajam keterampilan SQL Anda dengan tugas praktis dan pertanyaan yang menantang.⚡️

### Latihan Soal 🏋

#### Masalah 1: Total Penjualan berdasarkan Wilayah

Diberikan tabel `sales` berikut:

|penjual |wilayah |jumlah_penjualan |
|-------------|------------|--------------|
|Alice |Utara |5000 |
|Bob |Selatan |7000 |
|Alice |Utara |3000 |
|Bob |Selatan |2000 |
|Karol |Timur |8000 |

**Tugas:** Menulis kueri untuk menemukan total penjualan untuk setiap wilayah.

#### Soal 2: Nilai Rata-Rata Berdasarkan Kelas

Diberikan tabel `students` berikut:

|kelas |nama_siswa |skor |
|--------|--------------|-------|
|SEBUAH |Yohanes |85 |
|SEBUAH |Maria |90 |
|B |jake |70 |
|B |Emily |75 |
|SEBUAH |Steve |95 |

**Tugas:** Menulis kueri untuk menemukan nilai rata-rata setiap kelas.

#### Masalah 3: Tenaga Penjual dengan Penjualan Tinggi

Diberikan tabel `sales` yang sama dengan Soal 1:

**Tugas:** Menulis kueri untuk menemukan tenaga penjualan dengan total penjualan lebih dari 8000.

#### Soal 4: Siswa dengan Entri Lebih dari Satu

Diberikan tabel `students`:

**Tugas:** Menulis kueri untuk menemukan semua siswa yang muncul lebih dari satu kali dalam tabel.

### Pertanyaan Kuis 🎮

#### Pertanyaan 1: Memfilter dengan WHERE dan HAVING

Manakah dari pernyataan berikut yang benar?

- (A) `WHERE` memfilter baris sebelum pengelompokan, sedangkan `HAVING` memfilter grup setelah agregasi.
- (B) `HAVING` memfilter baris sebelum pengelompokan, sedangkan `WHERE` memfilter grup setelah agregasi.
- (C) Baris filter `WHERE` dan `HAVING` setelah pengelompokan.
- (D) Tidak satu pun di atas.

#### Pertanyaan 2: Agregasi

Apa yang akan dikembalikan oleh kueri berikut?

```sql
SELECT region, COUNT(*) AS region_count
FROM sales
GROUP BY region;
```

- (A) Jumlah wilayah.
- (B) Hitungan penjualan di masing-masing wilayah.
- (C) Jumlah wilayah unik.
- (D) Tidak satu pun di atas.

#### Pertanyaan 3: Menggabungkan GROUP BY dan HAVING

Diberikan tabel `orders` berikut:

|id_pelanggan |jumlah_pesanan |
|-------------|--------------|
|1 |100 |
|2 |200 |
|1 |300 |
|2 |400 |
|3 |500 |

Apa yang dikembalikan oleh kueri ini?

```sql
SELECT customer_id, SUM(order_amount) AS total_amount
FROM orders
GROUP BY customer_id
HAVING total_amount > 400;
```

- (A) Pelanggan yang total pesanannya melebihi 400.
- (B) Pelanggan dengan lebih dari satu pesanan.
- (C) Jumlah total semua pesanan.
- (D) Tidak satu pun di atas.

### Solusi 🕵

#### Latihan Soal

1. **Total Penjualan berdasarkan Wilayah**:

```sql
SELECT region, SUM(sales_amount) AS total_sales
FROM sales
GROUP BY region;
```

2. **Nilai Rata-Rata Berdasarkan Kelas**:

```sql
SELECT class, AVG(score) AS average_score
FROM students
GROUP BY class;
```

3. **Tenaga Penjualan dengan Penjualan Tinggi**:

```sql
SELECT salesperson, SUM(sales_amount) AS total_sales
FROM sales
GROUP BY salesperson
HAVING total_sales > 10000;
```

4. **Siswa dengan Lebih dari Satu Entri**:

```sql
SELECT student_name, COUNT(*) AS entry_count
FROM students
GROUP BY student_name
HAVING entry_count > 1;
```

#### Jawaban Kuis

1. **(A)**: `WHERE` memfilter baris sebelum pengelompokan, sedangkan `HAVING` memfilter grup setelah agregasi.
2. **(B)** : Jumlah penjualan di tiap wilayah.
3. **(A)**: Pelanggan yang total pesanannya melebihi 400.

### Langkah Selanjutnya 🔄

Kerja bagus hari ini!Latihan dan kuis membantu memperkuat pemahaman Anda.Besok, kita akan mendalami **Bergabung** dan mempelajari cara menggabungkan data dari beberapa tabel.Pantau terus!🎉