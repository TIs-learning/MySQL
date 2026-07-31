# Hari 9: Bergabung Tingkat Lanjut 🚀

Hari ini, kita akan mendalami dunia gabungan SQL, menjelajahi teknik gabungan tingkat lanjut untuk menangani hubungan data yang lebih kompleks.Mari kita mulai!🎉

### Apa itu Gabungan Tingkat Lanjut?🔍

Gabungan tingkat lanjut dibangun berdasarkan konsep gabungan dasar dengan memperkenalkan teknik yang lebih kompleks untuk menggabungkan tabel.Gabungan ini sangat berguna ketika bekerja dengan kumpulan data hierarki, multidimensi, atau saling terkait.

### Bergabung Sendiri ✍

Self join adalah regular join dimana sebuah tabel digabungkan dengan tabel itu sendiri.Ini berguna untuk membandingkan baris dalam tabel yang sama.

#### Contoh: Hirarki Karyawan

Pertimbangkan tabel `employees`:

|karyawan_id |nama |manajer_id |
|-------------|------------|------------|
|1 |Alice |BATAL |
|2 |Bob |1 |
|3 |Charlie |1 |
|4 |Daud |2 |

Untuk menemukan karyawan dan manajer mereka:

```sql
SELECT e1.name AS employee, e2.name AS manager
FROM employees e1
LEFT JOIN employees e2
ON e1.manager_id = e2.employee_id;
```

**Hasil:**

|karyawan |manajer |
|----------|---------|
|Alice |BATAL |
|Bob |Alice |
|Charlie |Alice |
|Daud |Bob |

### Gabung Luar Penuh 🌐

Gabungan luar penuh mengembalikan semua baris dari kedua tabel, dengan `NULL` di kolom yang tidak ada kecocokan.

#### Contoh: Mencocokkan Pelanggan dan Pesanan

Perhatikan tabel berikut:

**pelanggan**

|id_pelanggan |nama |
|-------------|---------|
|1 |Yohanes |
|2 |Sarah |
|3 |Michael |

**pesanan**

|nomor_pesanan |id_pelanggan |jumlah |
|----------|-------------|--------|
|101 |1 |100 |
|102 |4 |200 |

Untuk menemukan semua pelanggan dan pesanan mereka:

```sql
SELECT c.name, o.amount
FROM customers c
FULL OUTER JOIN orders o
ON c.customer_id = o.customer_id;
```

**Hasil:**

|nama |jumlah |
|---------|--------|
|Yohanes |100 |
|Sarah |BATAL |
|Michael |BATAL |
|BATAL |200 |

### Gabung Silang 🌱

Gabungan silang mengembalikan produk Cartesian dari dua tabel.Setiap baris pada tabel pertama digabungkan dengan setiap baris pada tabel kedua.

#### Contoh: Kombinasi Produk

**produk**

|id_produk |nama_produk |
|------------|--------------|
|1 |Pena |
|2 |Buku catatan |

**warna**

|warna_id |nama_warna |
|----------|------------|
|1 |Merah |
|2 |Biru |

Untuk menemukan semua kombinasi warna produk:

```sql
SELECT p.product_name, c.color_name
FROM products p
CROSS JOIN colors c;
```

**Hasil:**

|nama_produk |nama_warna |
|--------------|------------|
|Pena |Merah |
|Pena |Biru |
|Buku catatan |Merah |
|Buku catatan |Biru |

### Menggunakan Gabungan dengan Agregat 📊

Gabungan dapat digabungkan dengan fungsi agregat untuk meringkas data di beberapa tabel.

#### Contoh: Total Penjualan berdasarkan Pelanggan

**pesanan**

|nomor_pesanan |id_pelanggan |jumlah |
|----------|-------------|--------|
|101 |1 |100 |
|102 |1 |150 |
|103 |2 |200 |

**pelanggan**

|id_pelanggan |nama |
|-------------|---------|
|1 |Yohanes |
|2 |Sarah |

Untuk menghitung total penjualan berdasarkan pelanggan:

```sql
SELECT c.name, SUM(o.amount) AS total_sales
FROM customers c
JOIN orders o
ON c.customer_id = o.customer_id
GROUP BY c.name;
```

**Hasil:**

|nama |total_penjualan |
|-------|-------------|
|Yohanes |250 |
|Sarah |200 |

### Contoh Gabungan Tingkat Lanjut 🔄

#### Contoh 1: Menggabungkan Lebih dari Dua Tabel

```sql
SELECT o.order_id, c.name AS customer_name, p.product_name
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id
JOIN products p ON o.product_id = p.product_id;
```

#### Contoh 2: Gabungan Bersyarat

```sql
SELECT *
FROM orders o
LEFT JOIN customers c
ON o.customer_id = c.customer_id
AND c.name LIKE 'S%';
```

### Latihan Latihan 🔧

1. Tulis kueri menggunakan self join untuk menemukan pasangan karyawan yang berbagi manajer yang sama.
2. Gunakan gabungan luar penuh untuk mencantumkan semua produk dan pesanannya, termasuk produk tanpa pesanan.
3. Tulis kueri gabung silang untuk menghasilkan semua kemungkinan pasangan pelanggan dan wilayah dari tabel `customers` dan `regions`.
4. Gabungkan gabungan dengan agregat untuk menghitung jumlah pesanan rata-rata untuk setiap produk.
5. Tulis kueri yang menggabungkan tiga tabel untuk menemukan ringkasan pesanan terperinci (misalnya, nama pelanggan, nama produk, dan jumlah total).

### Ringkasan 🎯

Hari ini, Anda belajar tentang:

- **Self Joins**: Menggabungkan tabel dengan dirinya sendiri.
- **Full Outer Joins**: Mengembalikan semua baris dari kedua tabel.
- **Cross Joins**: Menghasilkan produk Cartesian.
- Menggabungkan gabungan dengan fungsi agregat.

Besok, kita akan membahas **Subkueri**.Nantikan keseruan SQL lainnya!🚀