# 📘 30 Hari SQL: Hari ke-24 - Impor dan Ekspor Data

Selamat datang di **Hari ke-24** dari tantangan **30 Hari SQL**! 🎉 Hari ini, kita akan fokus pada topik praktis dan penting dalam SQL: **Impor dan Ekspor Data**. Baik Anda memindahkan data antar sistem, membuat cadangan, atau memuat kumpulan data besar, menguasai teknik ini akan secara signifikan meningkatkan keterampilan manajemen basis data Anda.

## 🔍 Gambaran Umum

Impor dan ekspor data adalah proses penting untuk:

- **Migrasi Data**: Memindahkan data dari satu basis data ke basis data lain.
- **Integrasi Data**: Menggabungkan data dari berbagai sumber.
- **Cadangan**: Membuat salinan data Anda untuk tujuan pemulihan.
- **Analisis**: Mempersiapkan data untuk alat analisis eksternal.

---

## 📚 Pentingnya Impor dan Ekspor Data

Memahami cara mengimpor dan mengekspor data secara efektif memastikan:

- **Integritas Data**: Mencegah kehilangan atau kerusakan selama transfer.
- **Efisiensi**: Mengotomatiskan tugas-tugas berulang.
- **Kompatibilitas**: Menyesuaikan data untuk berbagai sistem dan format.

---

## 🔧 Alat dan Teknik

### 1. Mengimpor Data

#### Menggunakan Perintah SQL
- **MySQL**:
  ```sql
  LOAD DATA INFILE 'file_path.csv'
  INTO TABLE table_name
  FIELDS TERMINATED BY ','
  ENCLOSED BY '"'
  LINES TERMINATED BY '\n'
  IGNORE 1 ROWS;
  ```

- **PostgreSQL**:
  ```sql
  COPY table_name(column1, column2)
  FROM '/path/to/file.csv'
  DELIMITER ','
  CSV HEADER;
  ```

#### Menggunakan Alat GUI
Sebagian besar sistem manajemen basis data (misalnya, MySQL Workbench, pgAdmin) menyediakan antarmuka grafis untuk mengimpor data.

#### Menggunakan Alat Eksternal
- **Alat ETL**: Apache NiFi, Talend, Pentaho.

- **Alat Baris Perintah**: `mysqlimport`, `psql`.

### 2. Mengekspor Data

#### Menggunakan Perintah SQL
- **MySQL**:
  ```sql
  SELECT * FROM table_name
  INTO OUTFILE 'file_path.csv'
  FIELDS TERMINATED BY ','
  ENCLOSED BY '"'
  LINES TERMINATED BY '\n';
  ```

- **PostgreSQL**:
  ```sql
  COPY table_name(column1, column2)
  TO '/path/to/file.csv'
  DELIMITER ','
  CSV HEADER;
  ```

#### Menggunakan Alat GUI
Ekspor data melalui alat basis data bawaan atau perangkat lunak eksternal seperti DBeaver.

#### Menggunakan Alat Eksternal
- **Alat ETL** untuk alur kerja yang kompleks.

- **Alat Baris Perintah**: `mysqldump`, `pg_dump`.

---

## 📊 Format Data dan Contoh

### File CSV
CSV (Comma-Separated Values) adalah salah satu format yang paling umum untuk impor/ekspor data.

#### Contoh Impor (MySQL):
```sql
LOAD DATA INFILE 'data.csv'
INTO TABLE employees
FIELDS TERMINATED BY ','
LINES TERMINATED BY '\n'
IGNORE 1 ROWS;
```

#### Contoh Ekspor (PostgreSQL):
```sql
COPY employees TO '/path/to/employees.csv' DELIMITER ',' CSV HEADER;
```

### File JSON
JSON (JavaScript Object Notation) banyak digunakan untuk API dan aplikasi web.

#### Contoh Impor (MongoDB):
```bash
mongoimport --db database_name --collection collection_name --file data.json
```

#### Contoh Ekspor (MongoDB):
```bash
mongoexport --db database_name --collection collection_name --out data.json
```

### Dump SQL
SQL dumps are complete backups of a database or table, including schema and data.

#### Contoh Ekspor (MySQL):
```bash
mysqldump -u username -p database_name > backup.sql
```

#### Contoh Impor (PostgreSQL):
```bash
psql -U username -d database_name -f backup.sql
```

---

## ⚙ Praktik Terbaik

1. **Validasi Data**: Pastikan data sesuai dengan struktur tabel sebelum mengimpor.
2. **Cadangkan Sebelum Impor**: Selalu cadangkan basis data untuk menghindari penimpaan yang tidak disengaja.
3. **Gunakan Transaksi**: Bungkus impor dalam transaksi untuk penanganan kesalahan.
4. **Pantau Kinerja**: Optimalkan impor besar menggunakan pemrosesan batch.
5. **Amankan Data Sensitif**: Enkripsi file selama transfer dan pastikan kontrol akses yang tepat.

---

## 🎯 Tantangan Praktik Langsung

1. **Impor CSV**: Impor file `products.csv` ke dalam tabel basis data.
2. **Ekspor JSON**: Ekspor data karyawan ke dalam file JSON.
3. **Cadangkan dan Pulihkan**: Buat dump SQL dari basis data dan pulihkan ke basis data lain.

---

## 💻 Latihan - Hari ke-24

### ✅ Latihan: Level 1

1. Tulis kueri untuk mengimpor data penjualan dari file CSV.
2. Ekspor semua catatan pelanggan ke dalam file CSV.
3. Buat dump SQL dari tabel `inventory`.

### 🚀 Latihan: Level 2

1. Impor data JSON ke dalam koleksi MongoDB dan lakukan kueri.
2. Gunakan `mysqldump` untuk mencadangkan seluruh basis data dan memulihkannya ke lingkungan baru.
3. Otomatiskan impor data menggunakan skrip Python.

---

## 🖋 Ringkasan Hari ke-24

Hari ini, Anda telah mempelajari cara mengimpor dan mengekspor data di SQL, meliputi alat, teknik, dan format seperti CSV, JSON, dan dump SQL. Keterampilan ini sangat penting untuk migrasi data, pencadangan, dan integrasi.

Nantikan **Hari ke-25**, di mana kita akan menjelajahi **SQL untuk Analitik**! 🚀