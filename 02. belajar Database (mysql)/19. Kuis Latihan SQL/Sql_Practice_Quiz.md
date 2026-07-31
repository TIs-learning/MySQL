📘 30 Hari SQL: Hari ke-20 - Latihan dan Kuis SQL Tingkat Lanjut

hari ini adalah tentang menerapkan apa yang telah Anda pelajari sejauh ini melalui latihan dan kuis untuk menguji keterampilan Anda.Mari pertajam kemampuan SQL Anda dengan skenario dunia nyata!

### 🔍 Ikhtisar

Sesi hari ini akan memperkuat pemahaman Anda tentang konsep-konsep utama SQL, termasuk:

- Fungsi agregat dan gabungan.
- Ekspresi Tabel Umum (CTE).
- Fungsi jendela dan aplikasinya.
- Subquery dan mengatur operasi.

Anda juga akan mencoba kuis untuk menilai pemahaman Anda tentang topik-topik lanjutan ini.

### 🧑‍💻 Skenario Latihan

#### 1. Agregat dan Gabungan

Tulis kueri untuk menghitung total pendapatan penjualan untuk setiap kategori produk pada tahun lalu, termasuk nama kategori dan total pendapatan.Gunakan fungsi gabungan dan agregat.

**Petunjuk:** Anda harus menggabungkan tabel `products` dengan tabel `sales` dan mengelompokkannya berdasarkan kategori.

```sql
SELECT p.category_name, SUM(s.amount) AS total_revenue
FROM products p
JOIN sales s ON p.product_id = s.product_id
WHERE s.sale_date >= '2024-01-01'
GROUP BY p.category_name
ORDER BY total_revenue DESC;
```

#### 2. CTE dan Fungsi Jendela

Gunakan CTE untuk membuat kumpulan hasil sementara pelanggan yang melakukan pembelian pada bulan lalu.Kemudian, gunakan fungsi jendela untuk menentukan peringkat pelanggan ini berdasarkan total pembelanjaan.

**Petunjuk:** Gabungkan CTE dan `RANK()`.

```sql
WITH RecentPurchases AS (
    SELECT customer_id, SUM(amount) AS total_spent
    FROM sales
    WHERE sale_date >= '2024-12-01'
    GROUP BY customer_id
)
SELECT customer_id, total_spent,
       RANK() OVER (ORDER BY total_spent DESC) AS rank
FROM RecentPurchases;
```

#### 3. Subkueri dan Operasi Set

Temukan pelanggan yang membeli dari kategori `electronics` dan `furniture`.

**Petunjuk:** Gunakan `INTERSECT` di antara dua subkueri.

```sql
SELECT customer_id
FROM sales
WHERE product_id IN (
    SELECT product_id
    FROM products
    WHERE category_name = 'electronics'
)
INTERSECT
SELECT customer_id
FROM sales
WHERE product_id IN (
    SELECT product_id
    FROM products
    WHERE category_name = 'furniture'
);
```

### 🎯 Kuis - Hari ke-20

#### 1. Pilihan Ganda

1. Klausa SQL manakah yang digunakan untuk mendefinisikan CTE?
- a) PILIH
- b) DENGAN
- c) SEBAGAI
- d) BUAT

2. Apa fungsi `ROW_NUMBER()`?
- a) Menghitung jumlah baris dalam sebuah tabel.
- b) Menetapkan nomor urut unik ke baris dalam partisi.
- c) Mengurutkan baris dalam urutan menurun.
- d) Menghapus baris duplikat dari kumpulan hasil.

#### 2. Tantangan Kueri

1. Tulis query menggunakan CTE rekursif untuk menghitung faktorial dari 5.
2. Gunakan fungsi jendela untuk menemukan jumlah total penjualan tertinggi kedua di tabel `sales`.
3. Gabungkan beberapa CTE untuk mengidentifikasi produk dengan kinerja terbaik berdasarkan wilayah.

### 📝 Ringkasan Hari ke-20

Hari ini, Anda menggabungkan pengetahuan SQL Anda dengan latihan praktis dan kuis.Dari agregat tingkat lanjut hingga CTE rekursif, Anda telah menjelajahi skenario yang mempersiapkan Anda menghadapi tantangan database dunia nyata.Teruslah berlatih, dan bersiaplah untuk Hari ke-21, saat kita akan membahas Pemodelan dan Normalisasi Data!🚀
