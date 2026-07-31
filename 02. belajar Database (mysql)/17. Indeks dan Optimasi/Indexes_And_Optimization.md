📘 30 Hari SQL: Hari ke-18 - Indeks dan Optimasi Kueri

Hari ini, kita akan menjelajahi cara menggunakan indeks untuk meningkatkan kinerja kueri dan seni optimasi kueri. Teknik-teknik ini penting untuk membuat kueri SQL Anda efisien dan terukur.

### 🔎 Gambaran Umum

Indeks adalah struktur data yang meningkatkan kecepatan pengambilan data. Namun, ada konsekuensinya: peningkatan penyimpanan dan operasi penulisan yang lebih lambat. Optimasi kueri yang efektif melibatkan pemanfaatan indeks dan penulisan kueri yang efisien.

---

### 📘 Memahami Indeks

#### 1. Jenis-Jenis Indeks

- **Indeks Utama**: Dibuat secara otomatis pada kunci utama.

- **Indeks Unik**: Memastikan nilai unik pada kolom yang diindeks.

- **Indeks Klaster**: Mengurutkan dan menyimpan baris data dalam tabel berdasarkan nilai kunci.

- **Indeks Non-Klaster**: Menyimpan penunjuk ke baris data sebenarnya.

- **Indeks Komposit**: Mengindeks beberapa kolom.

- **Indeks Teks Lengkap**: Dioptimalkan untuk pencarian teks.

#### 2. Cara Kerja Indeks

Indeks seperti daftar isi buku. Alih-alih memindai seluruh tabel, basis data menggunakan indeks untuk menemukan baris lebih cepat.

**Contoh Tanpa Indeks**:

```sql
SELECT *
FROM orders
WHERE customer_id = 12345;
```

**Contoh Dengan Indeks**:

```sql
CREATE INDEX idx_customer_id ON orders(customer_id);
SELECT *
FROM orders
WHERE customer_id = 12345;
```

#### 3. Membuat dan Mengelola Indeks

**Creating an Index**:

```sql
CREATE INDEX idx_column_name ON table_name(column_name);
```

**Dropping an Index**:

```sql
DROP INDEX idx_column_name;
```

**Viewing Existing Indexes** (PostgreSQL Example):

```sql
SELECT *
FROM pg_indexes
WHERE tablename = 'table_name';
```

---

### 🔧 Teknik Optimasi Kueri

#### 1. Menganalisis Rencana Kueri

Gunakan kata kunci `EXPLAIN` untuk memahami bagaimana basis data mengeksekusi kueri.

**Example**:

```sql
EXPLAIN SELECT *
FROM orders
WHERE order_date > '2024-01-01';
```

#### 2. Menghindari Kesalahan Umum

- **Hindari SELECT**: Tentukan hanya kolom yang dibutuhkan.
- **Penggunaan Indeks**: Pastikan indeks digunakan untuk pemfilteran dan penggabungan.
- **Hindari Fungsi pada Kolom yang Diindeks**:

```sql
-- Avoid
SELECT *
FROM orders
WHERE YEAR(order_date) = 2024;

-- Use
SELECT *
FROM orders
WHERE order_date >= '2024-01-01' AND order_date < '2025-01-01';
```

#### 3. Mengoptimalkan Penggabungan dan Subkueri

- Gunakan kolom yang diindeks dalam kondisi `JOIN`.
- Hindari subkueri yang tidak perlu; gunakan `WITH` (CTE) jika memungkinkan.

**Example**:

```sql
-- Inefficient Subquery
SELECT *
FROM orders
WHERE customer_id IN (
    SELECT customer_id
    FROM customers
    WHERE country = 'USA'
);

-- Optimized Query
WITH US_Customers AS (
    SELECT customer_id
    FROM customers
    WHERE country = 'USA'
)
SELECT *
FROM orders
JOIN US_Customers
ON orders.customer_id = US_Customers.customer_id;
```

---

### 🔄 Praktik Terbaik untuk Pengindeksan

- **Indeks Secara Selektif**: Indeks kolom yang sering digunakan dalam klausa `WHERE`, `JOIN`, atau `ORDER BY`.

- **Pantau Penggunaan Indeks**: Gunakan rencana eksekusi kueri untuk memastikan indeks dimanfaatkan.

- **Hindari Pengindeksan Berlebihan**: Terlalu banyak indeks dapat menurunkan kinerja untuk operasi `INSERT`, `UPDATE`, dan `DELETE`.

- **Pemeliharaan Rutin**: Bangun kembali atau atur ulang indeks yang terfragmentasi.

---

### 🔟 Tantangan Praktik

1. Buat indeks non-clustered pada kolom `order_date` dari tabel `orders` dan ukur kinerja kueri dengan dan tanpa indeks.
2. Gunakan `EXPLAIN` untuk menganalisis kueri dan mengidentifikasi peluang optimasi.
3. Optimalkan kueri menggunakan indeks komposit.

---

### 💻 Latihan - Hari ke-18

#### ✅ Latihan: Level 1

1. Buat indeks pada kolom `customer_id` di tabel `orders`.
2. Gunakan `EXPLAIN` untuk membandingkan rencana kueri untuk kueri dengan dan tanpa indeks.
3. Tulis kueri untuk menemukan semua pesanan yang dilakukan pada tahun 2024, dan optimalkan menggunakan indeks.

#### 🚀 Latihan: Level 2

1. Implementasikan indeks komposit pada `customer_id` dan `order_date` di tabel `orders`. Tulis kueri untuk mengambil pesanan untuk pelanggan tertentu dalam rentang tanggal.
2. Gunakan rencana kueri untuk menganalisis kinerja kueri gabungan yang kompleks dan sarankan optimasi.
3. Buat dan gunakan indeks teks lengkap untuk mencari kata kunci di kolom `comments`.

---

### 🗳 Ringkasan Hari ke-18

Hari ini, kita telah membahas pentingnya indeks dan optimasi kueri. Dengan memahami berbagai jenis indeks dan menerapkan praktik terbaik, Anda dapat meningkatkan kinerja kueri secara signifikan. Nantikan Hari ke-19, di mana kita akan membahas Transaksi dan Kontrol Konkurensi! 🚀

---