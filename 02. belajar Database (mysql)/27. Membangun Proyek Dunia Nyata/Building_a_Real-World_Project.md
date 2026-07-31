# 30 Hari SQL: Hari ke-28 - Membangun Proyek Dunia Nyata

Selamat datang di **Hari ke-28** dari tantangan **30 Hari SQL**! 🎉 Hari ini, kita akan menggunakan pendekatan praktik dengan menerapkan semua yang telah Anda pelajari untuk membangun proyek SQL dunia nyata. Ini adalah kesempatan Anda untuk mengkonsolidasikan pengetahuan Anda, mengatasi tantangan praktis, dan mendapatkan kepercayaan diri dalam memecahkan masalah data yang kompleks.

## Gambaran Umum Proyek

### Judul Proyek: **Analisis Penjualan untuk Platform E-Commerce**

Anda akan merancang dan mengeksekusi kueri SQL untuk menganalisis data penjualan untuk perusahaan e-commerce online. Tujuannya adalah untuk menghasilkan wawasan tentang tren penjualan, perilaku pelanggan, dan kinerja produk. Wawasan ini dapat membantu perusahaan meningkatkan proses pengambilan keputusannya.

## Deskripsi Dataset

Kita akan bekerja dengan tabel berikut:

### 1. **Pelanggan**
| **Kolom** | **Tipe Data** | **Deskripsi** |

|-------------------|---------------|-------------------------------------------|

| customer_id | INT | Pengidentifikasi unik untuk setiap pelanggan. |

| first_name | VARCHAR | Nama depan pelanggan. |

| last_name | VARCHAR | Nama belakang pelanggan. |

| email | VARCHAR | Alamat email pelanggan. |

| registration_date | DATE | Tanggal pelanggan mendaftar. |

| country | VARCHAR | Negara pelanggan. |

### 2. **Produk**
| **Kolom** | **Tipe Data** | **Deskripsi** |

|-------------------|---------------|-------------------------------------------|

| product_id | INT | Pengidentifikasi unik untuk setiap produk. |

| product_name | VARCHAR | Nama produk. |

| kategori | VARCHAR | Kategori produk. |

| harga | DECIMAL | Harga produk. |

| jumlah_stok | INT | Jumlah produk yang tersedia. |

### 3. **Pesanan**
| **Kolom** | **Tipe Data** | **Deskripsi** |

|-------------------|---------------|-------------------------------------------|

| order_id | INT | Pengidentifikasi unik untuk setiap pesanan. |

| customer_id | INT | ID pelanggan yang melakukan pemesanan. |

| order_date | DATE | Tanggal pemesanan dilakukan. |

| total_amount | DECIMAL | Jumlah total pesanan. |

### 4. **Detail_Pesanan**
| **Kolom** | **Tipe Data** | **Deskripsi** |

|-------------------|---------------|-------------------------------------------|

| order_detail_id | INT | Pengidentifikasi unik untuk setiap detail pesanan. |

| order_id | INT | ID pesanan terkait. |

| product_id | INT | ID produk dalam pesanan. |

| quantity | INT | Kuantitas produk yang dipesan. |

| line_total | DECIMAL | Total harga untuk baris ini (harga x kuantitas). |

## Tugas Proyek

### 1. Eksplorasi Data Dasar
- Lihat beberapa baris pertama dari setiap tabel untuk memahami data.

- Periksa apakah ada nilai yang hilang atau inkonsistensi.

### 2. Analisis Perilaku Pelanggan
- Temukan jumlah total pelanggan dan jumlah pelanggan berdasarkan negara.

- Mengidentifikasi 5 negara teratas dengan jumlah pelanggan terbanyak.

- Menghitung rata-rata jumlah pesanan per pelanggan.

### 3. Analisis Kinerja Produk
- Mencantumkan 10 produk terlaris berdasarkan total kuantitas terjual.

- Mengidentifikasi 5 kategori produk teratas berdasarkan pendapatan.

- Menemukan produk yang berkinerja buruk (penjualan rendah dan stok tinggi).

### 4. Analisis Tren Penjualan
- Menghitung pendapatan penjualan bulanan selama setahun terakhir.

- Mengidentifikasi bulan dengan penjualan tertinggi.

- Menentukan nilai pesanan rata-rata (AOV).

### 5. Wawasan Lanjutan
- Menganalisis pelanggan tetap dengan mengidentifikasi pelanggan yang melakukan lebih dari 3 pesanan.

- Menemukan kombinasi produk-kategori yang menghasilkan pendapatan terbanyak.

- Menghitung persentase kontribusi setiap produk terhadap total pendapatan.

## Kueri SQL

Berikut beberapa contoh kueri yang akan Anda tulis untuk proyek ini:

### 1. Melihat Data dari Tabel
```sql
SELECT *
FROM Customers
LIMIT 10;
```

### 2. Jumlah Total Pelanggan
```sql
SELECT COUNT(*) AS total_customers
FROM Customers;
```

### 3. Produk Terlaris
```sql
SELECT p.product_name, SUM(od.quantity) AS total_quantity_sold
FROM Order_Details od
JOIN Products p ON od.product_id = p.product_id
GROUP BY p.product_name
ORDER BY total_quantity_sold DESC
LIMIT 10;
```

### 4. Pendapatan Penjualan Bulanan
```sql
SELECT DATE_TRUNC('month', order_date) AS month, SUM(total_amount) AS monthly_revenue
FROM Orders
GROUP BY month
ORDER BY month;
```

### 5. Pelanggan Tetap
```sql
SELECT c.customer_id, COUNT(o.order_id) AS order_count
FROM Customers c
JOIN Orders o ON c.customer_id = o.customer_id
GROUP BY c.customer_id
HAVING COUNT(o.order_id) > 3;
```

## Hasil yang Harus Diserahkan

1. **Skrip SQL**: Kumpulan semua kueri yang Anda tulis selama proyek.

2. **Laporan Analisis**: Laporan singkat yang merangkum temuan Anda.

3. **Visualisasi** (Opsional): Gunakan alat seperti Tableau atau Excel untuk membuat visualisasi metrik utama.

## Tantangan Praktik

- Tulis kueri SQL untuk menjawab pertanyaan dalam tugas di atas.

- Dokumentasikan proses dan hasil Anda.

- Bagikan wawasan dan saran Anda untuk meningkatkan kinerja platform e-commerce.

## Ringkasan

Hari ini, Anda menerapkan pengetahuan SQL Anda pada proyek dunia nyata yang melibatkan analisis data untuk perusahaan e-commerce. Latihan ini merupakan puncak dari konsep yang telah Anda pelajari sejauh ini, mempersiapkan Anda untuk tantangan SQL di dunia nyata.

Selanjutnya, **Hari ke-29: Revisi Akhir**, di mana kita akan meninjau kembali semua yang telah kita bahas dalam 28 hari terakhir. 🚀