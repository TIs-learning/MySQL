# Hari 10: Subkueri dalam SQL 🎉

Hari ini, kita akan mendalami **subkueri** — cara ampuh untuk menyatukan satu kueri ke dalam kueri lainnya.Subkueri sangat penting untuk menulis kueri SQL tingkat lanjut dan efisien.Mari jelajahi sintaksis, tipe, dan kasus penggunaannya.🚀

### Apa itu Subkueri?🔎

**Subkueri** adalah kueri yang disarangkan di dalam kueri SQL lain.Subkueri dapat:

- Digunakan dalam klausa `SELECT`, `FROM`, atau `WHERE`.
- Memberikan hasil antara untuk kueri utama.
- Membuat pertanyaan kompleks lebih mudah dibaca dan dipelihara.

### Jenis Subkueri ⚖️

Subkueri dikategorikan berdasarkan penggunaan dan keluarannya:

1. **Subkueri Baris Tunggal:** Mengembalikan satu baris dengan satu kolom.
2. **Subkueri Multi-Baris:** Mengembalikan beberapa baris dengan satu kolom.
3. **Subkueri Multi-Kolom:** Mengembalikan beberapa baris dengan beberapa kolom.
4. **Subkueri Berkorelasi:** Bergantung pada kueri luar untuk eksekusinya.
5. **Subkueri Tidak Berkorelasi:** Jalankan secara independen dari kueri luar.

### Sintaks Subkueri 🔧

```sql
SELECT column1, column2
FROM table_name
WHERE column3 = (SELECT aggregate_function(column4) FROM table_name WHERE condition);
```

### Poin Penting:

- Subkueri diapit tanda kurung `()`.
- Mereka dapat menggunakan fungsi agregat seperti `SUM`, `COUNT`, `AVG`.
- Penempatannya bergantung pada klausa (misalnya, `SELECT`, `FROM`, atau `WHERE`).

### Contoh Subkueri 🔄

#### Contoh 1: Subquery pada Klausul WHERE

Temukan karyawan yang berpenghasilan lebih dari gaji rata-rata:

```sql
SELECT employee_name, salary
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

**Hasil:**

|nama_karyawan |gaji |
|---------------|--------|
|Yohanes |75000 |
|Sarah |80000 |

#### Contoh 2: Subquery pada Klausa SELECT

Temukan gaji setiap karyawan dan gaji rata-rata di departemennya:

```sql
SELECT employee_name, salary,
       (SELECT AVG(salary)
        FROM employees e2
        WHERE e1.department_id = e2.department_id) AS avg_department_salary
FROM employees e1;
```

**Hasil:**

|nama_karyawan |gaji |gaji_rata-rata_departemen |
|---------------|--------|-----------------------|
|Yohanes |75000 |70000 |
|Sarah |80000 |70000 |

#### Contoh 3: Subquery pada Klausa FROM

Temukan departemen dengan total gaji tertinggi:

```sql
SELECT department_name, total_salary
FROM (SELECT department_id, SUM(salary) AS total_salary
      FROM employees
      GROUP BY department_id) AS department_totals
WHERE total_salary = (SELECT MAX(total_salary)
                      FROM (SELECT department_id, SUM(salary) AS total_salary
                            FROM employees
                            GROUP BY department_id) AS department_totals);
```

**Hasil:**

|nama_departemen |total_gaji |
|-----------------|--------------|
|itu |250000 |

#### Contoh 4: Subquery Berkorelasi

Temukan karyawan yang gajinya di atas gaji rata-rata departemennya:

```sql
SELECT employee_name, salary
FROM employees e1
WHERE salary > (SELECT AVG(salary)
                FROM employees e2
                WHERE e1.department_id = e2.department_id);
```

**Hasil:**

|nama_karyawan |gaji |
|---------------|--------|
|Yohanes |75000 |
|Sarah |80000 |

### Subkueri vs. Gabungan ⚖️

|**Aspek** |**Subkueri** |**Bergabung** |
|-----------------------------------|---------------------------------------------|---------------------------------------|
|**Penggunaan** |Tempatkan satu kueri di dalam kueri lainnya.|Gabungkan data dari beberapa tabel.|
|**Kinerja** |Mungkin lebih lambat untuk kumpulan data besar.|Seringkali lebih cepat dengan pengindeksan yang tepat.|
|**Keterbacaan** |Lebih mudah untuk logika yang kompleks.|Lebih jelas untuk hubungan tabel langsung.|

### Latihan Latihan 🎓

1. Tulis kueri untuk menemukan karyawan dengan bayaran tertinggi di setiap departemen menggunakan subkueri.
2. Gunakan subkueri untuk mengidentifikasi pelanggan yang melakukan pemesanan lebih banyak daripada jumlah rata-rata pesanan.
3. Temukan nama dan gaji karyawan yang gajinya lebih besar dari gaji rata-rata departemen tersebut.
4. Buat query untuk menentukan produk mana yang memiliki harga lebih tinggi dari harga rata-rata produk.
5. Tulis query untuk menemukan semua pesanan dengan nilai total lebih besar dari nilai rata-rata pesanan.

### Ringkasan 🏁

Hari ini, Anda belajar tentang:

- Berbagai jenis subkueri dan kasus penggunaannya.
- Menulis subquery pada klausa `SELECT`, `FROM`, dan `WHERE`.
- Perbedaan antara subkueri dan gabungan.

Subkueri adalah komponen kunci dari SQL tingkat lanjut, dan menguasainya akan sangat meningkatkan keterampilan kueri Anda.Besok, kita akan menjelajahi **Set Operations**!Bersiaplah untuk sesi menarik lainnya.🚀