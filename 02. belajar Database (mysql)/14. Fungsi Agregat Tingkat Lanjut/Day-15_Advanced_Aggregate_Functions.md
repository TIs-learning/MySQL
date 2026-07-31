# 📘 30 Hari SQL: Hari ke-15 - Fungsi Agregat Tingkat Lanjut di SQL

Hari ini, kita akan mempelajari lebih dalam **Fungsi Agregat Tingkat Lanjut**—alat penting untuk menganalisis dan meringkas data di SQL. Jika Anda sudah menguasai dasar-dasar `SUM`, `COUNT`, dan `AVG`, bersiaplah untuk meningkatkan keterampilan SQL Anda dengan menjelajahi fungsi agregat yang lebih kompleks dan ampuh.

## 🔍 Gambaran Umum

Fungsi agregat SQL sangat penting untuk meringkas dan menganalisis data. Meskipun agregat dasar seperti `SUM`, `AVG`, dan `COUNT` umum digunakan, fungsi agregat tingkat lanjut membuka wawasan yang lebih dalam ke dalam kumpulan data Anda. Fungsi ini membantu Anda:

- Menggabungkan string menjadi satu nilai.
- Menghitung ukuran statistik seperti median, varians, dan deviasi standar.
- Melakukan agregasi hierarkis dengan `ROLLUP` dan `CUBE`.
- Menangani agregasi berbeda secara lebih fleksibel.

## 📘 Fungsi Agregasi Utama

Berikut adalah uraian fungsi agregasi tingkat lanjut, sintaksnya, dan kasus penggunaannya.

### Jenis Fungsi Agregasi Tingkat Lanjut 🏆

| **Fungsi** | **Deskripsi** |
|--|-|
| **`VARIANCE`** | Menghitung varians kolom numerik. |
| **`STDDEV`** | Menghitung deviasi standar kolom numerik. |
| **`MEDIAN`** | Menemukan nilai median kolom numerik. |
| **`PERCENTILE_DISC`** | Mengembalikan persentil tertentu (diskrit). |
| **`PERCENTILE_CONT`** | Mengembalikan persentil tertentu (kontinu). |
| **`CUME_DIST`** | Menghitung distribusi kumulatif suatu nilai dalam kumpulan hasil. |
| **`NTILE`** | Membagi baris menjadi sejumlah grup yang ditentukan dan menetapkan ID grup. |

### **1. GROUP_CONCAT / STRING_AGG**
- **Tujuan**: Menggabungkan nilai dari beberapa baris menjadi satu string.
- **Basis Data yang Didukung**:
- `GROUP_CONCAT` (MySQL)
- `STRING_AGG` (PostgreSQL, SQL Server)

**Syntax**:  
- MySQL: 
  ```sql
  SELECT GROUP_CONCAT(column_name SEPARATOR ', ') AS concatenated_values
  FROM table_name;
  ```
- PostgreSQL:
  ```sql
  SELECT STRING_AGG(column_name, ', ') AS concatenated_values
  FROM table_name;
  ```

**Example**:
```sql
SELECT STRING_AGG(product_name, ', ') AS products
FROM orders
WHERE category = 'Electronics';
```

### **2. LISTAGG (Oracle)**

- **Tujuan**: Mirip dengan `GROUP_CONCAT`, tetapi khusus untuk basis data Oracle.
- **Syntax**:
  ```sql
  SELECT LISTAGG(column_name, ', ') WITHIN GROUP (ORDER BY column_name) AS concatenated_values
  FROM table_name;
  ```

**Example**:
```sql
SELECT LISTAGG(employee_name, ', ') WITHIN GROUP (ORDER BY hire_date) AS employee_list
FROM employees
WHERE department = 'HR';
```

### **3. MEDIAN**

- **Tujuan**: Menghitung nilai median dari kolom numerik.
- **Basis Data yang Didukung**: Oracle, PostgreSQL, SQL Server (dengan fungsi persentil).

**Syntax**:
```sql
SELECT MEDIAN(column_name) AS median_value
FROM table_name;
```

**Example**:
```sql
SELECT MEDIAN(salary) AS median_salary
FROM employees
WHERE department_id = 10;
```

### **4. PERCENTILE_CONT dan PERCENTILE_DISC**
- **Tujuan**: Menghitung persentil.
- `PERCENTILE_CONT`: Persentil kontinu.
- `PERCENTILE_DISC`: Persentil diskrit.

- **Basis Data yang Didukung**: PostgreSQL, Oracle, SQL Server.

**Syntax** (PostgreSQL):
```sql
SELECT PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY column_name) AS median
FROM table_name;
```

**Example**:
```sql
SELECT PERCENTILE_CONT(0.9) WITHIN GROUP (ORDER BY score) AS top_10_percent
FROM test_results;
```

### **5. STDDEV dan VARIANS**

- **Tujuan**: Menghitung ukuran statistik seperti deviasi standar dan varians.
- **Basis Data yang Didukung**: Semua basis data utama.

**Syntax**:
```sql
SELECT STDDEV(column_name) AS std_dev, VARIANCE(column_name) AS var
FROM table_name;
```

**Example**:
```sql
SELECT STDDEV(salary) AS salary_stddev, VARIANCE(salary) AS salary_variance
FROM employees;
```

### **6. ROLLUP dan CUBE**

- **Tujuan**: Menghasilkan subtotal dan total keseluruhan untuk data hierarkis.
- **Basis Data yang Didukung**: PostgreSQL, MySQL, SQL Server, Oracle.

**Syntax** (ROLLUP):
```sql
SELECT department_id, SUM(salary) AS total_salary
FROM employees
GROUP BY ROLLUP(department_id);
```

**Syntax** (CUBE):
```sql
SELECT product_id, region, SUM(sales) AS total_sales
FROM sales_data
GROUP BY CUBE(product_id, region);
```

### **7. MENGHITUNG NILAI UNIK DENGAN FILTER**

- **Tujuan**: Menghitung nilai unik dengan kondisi tambahan.
- **Basis Data yang Didukung**: PostgreSQL.

**Syntax**:
```sql
SELECT COUNT(DISTINCT column_name) FILTER (WHERE condition) AS count_value
FROM table_name;
```

**Example**:
```sql
SELECT COUNT(DISTINCT customer_id) FILTER (WHERE region = 'North') AS north_customers
FROM orders;
```

## 💡 Contoh Praktis
Berikut adalah contoh penggunaan fungsi agregasi tingkat lanjut di dunia nyata:

1. **Agregasi String**:
  Hasilkan daftar nama karyawan berdasarkan departemen yang dipisahkan oleh koma.

   ```sql
   SELECT department_id, STRING_AGG(employee_name, ', ') AS employee_list
   FROM employees
   GROUP BY department_id;
   ```

2. **Gaji Median**:
  Carilah gaji median di setiap departemen.

   ```sql
   SELECT department_id, PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY salary) AS median_salary
   FROM employees
   GROUP BY department_id;
   ```

3. **Wawasan Statistik**:
  Analisis distribusi gaji dengan deviasi standar dan varians.

   ```sql
   SELECT department_id, STDDEV(salary) AS salary_stddev, VARIANCE(salary) AS salary_variance
   FROM employees
   GROUP BY department_id;
   ```

4. **Agregasi Hierarkis**:
  Dapatkan total penjualan berdasarkan wilayah dan total keseluruhan menggunakan `ROLLUP`.

   ```sql
   SELECT region, SUM(sales) AS total_sales
   FROM sales_data
   GROUP BY ROLLUP(region);
   ```

### Sintaks 🔧

Setiap fungsi agregat tingkat lanjut mengikuti sintaks umum ini:

```sql
SELECT aggregate_function(column_name) AS result_alias
FROM table_name
[GROUP BY column_name]
[ORDER BY column_name];
```

## 📚 Contoh

#### Contoh 1: Varians dan Deviasi Standar
Misalkan kita memiliki tabel `sales`:
| region | sales_amount |
|-|--|
| North | 5000 |
| South | 7000 |
| East | 6000 |
| West | 8000 |
| North | 5500 |
Untuk menghitung varians dan deviasi standar dari `sales_amount`:

```sql
SELECT
    VARIANCE(sales_amount) AS sales_variance,
    STDDEV(sales_amount) AS sales_stddev
FROM sales;
```

**Result:**

| sales_variance | sales_stddev |
|-|--|
| 1250000        | 1118.03      |

#### Contoh 2: Median dan Persentil

Untuk menghitung median dan persentil ke-75 dari `sales_amount`:

```sql
SELECT
    MEDIAN(sales_amount) AS median_sales,
    PERCENTILE_CONT(0.75) WITHIN GROUP (ORDER BY sales_amount) AS percentile_75
FROM sales;
```

**Hasil:**

| median_penjualan | persentil_75 |
|--|-|
| 6000 | 7500 |

#### Contoh 3: Distribusi Kumulatif

Untuk menghitung distribusi kumulatif jumlah penjualan:

```sql
SELECT
    sales_amount,
    CUME_DIST() OVER (ORDER BY sales_amount) AS cumulative_distribution
FROM sales;
```

**Result:**

| sales_amount | cumulative_distribution |
|--|--|
| 5000         | 0.2                      |
| 5500         | 0.4                      |
| 6000         | 0.6                      |
| 7000         | 0.8                      |
| 8000         | 1.0                      |

#### Contoh 4: Pengelompokan dengan NTILE

Untuk membagi penjualan menjadi 2 kelompok (kuartil):

```sql
SELECT
    sales_amount,
    NTILE(2) OVER (ORDER BY sales_amount) AS group_id
FROM sales;
```

**Result:**

| sales_amount | group_id |
|--|-|
| 5000         | 1        |
| 5500         | 1        |
| 6000         | 2        |
| 7000         | 2        |
| 8000         | 2        |

## 🔧 Praktik Terbaik

1. **Optimalkan Kueri**: Gunakan fungsi agregasi dengan indeks yang tepat untuk menghindari masalah kinerja.
2. **Manfaatkan Fitur Khusus Basis Data**: Beberapa basis data mendukung fungsi-fungsi canggih secara bawaan—gunakan fungsi-fungsi tersebut untuk kinerja yang lebih baik.
3. **Pahami Penanganan Nilai Null**: Perhatikan bagaimana nilai NULL diperlakukan dalam fungsi agregasi.
4. **Gabungkan Agregasi dengan Filter**: Gunakan klausa `FILTER` atau `HAVING` untuk menargetkan subset data tertentu.

## 🎯 Tantangan Praktik Langsung

1. **Agregasi String**: Tulis kueri untuk mencantumkan semua nama produk yang terjual di setiap wilayah.
2. **Perhitungan Median**: Temukan pendapatan median yang dihasilkan oleh pesanan di setiap bulan.
3. **Analisis Statistik**: Hitung varians dan deviasi standar bonus karyawan di seluruh departemen.
4. **Agregasi Hierarkis**: Gunakan `CUBE` untuk menganalisis data penjualan berdasarkan produk dan wilayah.

## 💻 Latihan - Hari ke-15

### ✅ Latihan: Level 1

1. Gunakan `GROUP_CONCAT` atau `STRING_AGG` untuk membuat daftar nama pelanggan berdasarkan kota.
2. Temukan jumlah pembelian median untuk setiap pelanggan.
3. Hitung simpangan baku harga produk dalam basis data Anda.

### 🚀 Latihan: Level 2

1. Gunakan `ROLLUP` untuk mendapatkan subtotal dan total keseluruhan penjualan berdasarkan wilayah dan kategori produk.
2. Tulis kueri untuk menghitung persentil ke-90 dari jumlah transaksi untuk setiap hari.
3. Buat laporan yang menunjukkan varians gaji karyawan yang dikelompokkan berdasarkan jabatan.

## 📝 Ringkasan Hari ke-15

Hari ini, Anda telah menguasai **Fungsi Agregasi Tingkat Lanjut dalam SQL**, termasuk penggabungan string, ukuran statistik, dan agregasi hierarkis. Alat-alat ini memberdayakan Anda untuk mengungkap wawasan yang lebih dalam dari data Anda. Berlatihlah menggabungkan fungsi-fungsi ini dengan `GROUP BY`, `HAVING`, dan pemfilteran untuk membuat kueri yang ampuh.

Nantikan **Hari ke-16**, di mana kita akan menjelajahi **Fungsi Jendela** di SQL! 🚀