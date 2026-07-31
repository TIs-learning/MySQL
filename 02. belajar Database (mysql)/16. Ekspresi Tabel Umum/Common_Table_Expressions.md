📘 30 Hari SQL: Hari ke-17 - Ekspresi Tabel Umum (CTE) dalam SQL

Hari ini, kita akan membahas Common Table Expressions (CTE), alat penting untuk menulis kueri SQL yang jelas, modular, dan dapat digunakan kembali. Mari kita uraikan struktur dan kekuatannya!

### 🔍 Gambaran Umum

CTE (Common Table Expression) adalah kumpulan hasil sementara yang menyederhanakan kueri kompleks. CTE membuat kode SQL Anda lebih mudah dibaca dan dipelihara dengan memungkinkan Anda membangun kueri modular. CTE sangat berguna untuk:

- Membagi kueri kompleks menjadi langkah-langkah logis.
- Membuat komponen kueri yang dapat digunakan kembali.
- Mengimplementasikan kueri rekursif.
---

### 📘 Sintaks dan Komponen

#### 1. Dasar-Dasar Klausa WITH

Klausa `WITH` memperkenalkan CTE. Berikut sintaks umumnya:

```sql
WITH cte_name AS (
    SELECT column1, column2
    FROM table_name
    WHERE condition
)
SELECT *
FROM cte_name;
```

**Example**:

```sql
WITH SalesSummary AS (
    SELECT product_id, SUM(sales_amount) AS total_sales
    FROM sales
    GROUP BY product_id
)
SELECT *
FROM SalesSummary
WHERE total_sales > 1000;
```

#### 2. CTE Rekursif

CTE rekursif memungkinkan kueri untuk merujuk pada dirinya sendiri. CTE ini umumnya digunakan untuk data hierarkis, seperti bagan organisasi atau struktur pohon.

**Syntax**:

```sql
WITH RECURSIVE cte_name AS (
    -- Anchor member
    SELECT column1, column2
    FROM table_name
    WHERE condition

    UNION ALL

    -- Recursive member
    SELECT column1, column2
    FROM table_name
    INNER JOIN cte_name
    ON table_name.column = cte_name.column
)
SELECT *
FROM cte_name;
```

**Example**:

```sql
WITH RECURSIVE EmployeeHierarchy AS (
    -- Anchor member: Get top-level manager
    SELECT employee_id, manager_id, 1 AS level
    FROM employees
    WHERE manager_id IS NULL

    UNION ALL

    -- Recursive member: Get employees reporting to the previous level
    SELECT e.employee_id, e.manager_id, eh.level + 1
    FROM employees e
    INNER JOIN EmployeeHierarchy eh
    ON e.manager_id = eh.employee_id
)
SELECT *
FROM EmployeeHierarchy;
```

---

### 💡 Contoh Praktis

#### 1. Menyederhanakan Penggabungan yang Kompleks

Gunakan CTE untuk memecah operasi penggabungan multi-langkah:

```sql
WITH FilteredOrders AS (
    SELECT order_id, customer_id
    FROM orders
    WHERE order_date >= '2024-01-01'
),
CustomerSummary AS (
    SELECT customer_id, COUNT(order_id) AS order_count
    FROM FilteredOrders
    GROUP BY customer_id
)
SELECT *
FROM CustomerSummary
WHERE order_count > 5;
```

#### 2. Menghasilkan Total Berjalan

```sql
WITH RunningTotal AS (
    SELECT order_id, customer_id, order_date,
           SUM(order_amount) OVER (PARTITION BY customer_id ORDER BY order_date) AS cumulative_sales
    FROM orders
)
SELECT *
FROM RunningTotal
WHERE cumulative_sales > 500;
```

#### 3. Menelusuri Data Hierarkis

```sql
WITH RECURSIVE OrgChart AS (
    SELECT employee_id, manager_id, 0 AS level
    FROM employees
    WHERE manager_id IS NULL

    UNION ALL

    SELECT e.employee_id, e.manager_id, oc.level + 1
    FROM employees e
    INNER JOIN OrgChart oc
    ON e.manager_id = oc.employee_id
)
SELECT *
FROM OrgChart
ORDER BY level;
```

---

### 🔧 Praktik Terbaik

- **Gunakan Nama yang Deskriptif**: Beri nama CTE Anda dengan jelas untuk mencerminkan tujuannya.
- **Batasi Cakupan**: Hindari CTE yang terlalu besar atau kompleks; fokuskan pada tujuan.
- **Optimalkan Kinerja**: Gunakan kolom yang diindeks dan hindari komputasi yang tidak perlu di dalam CTE.
- **Uji Rekursi**: Untuk CTE rekursif, pastikan ada kondisi penghentian untuk menghindari perulangan tak terbatas.

---

### 🎯 Tantangan Praktik Langsung

1. Buat CTE untuk menghitung rata-rata penjualan untuk setiap kategori produk dan filter kategori dengan penjualan di atas rata-rata.
2. Gunakan CTE rekursif untuk menampilkan hierarki organisasi perusahaan.
3. Implementasikan CTE untuk menemukan pelanggan dengan lebih dari 3 pesanan dalam setahun terakhir.
4. Tulis kueri menggunakan beberapa CTE untuk menganalisis kinerja produk berdasarkan wilayah.

---

### 💻 Latihan - Hari ke-17

#### ✅ Latihan: Level 1

1. Tulis kueri menggunakan CTE untuk menampilkan semua karyawan di departemen tertentu.
2. Buat CTE untuk menghitung total pendapatan untuk setiap wilayah.
3. Gunakan CTE rekursif untuk menemukan rantai komando untuk karyawan tertentu.

#### 🚀 Latihan: Level 2

1. Gunakan beberapa CTE untuk menganalisis tren penjualan bulanan selama setahun terakhir.
2. Implementasikan CTE rekursif untuk menghitung faktorial suatu angka.
3. Tulis kueri menggunakan CTE untuk mengidentifikasi 5 produk teratas berdasarkan pendapatan.

---

### 📝 Ringkasan Hari ke-17

Hari ini, Anda telah mempelajari tentang Common Table Expressions (CTE) dan bagaimana CTE menyederhanakan kueri yang kompleks. Anda telah menjelajahi CTE dasar dan rekursif, aplikasi praktis, dan praktik terbaik. Dengan CTE, kueri SQL Anda dapat lebih modular, mudah dibaca, dan lebih ampuh.

Nantikan Hari ke-18, di mana kita akan membahas Indeks dan Optimasi Kueri! 🚀

---