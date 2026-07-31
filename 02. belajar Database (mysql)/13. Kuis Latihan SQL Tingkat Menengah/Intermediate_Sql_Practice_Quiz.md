# Hari 14: Latihan dan Kuis SQL Tingkat Menengah 📚

Hari ini, Anda akan mengkonsolidasikan pengetahuan Anda dengan memecahkan **masalah SQL tingkat menengah** dan menguji keterampilan Anda dengan kuis.🎯✨

### Latihan Latihan 🔧

Berikut beberapa latihan soal berdasarkan konsep SQL yang telah Anda pelajari sejauh ini:

#### Masalah 1: Total Penjualan Per Wilayah
Gunakan tabel `sales` untuk menghitung total penjualan untuk setiap wilayah dan hanya menyertakan wilayah dengan penjualan lebih dari $10.000.

**Tabel: penjualan**

|penjual |wilayah |jumlah_penjualan |
|-------------|--------|--------------|
|Alice |Utara |5000 |
|Bob |Selatan |7000 |
|Alice |Utara |3000 |
|Bob |Selatan |2000 |
|Karol |Timur |8000 |

**Hasil yang Diharapkan:**

|wilayah |total_penjualan |
|--------|-------------|
|Selatan |12000 |

**Pertanyaan:**
```sql
SELECT region, SUM(sales_amount) AS total_sales
FROM sales
GROUP BY region
HAVING SUM(sales_amount) > 10000;
```

#### Soal 2: Nilai Rata-Rata Berdasarkan Kelas
Dari tabel `students`, carilah nilai rata-rata setiap kelas, tetapi hanya sertakan kelas yang memiliki nilai rata-rata di atas 75.

**Tabel: siswa**

|kelas |nama_siswa |skor |
|--------|--------------|-------|
|SEBUAH |Yohanes |85 |
|SEBUAH |Maria |90 |
|B |jake |70 |
|B |Emily |75 |
|SEBUAH |Steve |95 |

**Hasil yang Diharapkan:**

|kelas |skor_rata-rata |
|-------|---------------|
|SEBUAH |90,0 |

**Pertanyaan:**
```sql
SELECT class, AVG(score) AS average_score
FROM students
GROUP BY class
HAVING AVG(score) > 75;
```

#### Masalah 3: Pesanan Pelanggan
Dengan menggunakan tabel `orders`, temukan pelanggan yang telah melakukan lebih dari 3 pesanan dan total nilai pesanan melebihi $5000.

**Tabel: pesanan**

|id_pelanggan |nomor_pesanan |pesanan_total |
|-------------|----------|-------------|
|1 |101 |2000 |
|2 |102 |1500 |
|1 |103 |3000 |
|3 |104 |800 |
|2 |105 |2000 |
|1 |106 |1000 |

**Hasil yang Diharapkan:**

|id_pelanggan |total_pesanan |nilai_total |
|-------------|--------------|-------------|
|1 |3 |6000 |

**Pertanyaan:**
```sql
SELECT customer_id, COUNT(order_id) AS total_orders, SUM(order_total) AS total_value
FROM orders
GROUP BY customer_id
HAVING COUNT(order_id) > 3 AND SUM(order_total) > 5000;
```

### Pertanyaan Kuis 🕵

Uji pemahaman Anda dengan pertanyaan-pertanyaan ini:

#### Pertanyaan 1: Identifikasi Kueri yang Tidak Valid
Manakah dari pertanyaan berikut yang akan menghasilkan kesalahan?

1.```sql
   SELECT region, SUM(sales_amount)
   FROM sales
   GROUP BY region
   HAVING SUM(sales_amount) > 10000;
   ```
2. ```sql
   SELECT region
   FROM sales
   HAVING SUM(sales_amount) > 10000;
   ```
3.```sql
   SELECT region, AVG(sales_amount)
   FROM sales
   GROUP BY region
   HAVING AVG(sales_amount) > 4000;
   ```

#### Pertanyaan 2: Benar atau Salah
Klausa `HAVING` hanya dapat digunakan dengan fungsi agregat.

- [ ] Benar
- [ ] Salah

#### Pertanyaan 3: Isilah Bagian yang Kosong
Selesaikan kueri untuk menemukan wilayah dengan total penjualan lebih dari $15.000:

```sql
SELECT region, ________(sales_amount) AS total_sales
FROM sales
GROUP BY region
HAVING ________(sales_amount) > 15000;
```

### Kunci Jawaban 🔐

#### Pertanyaan 1: Identifikasi Kueri yang Tidak Valid
- Jawaban: Query 2 akan menghasilkan error karena klausa `HAVING` memerlukan klausa `GROUP BY`.

#### Pertanyaan 2: Benar atau Salah
- Jawaban: Benar

#### Pertanyaan 3: Isilah Bagian yang Kosong
- Jawaban:

```sql
SELECT region, SUM(sales_amount) AS total_sales
FROM sales
GROUP BY region
HAVING SUM(sales_amount) > 15000;
```

### Ringkasan 🌟

Hari ini, Anda berlatih konsep SQL tingkat menengah dan menguji pemahaman Anda dengan kuis.Latihan-latihan ini dirancang untuk memperkuat keterampilan Anda dan mempersiapkan Anda untuk topik yang lebih maju.Pertahankan kerja bagus Anda!🏋️‍♂️
