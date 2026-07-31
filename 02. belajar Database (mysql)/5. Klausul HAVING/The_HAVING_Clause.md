# Hari 6: Klausul HAVING 🎉

Hari ini, kita akan menjelajahi klausa `HAVING`—alat penting untuk memfilter data yang dikelompokkan dalam SQL.Mari selami sintaksis dan penerapan praktisnya.🚀

### Apa yang dimaksud dengan Klausul HAVING?🔍

Klausa `HAVING` digunakan untuk memfilter hasil grup yang dibuat oleh klausa `GROUP BY`.Berbeda dengan klausa `WHERE`, yang memfilter baris sebelum pengelompokan, `HAVING` memfilter grup setelah agregasi.

### Sintaks HAVING 🔧

```sql
SELECT column1, column2, aggregate_function(column3)
FROM table_name
GROUP BY column1, column2
HAVING condition;
```

- **`column1, column2`**: Kolom yang digunakan untuk pengelompokan.
- **`aggregate_function(column3)`**: Fungsi agregat seperti `SUM`, `AVG`, `COUNT`, dll.
- **`condition`**: Kondisi untuk memfilter data yang dikelompokkan.

### Perbedaan Antara WHERE dan HAVING ⚙

|**Aspek** |**Klausul MANA** |**MEMILIKI Klausa** |
|------------------|----------------------------------------------------------------|------------------------------------------------|
|**Tujuan** |Filter baris sebelum mengelompokkan.|Filter grup setelah agregasi.|
|**Penggunaan** |Tidak dapat menggunakan fungsi agregat secara langsung.|Bekerja dengan fungsi agregat.|
|**Contoh** |`WHERE age > 30` |`HAVING COUNT(*) > 5` |

### Contoh MEMILIKI 🎓

#### Contoh 1: Penggunaan Dasar HAVING

Misalkan kita memiliki tabel bernama `sales`:

|penjual |wilayah |jumlah_penjualan |
|-------------|------------|--------------|
|Alice |Utara |5000 |
|Bob |Selatan |7000 |
|Alice |Utara |3000 |
|Bob |Selatan |2000 |
|Karol |Timur |8000 |

Untuk menemukan wilayah dengan total penjualan lebih dari 10.000:

```sql
SELECT region, SUM(sales_amount) AS total_sales
FROM sales
GROUP BY region
HAVING total_sales > 10000;
```

**Hasil:**

Karena tidak ada wilayah yang memiliki total penjualan lebih dari 10.000, kueri mengembalikan **tidak ada baris**.

#### Contoh 2: Menggunakan Beberapa Kondisi

Untuk menemukan tenaga penjualan yang telah melakukan lebih dari 1 penjualan dan total penjualannya melebihi 6.000:

```sql
SELECT salesperson, COUNT(*) AS sales_count, SUM(sales_amount) AS total_sales
FROM sales
GROUP BY salesperson
HAVING sales_count > 1 AND total_sales > 6000;
```

**Hasil:**

|penjual |jumlah_penjualan |total_penjualan |
|-------------|-------------|-------------|
|Alice |2 |8000 |

#### Contoh 3: Menggabungkan HAVING dengan Agregat Lain

Untuk menemukan wilayah yang rata-rata jumlah penjualannya lebih besar dari 4000:

```sql
SELECT region, AVG(sales_amount) AS average_sales
FROM sales
GROUP BY region
HAVING average_sales > 4000;
```

**Hasil:**

|wilayah |rata-rata_penjualan |
|--------|---------------|
|Utara |4000 |
|Selatan |6000 |
|Timur |8000 |

#### Contoh 4: Menggunakan HAVING dengan COUNT

Misalkan ada tabel `students`:

|kelas |nama_siswa |skor |
|--------|--------------|-------|
|SEBUAH |Yohanes |85 |
|SEBUAH |Maria |90 |
|B |jake |70 |
|B |Emily |75 |
|SEBUAH |Steve |95 |

Untuk menemukan kelas dengan lebih dari 2 siswa:

```sql
SELECT class, COUNT(student_name) AS student_count
FROM students
GROUP BY class
HAVING student_count > 2;
```

**Hasil:**

|kelas |jumlah_siswa |
|-------|---------------|
|SEBUAH |3 |

### Latihan Latihan 🔧

1. Diberikan tabel `orders` dengan kolom `customer_id`, `order_date`, dan `order_total`, tulis kueri untuk menemukan pelanggan yang total nilai pesanannya melebihi $5000.
2. Gunakan klausa `HAVING` untuk memfilter produk dari tabel `products` yang harga rata-ratanya lebih besar dari $50.
3. Ubah contoh di atas untuk menyertakan kondisi tambahan atau fungsi agregat.
4. Buat kueri untuk tabel `library` untuk menemukan penulis yang memiliki lebih dari 3 buku terbitan dan nilai rata-rata di atas 4,5.
5. Tulis query untuk menemukan departemen dalam tabel `company` yang total gaji karyawannya melebihi $100.000.

### Ringkasan 🏁

Hari ini, Anda belajar tentang:

- Tujuan klausa `HAVING` dan perbedaannya dengan `WHERE`.
- Menulis kueri dengan `HAVING` untuk memfilter data gabungan.
- Kasus penggunaan praktis dengan banyak contoh dan latihan.

Besok, kami akan menguji pengetahuan Anda dengan **Hari Latihan dan Kuis**!Bersiaplah untuk mengkonsolidasikan pembelajaran Anda sejauh ini.🌟