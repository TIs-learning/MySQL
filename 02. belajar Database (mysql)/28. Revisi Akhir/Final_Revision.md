# 📘 30 Hari SQL: Hari ke-29 - Revisi Akhir

Selamat datang di **Hari ke-29** dari tantangan **30 Hari SQL**! 🎉 Hari ini adalah tentang revisi akhir, mengkonsolidasikan pembelajaran Anda, dan mempersiapkan diri untuk penilaian yang akan datang. Mari kita tinjau semua yang telah kita bahas dalam perjalanan ini dan pastikan Anda sepenuhnya siap untuk menerapkan SQL dalam skenario dunia nyata.

## 🔍 Gambaran Umum

Hari revisi sangat penting untuk memperkuat pengetahuan Anda, mengidentifikasi kekurangan, dan membangun kepercayaan diri sebelum penilaian akhir. Kita akan meninjau konsep-konsep kunci, memberikan kiat-kiat untuk peningkatan, dan menawarkan latihan untuk memperkuat keterampilan Anda.

---

## 🔄 Ringkasan Topik

### Hari 1 hingga 7: Dasar-Dasar SQL

- **Hari 1**: Pengantar SQL
- Perintah utama: `SELECT`, `FROM`
- Dasar-dasar definisi data: `CREATE`, `DROP`

- **Hari 2**: Pernyataan SELECT Dasar
- Menggunakan `DISTINCT`
- Perhitungan dasar dalam kueri

- **Hari 3**: Memfilter Data dengan WHERE
- Operator logika: `=`, `!=`, `LIKE`, `BETWEEN`

- **Hari 4**: Mengurutkan Data dengan ORDER BY
- Pengurutan dalam urutan naik (`ASC`) dan turun (`DESC`)

- **Hari 5**: Fungsi Agregat dan GROUP BY
- Fungsi: `SUM`, `AVG`, `COUNT`, `MIN`, `MAX`

- **Hari ke-6**: Klausa HAVING
- Memfilter data yang dikelompokkan

- **Hari ke-7**: Latihan dan Kuis

### Hari ke-8 hingga ke-14: Topik Menengah

- **Hari ke-8**: Gabungan (Dasar)

- Jenis: `INNER`, `LEFT`, `RIGHT`, `FULL OUTER`

- **Hari ke-9**: Gabungan Tingkat Lanjut
- Gabungan sendiri dan gabungan silang

- **Hari ke-10**: Subkueri
- Subkueri berkorelasi vs tidak berkorelasi

- **Hari ke-11**: Operasi Himpunan
- Perintah: `UNION`, `INTERSECT`, `EXCEPT`

- **Hari ke-12**: Fungsi String
- Fungsi umum: `CONCAT`, `SUBSTRING`, `LENGTH`

- **Hari ke-13**: Tanggal dan Waktu Fungsi
- Fungsi: `NOW`, `DATEADD`, `DATEDIFF`

- **Hari ke-14**: Latihan dan Kuis Tingkat Menengah

### Hari ke-15 hingga 21: Konsep SQL Tingkat Lanjut

- **Hari ke-15**: Fungsi Agregat Tingkat Lanjut
- Fungsi: `MEDIAN`, `PERCENTILE_CONT`, `ROLLUP`, `CUBE`

- **Hari ke-16**: Fungsi Jendela
- Perintah: `ROW_NUMBER`, `RANK`, `NTILE`

- **Hari ke-17**: Ekspresi Tabel Umum (CTE)

- CTE rekursif dan non-rekursif

- **Hari ke-18**: Indeks dan Optimasi Kueri
- Jenis indeks: clustered, non-clustered

- **Hari ke-19**: Transaksi dan Kontrol Konkurensi
- Perintah: `BEGIN`, `COMMIT`, `ROLLBACK`, `SAVEPOINT`

- **Hari ke-20**: Latihan Lanjutan dan Kuis

- **Hari ke-21**: Pemodelan dan Normalisasi Data
- Bentuk normal (1NF, 2NF, 3NF)

### Hari ke-22 hingga 28: Aplikasi Dunia Nyata

- **Hari ke-22**: Prosedur dan Fungsi Tersimpan
- Sintaks untuk `CREATE PROCEDURE` dan `CREATE FUNCTION`

- **Hari ke-23**: Pemicu dan Peristiwa
- Perintah: `CREATE TRIGGER`, `AFTER INSERT`

- **Hari ke-24**: Impor dan Ekspor Data
- Alat: `LOAD DATA`, `COPY`

- **Hari ke-25**: SQL untuk Analisis
- Fungsi analitik: `LEAD`, `LAG`

- **Hari ke-26**: Penanganan Kesalahan dan Debugging
- Menggunakan `TRY...CATCH`

- **Hari ke-27**: Keamanan SQL
- Izin: `GRANT`, `REVOKE`

- **Hari ke-28**: Membangun Proyek Dunia Nyata
- Langkah-langkah: definisi masalah, pemodelan data, implementasi kueri

---

## 🔧 Praktik Langsung

1. Tinjau kembali semua kueri dan perintah yang dipelajari selama tantangan.

2. Berlatih membuat skema basis data dengan tabel yang dinormalisasi.

3. Kerjakan join, subkueri, dan fungsi jendela yang kompleks.

4. Debug kueri dan optimalkan kinerjanya.

5. Kunjungi kembali proyek dunia nyata dari Hari ke-28 dan perbaiki lebih lanjut.

---

## 🕵 Tips untuk Penilaian Akhir

1. **Pahami Pertanyaan**: Baca pernyataan masalah dengan saksama.

2. **Rencanakan Kueri**: Uraikan masalah menjadi bagian-bagian yang lebih kecil.

3. **Optimalkan Kueri**: Tulis kueri yang efisien dan mudah dibaca.

4. **Berlatih dalam Kondisi Berwaktu**: Simulasikan lingkungan penilaian.

5. **Periksa Kesalahan**: Verifikasi kesalahan sintaks dan logika sebelum eksekusi.

---

## 🖋 Daftar Periksa Revisi

- [ ] Dapatkah Anda membuat dan memanipulasi tabel secara efektif?

- [ ] Apakah Anda memahami semua jenis join?

- [ ] Apakah Anda nyaman dengan subkueri dan operasi set?

- [ ] Apakah Anda telah menguasai fungsi agregat dan window?

- [ ] Apakah Anda tahu cara menangani transaksi dan masalah konkurensi?

- [ ] Dapatkah Anda menulis dan men-debug stored procedure dan trigger?

- [ ] Apakah Anda yakin dengan teknik optimasi kueri?

---

## 🔬 Latihan Praktik

### Latihan 1: Desain Basis Data

Rancang skema basis data untuk sistem manajemen perpustakaan:
- **Tabel**: Buku, Anggota, Peminjaman
- **Relasi**: Satu-ke-banyak antara Anggota dan Peminjaman, satu-ke-banyak antara Buku dan Peminjaman

### Latihan 2: Kueri Tingkat Lanjut

Tulis kueri untuk menghitung:
- Jumlah total buku yang dipinjam oleh setiap anggota
- Anggota dengan jumlah peminjaman tertinggi

### Latihan 3: Debugging

Optimalkan kueri berikut:
```sql
SELECT *
FROM orders
WHERE order_date > '2023-01-01'
  AND customer_id IN (
      SELECT customer_id
      FROM customers
      WHERE region = 'North'
  );
```

### Latihan 4: Prosedur Tersimpan

Buat prosedur tersimpan untuk:
- Menghitung total penjualan untuk wilayah tertentu
- Mengembalikan hasilnya sebagai parameter keluaran

---

## 📊 Ringkasan Hari ke-29

Hari ini, kita telah mengkonsolidasikan pembelajaran dan mempersiapkan diri untuk penilaian akhir. Mengulas kembali konsep-konsep kunci, berlatih kueri, dan melakukan debugging sangat penting untuk keberhasilan. Pada **Hari ke-30**, Anda akan menunjukkan semua yang telah Anda pelajari dalam penilaian akhir yang komprehensif. Bersiaplah untuk bersinar! 🌟