# 📘 30 Hari SQL: Hari ke-22 - Prosedur dan Fungsi Tersimpan

Hari ini, kita akan fokus pada prosedur dan fungsi tersimpan, yang merupakan alat penting untuk merangkum logika SQL yang dapat digunakan kembali. Fitur-fitur ini memungkinkan Anda untuk memodularisasi kode Anda, meningkatkan kinerja, dan menegakkan aturan bisnis dalam basis data Anda.

## 🔍 Gambaran Umum

Prosedur dan fungsi tersimpan memungkinkan Anda untuk mengelompokkan pernyataan SQL ke dalam blok kode yang dapat digunakan kembali. Mereka dapat menerima parameter input, mengeksekusi logika kompleks, dan mengembalikan hasil—menjadikannya sangat diperlukan untuk menciptakan sistem basis data yang tangguh, efisien, dan mudah dipelihara.

---

## 📚 Konsep Utama

### 1. Apa Itu Prosedur Tersimpan?

Prosedur tersimpan adalah rutin SQL yang telah dikompilasi sebelumnya yang dapat melakukan serangkaian operasi. Mereka umumnya digunakan untuk:

- Merangkum logika bisnis.

- Mengurangi lalu lintas jaringan dengan menjalankan beberapa pernyataan dalam satu eksekusi.

- Meningkatkan keamanan dengan mengontrol akses ke data yang mendasarinya.

**Syntax (General):**
```sql
CREATE PROCEDURE procedure_name (
    IN param1 DataType,
    OUT param2 DataType
)
BEGIN
    -- SQL statements
END;
```

### 2. Apa Itu Fungsi?

Fungsi mirip dengan stored procedure tetapi dirancang untuk mengembalikan satu nilai. Fungsi biasanya digunakan untuk:

- Perhitungan atau transformasi.

- Dapat digunakan kembali dalam klausa SELECT atau WHERE.

- Menegakkan logika yang konsisten.

**Sintaks (Umum):**
```sql
CREATE FUNCTION function_name (
    param1 DataType,
    param2 DataType
) RETURNS ReturnType
BEGIN
    -- SQL statements
    RETURN value;
END;
```

---

## 📊 Contoh Praktis

### 1. Membuat Prosedur Tersimpan

Misalkan kita ingin membuat prosedur untuk memperbarui gaji karyawan dengan persentase tertentu:

```sql
DELIMITER //
CREATE PROCEDURE UpdateSalaries (
    IN department_id INT,
    IN percentage DECIMAL(5, 2)
)
BEGIN
    UPDATE employees
    SET salary = salary + (salary * percentage / 100)
    WHERE dept_id = department_id;
END //
DELIMITER ;
```

**Usage:**
```sql
CALL UpdateSalaries(5, 10.0); -- Increase salaries by 10% for department 5
```

### 2. Membuat Fungsi

Mari kita buat fungsi untuk menghitung bonus tahunan karyawan berdasarkan gaji mereka:

```sql
DELIMITER //
CREATE FUNCTION CalculateBonus (
    base_salary DECIMAL(10, 2),
    bonus_percentage DECIMAL(5, 2)
) RETURNS DECIMAL(10, 2)
BEGIN
    RETURN base_salary * bonus_percentage / 100;
END //
DELIMITER ;
```

**Usage:**
```sql
SELECT CalculateBonus(salary, 15.0) AS annual_bonus FROM employees;
```

---

## 🔧 Praktik Terbaik

1. **Gunakan Nama yang Deskriptif**: Tunjukkan dengan jelas tujuan prosedur atau fungsi tersebut.
2. **Batasi Kompleksitas**: Jaga agar logika tetap sederhana dan modular.
3. **Dokumentasikan Parameter**: Berikan komentar yang menjelaskan parameter input dan output.
4. **Penanganan Kesalahan**: Sertakan pemeriksaan kesalahan untuk menangani input atau status basis data yang tidak terduga.

5. **Uji Secara Menyeluruh**: Validasi dengan berbagai kasus ekstrem untuk memastikan keandalan.

---

## 🔢 Tantangan Praktik Langsung

1. Tulis prosedur tersimpan untuk mengarsipkan pesanan lama berdasarkan tanggal batas.
2. Buat fungsi untuk menghitung total nilai pesanan, termasuk pajak, untuk ID pesanan tertentu.
3. Rancang prosedur untuk mencatat perubahan pada tabel tertentu dalam log audit.

---

## 💻 Latihan - Hari ke-22

### ✅ Latihan: Level 1

1. Tulis prosedur tersimpan untuk meningkatkan stok suatu produk dengan jumlah tertentu.
2. Buat fungsi untuk menghitung kuadrat suatu angka.
3. Tulis prosedur untuk mengambil dan mencetak detail karyawan untuk ID departemen tertentu.

### 🚀 Latihan: Level 2

1. Buat fungsi untuk menghitung bunga majemuk untuk pokok, suku bunga, dan waktu tertentu.
2. Tulis prosedur tersimpan untuk mencadangkan baris dari satu tabel ke tabel lain sebelum menghapusnya.
3. Rancang fungsi untuk mengembalikan nama lengkap karyawan dengan menggabungkan nama depan dan nama belakang mereka.

---

## 🖋 Ringkasan Hari ke-22

Hari ini, Anda telah mempelajari cara:

- Mendefinisikan dan menggunakan prosedur tersimpan untuk merangkum logika SQL.
- Membuat dan menggunakan fungsi untuk komputasi yang dapat digunakan kembali.
- Ikuti praktik terbaik untuk memastikan kode basis data yang mudah dipelihara dan efisien.

Prosedur tersimpan dan fungsi adalah alat yang ampuh untuk mengoptimalkan alur kerja SQL. Selanjutnya: **Hari ke-23 - Pemicu dan Peristiwa**! 🚀