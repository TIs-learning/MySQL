# Hari 5: Fungsi Agregat dan GROUP BY 🎉

Hari ini, kita akan mempelajari **fungsi agregat** dan cara menggunakan klausa **GROUP BY** untuk meringkas data.Ayo selami!🚀

### Apa itu Fungsi Agregat?📊

Fungsi agregat digunakan untuk melakukan penghitungan pada sekumpulan nilai, dan menghasilkan nilai tunggal.Fungsi-fungsi ini biasanya digunakan untuk meringkas data dalam SQL.

### Fungsi Agregat Umum 🛠

|**Fungsi** |**Deskripsi** |**Contoh** |
|----------------|-----------------------------|----------------------------------|
|`COUNT()` |Menghitung jumlah baris.|`COUNT(*)` |
|`SUM()` |Menghitung jumlah total kolom.|`SUM(salary)` |
|`AVG()` |Menghitung nilai rata-rata kolom.|`AVG(salary)` |
|`MIN()` |Mengembalikan nilai terkecil dalam kolom.|`MIN(age)` |
|`MAX()` |Mengembalikan nilai terbesar dalam kolom.|`MAX(age)` |

Contoh:

```sql
SELECT COUNT(*) AS total_employees,
       AVG(salary) AS average_salary
FROM employees;
```

### Menggunakan GROUP BY 🧑‍🤝‍🧑

Klausa `GROUP BY` digunakan untuk mengelompokkan baris yang memiliki nilai yang sama pada kolom tertentu.Ini sering digunakan dengan fungsi agregat untuk mengelompokkan hasil berdasarkan satu atau lebih kolom.

#### Sintaks 🛠️

```sql
SELECT column1, aggregate_function(column2)
FROM table_name
GROUP BY column1;
```

#### Contoh:

Bayangkan tabel `employees` berikut:

|identitas |nama |departemen |gaji |
|----|------------|------------|--------|
|1 |John Doe |SDM |50000 |
|2 |Jane Smith |itu |60000 |
|3 |Sam Coklat |SDM |55000 |
|4 |Lisa Wong |itu |70000 |
|5 |Tandai Lee |Pemasaran |45000 |

Untuk menghitung total gaji setiap departemen:

```sql
SELECT department, SUM(salary) AS total_salary
FROM employees
GROUP BY department;
```

Hasil:

|departemen |total_gaji |
|------------|--------------|
|SDM |105000 |
|itu |130000 |
|Pemasaran |45000 |

### Menggabungkan GROUP BY dengan Fungsi Agregat 🤝

Anda dapat menggunakan beberapa fungsi agregat dengan klausa `GROUP BY`.Misalnya:

```sql
SELECT department,
       COUNT(*) AS total_employees,
       AVG(salary) AS average_salary,
       MAX(salary) AS highest_salary
FROM employees
GROUP BY department;
```

### Latihan Latihan 📝

1. Tulis query untuk mencari jumlah total siswa di setiap mata pelajaran dari tabel `students`.
2. Hitung rata-rata gaji karyawan di setiap departemen dari tabel `employees`.
3. Temukan harga minimum dan maksimum produk di setiap kategori dari tabel `products`.
4. Hitung jumlah pesanan yang dilakukan oleh setiap pelanggan dari tabel `orders`.

### Ringkasan 🏁

Hari ini, Anda belajar:

- Apa fungsi agregat dan bagaimana menggunakannya.
- Tujuan dan sintaksis klausa `GROUP BY`.
- Cara menggabungkan `GROUP BY` dengan fungsi agregat untuk meringkas data.

Besok, kita akan mempelajari **klausa HAVING** untuk memfilter data yang dikelompokkan.Pantau terus!🌟
