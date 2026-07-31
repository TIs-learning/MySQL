# Hari 13: Fungsi Tanggal dan Waktu di SQL 🌐

Hari ini, kita akan mendalami salah satu aspek paling serbaguna dari SQL—**Fungsi Tanggal dan Waktu**.Fungsi-fungsi ini membantu Anda memanipulasi dan menganalisis data temporal secara efektif, memungkinkan kemampuan kueri yang kuat.⏳

### Apa itu Fungsi Tanggal dan Waktu?❓

Fungsi Tanggal dan Waktu di SQL adalah operasi bawaan yang memungkinkan Anda mengekstrak, mengubah, dan menghitung data dari kolom temporal.Fungsi-fungsi ini penting untuk bekerja dengan jadwal, log, laporan, dan data sensitif waktu lainnya.

### Fungsi Tanggal dan Waktu yang Umum Digunakan ⏰

Berikut adalah beberapa fungsi Tanggal dan Waktu yang paling sering digunakan:

|**Fungsi** |**Deskripsi** |
|-------------------------------------|-----------------------------------------------------|
|`CURRENT_DATE` |Mengembalikan tanggal saat ini.|
|`CURRENT_TIME` |Mengembalikan waktu saat ini.|
|`NOW()` |Mengembalikan tanggal dan waktu saat ini.|
|`DATE()` |Mengekstrak bagian tanggal dari nilai `DATETIME`.|
|`TIME()` |Mengekstrak bagian waktu dari nilai `DATETIME`.|
|`YEAR()` |Mengekstrak tahun dari tanggal.|
|`MONTH()` |Mengekstrak bulan dari tanggal.|
|`DAY()` |Mengekstrak hari dalam sebulan dari tanggal.|
|`DATEDIFF()` |Mengembalikan jumlah hari antara dua tanggal.|
|`DATE_ADD()` |Menambahkan interval waktu tertentu ke tanggal.|
|`DATE_SUB()` |Mengurangi interval waktu tertentu dari suatu tanggal.|
|`DATE_FORMAT()` |Memformat tanggal menurut pola tertentu.|
|`TIMESTAMPDIFF()` |Mengembalikan perbedaan antara dua stempel waktu dalam unit yang dipilih.|

### Contoh Fungsi Tanggal dan Waktu 🔧

#### Contoh 1: Dapatkan Tanggal dan Waktu Saat Ini

```sql
SELECT CURRENT_DATE AS today, CURRENT_TIME AS current_time, NOW() AS current_datetime;
```
**Hasil:**

|hari ini |waktu_saat ini |waktu_saat ini |
|------------|--------------|------------------------|
|28-12-2024 |15:45:00 |28-12-2024 15:45:00 |

#### Contoh 2: Ekstrak Bagian Tanggal

```sql
SELECT YEAR(NOW()) AS year, MONTH(NOW()) AS month, DAY(NOW()) AS day;
```
**Hasil:**

|tahun |bulan |hari |
|------|-------|-----|
|2024 |12 |28 |

#### Contoh 3: Menghitung Selisih Tanggal

```sql
SELECT DATEDIFF('2025-01-01', '2024-12-28') AS days_difference;
```
**Hasil:**

|perbedaan_hari |
|-----------------|
|4 |

#### Contoh 4: Menambah dan Mengurangi Tanggal

```sql
SELECT
    DATE_ADD('2024-12-28', INTERVAL 7 DAY) AS next_week,
    DATE_SUB('2024-12-28', INTERVAL 1 MONTH) AS last_month;
```
**Hasil:**

|minggu_depan |bulan_terakhir |
|------------|-------------|
|04-01-2024 |28-11-2024 |

#### Contoh 5: Format Tanggal

```sql
SELECT DATE_FORMAT('2024-12-28', '%W, %M %d, %Y') AS formatted_date;
```
**Hasil:**

|tanggal_diformat |
|--------|
|Sabtu, 28 Desember 2024 |

### Latihan Latihan ⚖

1. Tulis kueri untuk mencari hari dalam seminggu untuk tanggal `2024-12-25`.
2. Hitung jumlah hari antara ulang tahun Anda dan hari ini.
3. Tambahkan 3 bulan ke tanggal sekarang dan tampilkan hasilnya.
4. Ekstrak tahun, bulan, dan hari dari stempel waktu `2023-11-15 08:45:30`.
5. Format tanggal sekarang dalam pola: `DD-MM-YYYY`.

### Ringkasan 🏁

Hari ini, kami belajar:

- Tujuan fungsi Tanggal dan Waktu.
- Fungsi SQL yang umum digunakan untuk data temporal.
- Contoh praktis dan cara memanipulasi tanggal dan waktu dalam kueri.

Besok, kita akan mempelajari **Latihan Tingkat Menengah dan Kuis** untuk mengkonsolidasikan pengetahuan kita.Teruslah berlatih, dan sampai jumpa besok!✨
