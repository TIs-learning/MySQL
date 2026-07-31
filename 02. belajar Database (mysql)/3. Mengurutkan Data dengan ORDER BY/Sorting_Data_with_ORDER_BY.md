# Hari ke-4: Menyortir Data dengan ORDER BY 🎈

Hari ini, kita akan mempelajari klausa `ORDER BY`, yang digunakan untuk mengurutkan data dalam urutan menaik atau menurun.Penyortiran adalah aspek penting dalam pengambilan data yang membantu mengatur dan menganalisis data secara efektif.Mari kita mulai!🚀

### Apa yang dimaksud dengan Klausul ORDER BY?🏛

Klausa `ORDER BY` dalam SQL digunakan untuk mengurutkan baris yang dikembalikan oleh kueri berdasarkan satu atau lebih kolom.Secara default, data diurutkan dalam urutan menaik kecuali ditentukan lain.

### Sintaks Dasar ORDER BY 🔠

```sql
SELECT column1, column2, ...
FROM table_name
ORDER BY column_name [ASC|DESC];
```

- `column_name`: Kolom yang ingin Anda urutkan.
- `ASC`: Kata kunci opsional untuk mengurutkan dalam urutan menaik (default).
- `DESC`: Kata kunci untuk diurutkan dalam urutan menurun.

### Menyortir dalam Urutan Menaik 🔼

Urutan menaik (`ASC`) adalah urutan pengurutan default.Ini menyusun data dari yang terkecil hingga terbesar (untuk angka) atau berdasarkan abjad (untuk string).

#### Contoh:

Diberikan tabel `employees`:

|identitas |nama |usia |departemen |
|----|------------|-----|------------|
|1 |John Doe |30 |SDM |
|2 |Jane Smith |25 |itu |
|3 |Sam Coklat |35 |Pemasaran |

Untuk mengurutkan karyawan berdasarkan usia dalam urutan menaik:

```sql
SELECT *
FROM employees
ORDER BY age;
```

**Hasil:**

|identitas |nama |usia |departemen |
|----|------------|-----|------------|
|2 |Jane Smith |25 |itu |
|1 |John Doe |30 |SDM |
|3 |Sam Coklat |35 |Pemasaran |

### Menyortir dalam Urutan Menurun 🔽

Urutan menurun (`DESC`) menyusun data dari yang terbesar ke terkecil (untuk angka) atau terbalik berdasarkan abjad (untuk string).

#### Contoh:

Untuk mengurutkan karyawan berdasarkan usia dalam urutan menurun:

```sql
SELECT *
FROM employees
ORDER BY age DESC;
```

**Hasil:**

|identitas |nama |usia |departemen |
|----|------------|-----|------------|
|3 |Sam Coklat |35 |Pemasaran |
|1 |John Doe |30 |SDM |
|2 |Jane Smith |25 |itu |

### Menyortir berdasarkan Beberapa Kolom 🔄

Anda dapat mengurutkan berdasarkan beberapa kolom dengan menentukannya di klausa `ORDER BY`.Penyortiran diterapkan sesuai urutan kolom yang dicantumkan.

#### Contoh:

Untuk mengurutkan karyawan berdasarkan departemen dalam urutan menaik dan berdasarkan usia dalam urutan menurun:

```sql
SELECT *
FROM employees
ORDER BY department ASC, age DESC;
```

**Hasil:**

|identitas |nama |usia |departemen |
|----|------------|-----|------------|
|1 |John Doe |30 |SDM |
|3 |Sam Coklat |35 |Pemasaran |
|2 |Jane Smith |25 |itu |

### Latihan Latihan 🖋

1. Ambil semua baris dari tabel `employees` dan urutkan berdasarkan `name` dalam urutan menaik.
2. Urutkan tabel `employees` berdasarkan `department` dalam urutan menurun.
3. Gabungkan pengurutan berdasarkan `age` dalam urutan menaik dan `department` dalam urutan abjad.
4. Buat query untuk mengurutkan tabel baru `products` berdasarkan `price` dalam urutan menurun dan `stock_quantity` dalam urutan menaik.

### Ringkasan 🎯

Hari ini, Anda belajar:

- Cara menggunakan klausa `ORDER BY` untuk mengurutkan data.
- Mengurutkan data dalam urutan menaik (`ASC`) dan menurun (`DESC`).
- Menyortir berdasarkan beberapa kolom untuk pertanyaan kompleks.

Latihlah konsep-konsep ini untuk memperkuat pemahaman Anda.Besok, kita akan mendalami **fungsi agregat dan mengelompokkan data dengan GROUP BY**.Tetap penasaran!🚀
