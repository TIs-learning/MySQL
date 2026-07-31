# 📘 30 Hari SQL: Hari ke-25 - SQL untuk Analisis

Selamat datang di **Hari ke-25** dari tantangan **30 Hari SQL**! 🎉 Hari ini, kita akan fokus pada bagaimana SQL dapat digunakan untuk analisis, mencakup teknik dan fungsi yang umum digunakan untuk mendapatkan wawasan dari data. Jika Anda bercita-cita menjadi analis atau ilmuwan data, sesi ini akan memberikan keterampilan yang sangat berharga.

## 🔍 Gambaran Umum

SQL adalah landasan alur kerja analitik, yang memungkinkan para profesional untuk:

- Mengekstrak dan mengubah data secara efisien.

- Menerapkan perhitungan dan agregasi tingkat lanjut.

- Membangun wawasan dengan peringkat, tren, dan pola.

- Melakukan analisis deret waktu dan kohort untuk wawasan yang dapat ditindaklanjuti.

Baik bekerja dengan gudang data terstruktur atau basis data transaksional besar, kekuatan SQL terletak pada kemampuannya untuk menangani analitik langsung di dalam basis data.

---

## 🔢 Konsep Kunci dalam SQL untuk Analisis

### 1. Fungsi Pemeringkatan

Fungsi pemeringkatan menetapkan peringkat atau nomor baris ke baris dalam kumpulan hasil, seringkali untuk tujuan pengurutan atau perbandingan. Fungsi pemeringkatan umum meliputi:

- **ROW_NUMBER**: Menetapkan bilangan bulat berurutan unik ke baris.

- **RANK**: Menetapkan peringkat, dengan celah untuk nilai yang sama.

- **DENSE_RANK**: Menetapkan peringkat tanpa celah.

**Syntax**:
```sql
SELECT
    column_name,
    RANK() OVER (PARTITION BY category ORDER BY sales DESC) AS rank
FROM sales_data;
```

---

### 2. Agregat Bergulir

Agregat bergulir menghitung metrik kumulatif selama periode baris yang ditentukan. Contohnya termasuk jumlah kumulatif atau rata-rata berjalan.

**Syntax**:
```sql
SELECT
    order_date,
    SUM(sales) OVER (ORDER BY order_date ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) AS cumulative_sales
FROM sales_data;
```

---

### 3. Memutar dan Mengembalikan Data ke Bentuk Asli

Memutar data mengubah baris menjadi kolom, sering digunakan untuk membentuk ulang data untuk analisis. Sebaliknya, mengembalikan kolom menjadi baris.

**Pivot Syntax** (SQL Server):
```sql
SELECT *
FROM sales_data
PIVOT (
    SUM(sales)
    FOR region IN ([North], [South], [East], [West])
) AS pivot_table;
```

**Unpivot Syntax** (SQL Server):
```sql
SELECT *
FROM sales_data
UNPIVOT (
    sales FOR region IN ([North], [South], [East], [West])
) AS unpivot_table;
```

---

### 4. Fungsi Jendela dalam Analisis

Fungsi jendela memungkinkan perhitungan di seluruh subset baris, yang umumnya digunakan untuk:
- Persentil dan peringkat persentil.

- Analisis keterlambatan dan keunggulan.

- Rata-rata bergerak.

**Example**:
```sql
SELECT
    product_id,
    sales,
    LAG(sales) OVER (PARTITION BY product_id ORDER BY sale_date) AS previous_day_sales
FROM sales_data;
```

---

### 5. Analisis Kohort

Analisis kohort mengelompokkan pengguna berdasarkan karakteristik yang sama, seperti tanggal pendaftaran, untuk menganalisis perilaku dari waktu ke waktu.

**Example**:
```sql
SELECT
    sign_up_month,
    cohort,
    COUNT(user_id) AS active_users
FROM (
    SELECT
        user_id,
        DATE_TRUNC('month', sign_up_date) AS cohort,
        DATE_TRUNC('month', last_active_date) AS sign_up_month
    FROM user_data
) subquery
GROUP BY cohort, sign_up_month;
```

---

### 6. Analisis Deret Waktu

Analisis deret waktu mengevaluasi tren dari waktu ke waktu, seringkali dengan pengelompokan dan agregasi berdasarkan waktu.

**Example**:
```sql
SELECT
    DATE_TRUNC('month', order_date) AS order_month,
    SUM(sales) AS total_sales
FROM sales_data
GROUP BY order_month;
```

---

## 📊 Aplikasi Praktis

1. **Segmentasi Pelanggan**: Menggunakan peringkat dan analisis kohort untuk mengidentifikasi pelanggan utama dan tren perilaku.

2. **Tren Pendapatan**: Menganalisis pertumbuhan atau penurunan pendapatan dari waktu ke waktu dengan data deret waktu.

3. **Analisis Churn**: Menggunakan fungsi lag untuk mengidentifikasi pelanggan yang tidak aktif dan potensi pola churn.

4. **Wawasan Operasional**: Menggabungkan dan memutar data operasional untuk memantau metrik kinerja.

---

## 🛠 Praktik Terbaik

- **Optimalkan Kueri**: Gunakan indeks untuk kumpulan data besar dan hindari komputasi yang tidak perlu.

- **Pahami Granularitas Data**: Sesuaikan kueri Anda dengan granularitas data (misalnya, harian, bulanan).

- **Gunakan Fungsi Jendela dengan Bijak**: Perhatikan konsumsi memori saat menggunakan fungsi jendela yang kompleks.

- **Visualisasikan Hasil**: Integrasikan kueri SQL dengan alat visualisasi untuk wawasan yang lebih jelas.

---

## 💻 Tantangan Praktik

1. Tulis kueri untuk memberi peringkat produk berdasarkan total penjualan di setiap wilayah.

2. Buat analisis deret waktu tren pendapatan bulanan.

3. Lakukan analisis kohort aktivitas pengguna berdasarkan bulan pendaftaran mereka.

4. Gunakan fungsi jendela untuk menghitung rata-rata bergulir 7 hari dari penjualan harian.

---

## 🔧 Latihan - Hari ke-25

### ✅ Latihan: Level 1

1. Gunakan `ROW_NUMBER` untuk memberi peringkat karyawan berdasarkan gaji mereka di setiap departemen.

2. Tulis kueri untuk menghitung penjualan kumulatif untuk setiap produk.

3. Pivot data penjualan untuk menunjukkan total penjualan berdasarkan wilayah untuk tahun tertentu.

### 🚀 Latihan: Level 2

1. Lakukan analisis kohort untuk mengevaluasi retensi pengguna berdasarkan bulan pendaftaran mereka.

2. Gunakan fungsi jendela untuk menghitung peringkat persentil untuk nilai siswa.

3. Buat kueri yang mengidentifikasi agen penjualan berkinerja terbaik berdasarkan wilayah.

---

## 🗋 Ringkasan Hari ke-25

Hari ini, kita telah menjelajahi **SQL untuk Analitik**, keterampilan penting untuk mendapatkan wawasan dari data. Dari pemeringkatan dan agregasi bergulir hingga analisis kohort dan deret waktu, Anda sekarang memiliki alat untuk mengatasi tantangan analitik dunia nyata. Gabungkan teknik-teknik ini untuk mengekstrak wawasan yang dapat ditindaklanjuti dan mendorong keputusan berbasis data.

Nantikan **Hari ke-26**, di mana kita akan membahas **Penanganan Kesalahan dan Debugging** di SQL! 🚀

