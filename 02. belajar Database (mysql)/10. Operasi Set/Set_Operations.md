# Hari 11: Mengatur Operasi di SQL ✨

Hari ini, kita mempelajari **Set Operations** — cara ampuh untuk menggabungkan hasil kueri dalam SQL.Menguasai operasi kumpulan akan secara signifikan meningkatkan kemampuan Anda untuk bekerja dengan kumpulan data yang kompleks.Mari kita mulai!🚀

## Apa itu Operasi Set?🔎

Operasi set memungkinkan Anda menggabungkan hasil dari dua atau lebih pernyataan `SELECT`.Operasi ini memperlakukan hasil kueri sebagai kumpulan dan melakukan operasi seperti gabungan, persimpangan, dan perbedaan.

### Poin Penting:

- Semua kueri yang terlibat dalam operasi kumpulan harus memiliki jumlah kolom yang sama.
- Kolom harus memiliki tipe data yang kompatibel.
- Urutan kolom penting.

## Jenis Operasi Set 🛠

### 1. PERSATUAN

Menggabungkan hasil dua kueri dan menghapus baris duplikat.

**Sintaks:**
```sql
SELECT column1, column2 FROM table1
UNION
SELECT column1, column2 FROM table2;
```

### 2. PERSATUAN SEMUA

Menggabungkan hasil dua kueri tetapi **menyertakan duplikat**.

**Sintaks:**
```sql
SELECT column1, column2 FROM table1
UNION ALL
SELECT column1, column2 FROM table2;
```

### 3. BERSINTANG

Mengembalikan baris yang **umum** untuk kedua kueri.

**Sintaks:**
```sql
SELECT column1, column2 FROM table1
INTERSECT
SELECT column1, column2 FROM table2;
```

### 4. KECUALI (atau MINUS di beberapa sistem)

Mengembalikan baris dari kueri pertama yang **tidak ada** di kueri kedua.

**Sintaks:**
```sql
SELECT column1, column2 FROM table1
EXCEPT
SELECT column1, column2 FROM table2;
```

## Contoh Operasi Himpunan 🔢

### Contoh 1: UNION

**Skenario:** Gabungkan karyawan dari dua departemen berbeda.

```sql
SELECT name FROM department_a
UNION
SELECT name FROM department_b;
```

**Hasil:**

|nama |
|----------|
|Alice |
|Bob |
|Karol |

### Contoh 2: UNION SEMUA

**Skenario:** Gabungkan karyawan, tetapi sertakan nama duplikat.

```sql
SELECT name FROM department_a
UNION ALL
SELECT name FROM department_b;
```

**Hasil:**

|nama |
|----------|
|Alice |
|Bob |
|Alice |

### Contoh 3: INTERSECT

**Skenario:** Temukan karyawan yang bekerja di kedua departemen.

```sql
SELECT name FROM department_a
INTERSECT
SELECT name FROM department_b;
```

**Hasil:**

|nama |
|----------|
|Alice |

### Contoh 4: KECUALI

**Skenario:** Temukan karyawan di departemen A tetapi tidak di departemen B.

```sql
SELECT name FROM department_a
EXCEPT
SELECT name FROM department_b;
```

**Hasil:**

|nama |
|----------|
|Bob |

### Latihan Latihan 🔧

1. Diketahui `orders_2023` dan `orders_2024`, temukan semua pelanggan unik yang melakukan pemesanan pada tahun mana pun.
2. Temukan pelanggan yang melakukan pemesanan di `orders_2023` dan `orders_2024`.
3. Ambil produk yang terdaftar di `products_2023` tetapi tidak di `products_2024`.
4. Gabungkan dua tabel penjualan dan sertakan entri duplikat.
5. Tulis kueri untuk mencari karyawan yang bekerja di dua proyek tertentu menggunakan `INTERSECT`.

### Ringkasan 🏁

Hari ini, Anda belajar tentang:

- Empat jenis operasi himpunan: `UNION`, `UNION ALL`, `INTERSECT`, dan `EXCEPT`.
- Cara menggunakan operasi set untuk menggabungkan hasil kueri.
- Skenario praktis di mana operasi yang ditetapkan dapat menyederhanakan kueri yang kompleks.

Besok, kita akan mendalami **Fungsi String** — topik menarik untuk memanipulasi dan menganalisis data teks!Pantau terus!🚀