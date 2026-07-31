# Hari 8: Bergabung – Dasar 🌟

Hari ini, kita akan menyelami dunia SQL Joins yang menakjubkan.Gabungan memungkinkan Anda menggabungkan data dari beberapa tabel menjadi wawasan yang bermakna.Mari kita mulai!✨

### Apa itu Gabungan?🔎

Gabungan adalah operasi SQL yang menggabungkan baris dari dua tabel atau lebih berdasarkan kolom terkait.Mereka membantu dalam:

- Mengakses data yang didistribusikan di beberapa tabel.
- Menciptakan hubungan yang bermakna antar entitas data.
- Menyederhanakan kueri untuk kumpulan data yang kompleks.

### Jenis Gabungan 🌐

|**Jenis Gabung** |**Deskripsi** |
|----------------------------------|-----------------------------------------------------------------------|
|**GABUNG DALAM** |Mengembalikan rekaman yang memiliki nilai yang cocok di kedua tabel.|
|**KIRI GABUNG** |Mengembalikan semua rekaman dari tabel kiri dan rekaman yang cocok dari tabel kanan.|
|**BENAR BERGABUNG** |Mengembalikan semua rekaman dari tabel kanan dan rekaman yang cocok dari tabel kiri.|
|**GABUNG LUAR LENGKAP** |Mengembalikan semua catatan ketika ada kecocokan di tabel kiri atau kanan.|

### Sintaks Gabungan 🔧

#### Sintaks INNER JOIN:

```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column_name = table2.column_name;
```

#### KIRI BERGABUNG Sintaks:

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column_name = table2.column_name;
```

#### Sintaks GABUNG KANAN:

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column_name = table2.column_name;
```

#### Sintaks FULL OUTER JOIN:

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column_name = table2.column_name;
```

### Contoh Gabungan 🔄

Anggaplah kita mempunyai dua tabel:

#### Tabel: `employees`

|karyawan_id |nama |departemen_id |
|-------------|------------|---------------|
|1 |John Doe |101 |
|2 |Jane Smith |102 |
|3 |Sam Coklat |103 |
|4 |Lisa Putih |BATAL |

#### Tabel: `departments`

|departemen_id |nama_departemen |
|---------------|-----------------|
|101 |SDM |
|102 |itu |
|103 |Pemasaran |
|104 |Keuangan |

#### Contoh 1: GABUNG DALAM

Untuk menemukan karyawan dan nama departemennya:

```sql
SELECT employees.name, departments.department_name
FROM employees
INNER JOIN departments
ON employees.department_id = departments.department_id;
```

**Hasil:**

|nama |nama_departemen |
|------------|-----------------|
|John Doe |SDM |
|Jane Smith |itu |
|Sam Coklat |Pemasaran |

#### Contoh 2: KIRI GABUNG

Untuk menyertakan semua karyawan, bahkan mereka yang tidak memiliki departemen:

```sql
SELECT employees.name, departments.department_name
FROM employees
LEFT JOIN departments
ON employees.department_id = departments.department_id;
```

**Hasil:**

|nama |nama_departemen |
|------------|-----------------|
|John Doe |SDM |
|Jane Smith |itu |
|Sam Coklat |Pemasaran |
|Lisa Putih |BATAL |

#### Contoh 3: GABUNG KANAN

Untuk memasukkan semua departemen, bahkan departemen tanpa karyawan:

```sql
SELECT employees.name, departments.department_name
FROM employees
RIGHT JOIN departments
ON employees.department_id = departments.department_id;
```

**Hasil:**

|nama |nama_departemen |
|------------|-----------------|
|John Doe |SDM |
|Jane Smith |itu |
|Sam Coklat |Pemasaran |
|BATAL |Keuangan |

#### Contoh 4: GABUNG LUAR LENGKAP

Untuk menyertakan semua karyawan dan semua departemen:

```sql
SELECT employees.name, departments.department_name
FROM employees
FULL OUTER JOIN departments
ON employees.department_id = departments.department_id;
```

**Hasil:**

|nama |nama_departemen |
|------------|-----------------|
|John Doe |SDM |
|Jane Smith |itu |
|Sam Coklat |Pemasaran |
|Lisa Putih |BATAL |
|BATAL |Keuangan |

### Latihan Latihan 🔧

1. Diberikan tabel `orders` dan tabel lainnya `customers`, temukan semua pesanan dengan nama pelanggannya menggunakan `INNER JOIN`.
2. Gunakan `LEFT JOIN` untuk mencantumkan semua produk dan pesanannya dari tabel `products` dan `orders`.
3. Buat query untuk mencari departemen tanpa ada karyawan menggunakan `RIGHT JOIN`.
4. Tulis kueri untuk menggabungkan dua tabel `authors` dan `books` untuk mencantumkan semua penulis dan buku yang mereka tulis menggunakan `FULL OUTER JOIN`.
5. Ubah contoh `employees` dan `departments` di atas untuk menyertakan kolom tambahan.

### Ringkasan 🏁

Hari ini, Anda belajar tentang:

- Tujuan SQL Gabungan dan tipenya.
- Menulis query menggunakan `INNER JOIN`, `LEFT JOIN`, `RIGHT JOIN`, dan `FULL OUTER JOIN`.
- Kasus penggunaan praktis dengan contoh dan latihan.

Besok, kita akan menjelajahi **Advanced Joins** untuk membangun fondasi hari ini.Tetap penasaran dan terus bertanya!🌐