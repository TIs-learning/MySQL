# 📘 30 Hari SQL: Hari ke-21 - Pemodelan dan Normalisasi Data

Selamat datang di **Hari ke-21** dari tantangan **30 Hari SQL**! 🎉 Hari ini, kita akan fokus pada **pemodelan data** dan **normalisasi**, teknik penting untuk mendesain basis data yang efisien dan terukur. Memahami konsep-konsep ini memastikan fondasi yang kuat untuk integritas, kinerja, dan fleksibilitas basis data.

## 🔍 Gambaran Umum

Pemodelan dan normalisasi data sangat penting untuk:

- Mendesain skema basis data yang logis dan efisien.
- Meminimalkan redundansi dan mencegah anomali.
- Meningkatkan konsistensi dan integritas data.
- Mengoptimalkan kinerja dan skalabilitas basis data.

---

## 📈 Dasar-Dasar Pemodelan Data

Pemodelan data adalah proses mendefinisikan dan mengatur struktur basis data. Proses ini melibatkan tiga tahap utama:

### 1. Model Konseptual

- **Tujuan**: Merepresentasikan struktur keseluruhan basis data pada tingkat tinggi, berfokus pada entitas dan relasi.
- **Komponen**: Entitas, atribut, relasi.
- **Alat**: Diagram Entitas-Relasi (ERD).

Contoh:

```
Pelanggan (CustomerID, Nama, Email)
Pesanan (OrderID, Tanggal, Jumlah, CustomerID)
Relasi: Satu Pelanggan melakukan banyak Pesanan.

```

### 2. Model Logis

- **Tujuan**: Menerjemahkan model konseptual ke dalam struktur yang lebih detail, mendefinisikan tabel, kolom, tipe data, dan batasan.
- **Komponen**: Tabel, kolom, kunci utama dan kunci asing.

Example:
```sql
CREATE TABLE Customers (
    CustomerID INT PRIMARY KEY,
    Name VARCHAR(100),
    Email VARCHAR(100) UNIQUE
);

CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    Date DATE,
    Amount DECIMAL(10, 2),
    CustomerID INT,
    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);
```

### 3. Model Fisik

- **Tujuan**: Berfokus pada implementasi model logis pada sistem manajemen basis data (DBMS) tertentu.
- **Pertimbangan**: Pengindeksan, partisi, dan optimasi kinerja.

Contoh:
```sql
CREATE INDEX idx_customer_email ON Customers (Email);
```

---

## 🔄 Prinsip Normalisasi

Normalisasi mengatur data ke dalam tabel untuk meminimalkan redundansi dan meningkatkan integritas data. Berikut adalah bentuk normal utama:

### 1. Bentuk Normal Pertama (1NF)

- **Definisi**: Memastikan semua kolom berisi nilai atomik (tidak dapat dibagi).
- **Aturan**:
- Setiap kolom hanya boleh berisi satu nilai.
- Setiap baris harus unik.

**Contoh**:

Tabel Non-1NF:
| CustomerID | Name | PhoneNumbers |
|------------|-----------|--------------------|
| 1 | Alice | 123-456, 987-654 |
Tabel 1NF:
| CustomerID | Name | PhoneNumber |
|------------|-----------|-------------|
| 1 | Alice | 123-456 |
| 1 | Alice | 987-654 |

### 2. Bentuk Normal Kedua (2NF)

- **Definisi**: Memastikan tidak ada ketergantungan parsial (yaitu, tidak ada atribut yang hanya bergantung pada sebagian dari kunci utama komposit).
- **Prasyarat**: Harus memenuhi 1NF.

**Contoh**:

Tabel Non-2NF:
| OrderID | ProductID | ProductName | Quantity |
|---------|-----------|-------------|----------|
| 101 | 1 | Laptop | 2 |
Tabel 2NF:
| OrderID | ProductID | Quantity |
|---------|-----------|----------|
| 101 | 1 | 2 |
| ID Produk | Nama Produk |
|-----------|-------------|
| 1 | Laptop |

### 3. Bentuk Normal Ketiga (3NF)

- **Definisi**: Menghilangkan ketergantungan transitif (yaitu, tidak ada atribut non-kunci yang bergantung pada atribut non-kunci lainnya).
- **Prasyarat**: Harus memenuhi 2NF.

**Contoh**:

Tabel Non-3NF:

| ID Pelanggan | Nama | Kota | Negara Bagian |
|------------|-------|-----------|-------|
| 1 | Alice | New York | NY |

Tabel 3NF:
| ID Pelanggan | Nama | ID Kota |
|------------|-------|--------|
| 1 | Alice | 101 |
| ID Kota | Kota | Negara Bagian |
|--------|-----------|-------|
| 101 | New York | NY |

### 4. Bentuk Normal Boyce-Codd (BCNF)

- **Definisi**: Memastikan setiap determinan adalah kunci kandidat.
- **Prasyarat**: Harus memenuhi 3NF.

**Contoh**:

Tabel Non-BCNF:
| StudentID | CourseID | Instructor |
|-----------|----------|------------|
| 1 | Math101 | Dr. Smith |
| 2 | Math101 | Dr. Smith |

Tabel BCNF:
| CourseID | Instructor |
|----------|------------|
| Math101 | Dr. Smith |
| StudentID | CourseID |
|-----------|----------|
| 1 | Matematika 101 |
| 2 | Matematika 101 |

---

## 🔧 Praktik Terbaik

1. **Rencanakan Terlebih Dahulu**: Investasikan waktu untuk membuat model konseptual yang kuat.
2. **Normalisasi ke Tingkat yang Tepat**: Normalisasi yang berlebihan dapat memengaruhi kinerja.
3. **Dokumentasikan Model Anda**: Gunakan alat seperti ERD untuk komunikasi yang jelas.
4. **Pantau Kinerja**: Gunakan indeks dan optimalkan kueri bila perlu.

---

## 🎨 Tantangan Praktik Langsung

1. **Model Konseptual**: Rancang ERD untuk platform e-commerce dengan Pelanggan, Produk, Pesanan, dan Ulasan.
2. **Model Logis**: Tulis skrip SQL untuk membuat tabel yang dinormalisasi untuk skenario di atas.
3. **Normalisasi**: Normalisasikan tabel berikut ke 3NF:

| OrderID | CustomerName | ProductName | City |
|---------|--------------|-------------|-----------|
| 101 | Alice | Laptop | New York |
| 102 | Bob | Tablet | San Diego |

---

## 💻 Latihan - Hari ke-21

### ✅ Latihan: Level 1

1. Normalisasikan tabel berikut ke 1NF:

| EmployeeID | Name | Departments |
|------------|------------|---------------------|
| 1 | John Smith | HR, Finance |

2. Buat ERD untuk basis data perpustakaan dengan Buku, Penulis, Anggota, dan Peminjaman.

### 🚀 Latihan: Level 2

1. Tulis skrip SQL untuk membuat tabel untuk basis data perpustakaan dalam bentuk normal ketiga (3NF).
2. Rancang model fisik untuk mengoptimalkan kinerja kueri untuk pencarian buku.

---

## 🖋 Ringkasan Hari ke-21

Hari ini, Anda telah mempelajari tentang **pemodelan data** dan **normalisasi**, teknik kunci untuk merancang basis data yang efisien dan terukur. Praktikkan prinsip-prinsip ini untuk membangun basis data yang tangguh dan berkinerja tinggi.

Nantikan **Hari ke-22**, di mana kita akan membahas **Prosedur Tersimpan dan Fungsi**! 🚀
