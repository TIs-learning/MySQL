# Hari ke-3: Memfilter Data dengan Klausul WHERE 🌟

Hari ini, kita akan fokus pada pemfilteran data menggunakan klausa `WHERE`, salah satu alat paling penting untuk mengambil baris tertentu dari tabel database.🚀

### Apa yang dimaksud dengan Klausa WHERE?🔍

Klausa `WHERE` digunakan dalam SQL untuk memfilter rekaman yang memenuhi kriteria tertentu.Tanpanya, kueri SQL akan mengembalikan semua baris dalam tabel, yang mungkin tidak berguna untuk kumpulan data besar.

### Sintaks Dasar WHERE 🔧

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

- **`condition`**: Menentukan kriteria filter.Baris yang memenuhi ketentuan ini akan disertakan dalam hasil kueri.

#### Contoh:
Mengambil karyawan berusia 30 tahun ke atas:

```sql
SELECT *
FROM employees
WHERE age >= 30;
```

### Menggunakan WHERE dengan Operator Perbandingan ⚙

SQL menyediakan beberapa operator perbandingan untuk memfilter data:

|**Operator** |**Deskripsi** |
|--------------|----------------|
|`=` |Sama dengan |
|`<>` atau `!=` |Tidak sama dengan |
|`>` |Lebih besar dari |
|`<` |Kurang dari |
|`>=` |Lebih besar dari atau sama dengan |
|`<=` |Kurang dari atau sama dengan |

#### Contoh:
Ambil karyawan di departemen TI:

```sql
SELECT *
FROM employees
WHERE department = 'IT';
```

### Menggabungkan Kondisi dengan AND, OR, NOT ⚖

Anda dapat menggabungkan beberapa kondisi menggunakan operator logika:

- **`AND`**: Semua ketentuan harus benar.
- **`OR`**: Setidaknya satu kondisi harus benar.
- **`NOT`**: Meniadakan kondisi.

#### Contoh:
Mengambil karyawan berusia di atas 25 tahun di departemen SDM:

```sql
SELECT *
FROM employees
WHERE age > 25 AND department = 'HR';
```

Ambil karyawan yang berada di bidang TI atau Pemasaran:

```sql
SELECT *
FROM employees
WHERE department = 'IT' OR department = 'Marketing';
```

Mengambil karyawan yang tidak berada di departemen SDM:

```sql
SELECT *
FROM employees
WHERE NOT department = 'HR';
```

### Menggunakan WHERE dengan Pencocokan Pola (LIKE) 🔄

Operator `LIKE` digunakan untuk pencocokan pola dalam SQL.Ini mendukung dua wildcard:

- `%`: Cocok dengan nol karakter atau lebih.
- `_`: Cocok persis dengan satu karakter.

#### Contoh:
Ambil karyawan yang namanya dimulai dengan 'J':

```sql
SELECT *
FROM employees
WHERE name LIKE 'J%';
```

Ambil karyawan yang namanya mengandung 'Smith':

```sql
SELECT *
FROM employees
WHERE name LIKE '%Smith%';
```

### Memfilter Nilai NULL 🏠

Untuk memfilter baris dengan nilai `NULL`, gunakan operator `IS NULL` atau `IS NOT NULL`.

#### Contoh:
Mengambil karyawan tanpa departemen tertentu:

```sql
SELECT *
FROM employees
WHERE department IS NULL;
```

Mengambil karyawan dengan departemen tertentu:

```sql
SELECT *
FROM employees
WHERE department IS NOT NULL;
```

### Latihan Latihan 📘

1. Mengambil semua karyawan yang usianya kurang dari 30 tahun.
2. Temukan karyawan di departemen `Marketing` atau berusia 35 tahun ke atas.
3. Mengambil pegawai yang namanya diakhiri dengan huruf 'n'.
4. Daftar karyawan yang bukan anggota departemen `IT`.
5. Ambil karyawan dengan nilai non-NULL `age`.

### Ringkasan 🏁

Hari ini, Anda belajar tentang:

- Tujuan dan sintaksis klausa `WHERE`.
- Menggunakan operator perbandingan untuk memfilter.
- Menggabungkan kondisi dengan operator logika (`AND`, `OR`, `NOT`).
- Pencocokan pola dengan `LIKE`.
- Memfilter nilai `NULL`.

Besok, kita akan mempelajari **menyortir data dengan klausa ORDER BY**.Pantau terus!🚀
