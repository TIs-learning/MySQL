# Hari 12: Fungsi String dalam SQL 🎉

Hari ini, kita akan menjelajahi fungsi string di SQL—alat canggih untuk memanipulasi dan memproses data tekstual.Mari selami!🚀

### Pengantar Fungsi String 🔍

Fungsi string digunakan untuk memanipulasi atau mengambil informasi dari data string.Baik Anda membersihkan data yang berantakan, mengekstraksi bagian teks yang bermakna, atau memformat string untuk pelaporan, fungsi string SQL sangat diperlukan.

### Fungsi String yang Biasa Digunakan 🆒

#### ATAS dan BAWAH
- Ubah teks menjadi huruf besar atau kecil.

```sql
SELECT UPPER('hello') AS uppercase, LOWER('WORLD') AS lowercase;
```
**Hasil:**

|huruf besar |huruf kecil |
|-----------|-----------|
|HALO |dunia |

#### PANJANG/PANJANG_CHAR
- Temukan panjang string.

```sql
SELECT LENGTH('hello world') AS length;
```
**Hasil:**

|panjang |
|--------|
|11 |

#### PANGKAS
- Hapus spasi awal atau akhir (atau karakter tertentu).

```sql
SELECT TRIM('   hello   ') AS trimmed;
```
**Hasil:**

|dipangkas |
|---------|
|halo |

#### SUBSTRING/SUBSTR
- Ekstrak sebagian string.

```sql
SELECT SUBSTRING('hello world', 1, 5) AS substring;
```
**Hasil:**

|substring |
|-----------|
|halo |

#### HUBUNGI
- Gabungkan beberapa string menjadi satu.

```sql
SELECT CONCAT('hello', ' ', 'world') AS concatenated;
```
**Hasil:**

|digabungkan |
|--------------|
|halo dunia |

#### GANTI
- Ganti kemunculan substring dengan yang lain.

```sql
SELECT REPLACE('hello world', 'world', 'SQL') AS replaced;
```
**Hasil:**

|diganti |
|-------------|
|halo SQL |

#### INSTR
- Temukan posisi substring dalam string.

```sql
SELECT INSTR('hello world', 'world') AS position;
```
**Hasil:**

|posisi |
|----------|
|7 |

### Fungsi String Tingkat Lanjut 🔬

#### KIRI dan KANAN
- Ekstrak sejumlah karakter tertentu dari awal atau akhir string.

```sql
SELECT LEFT('hello world', 5) AS left_part, RIGHT('hello world', 5) AS right_part;
```
**Hasil:**

|bagian_kiri |bagian_kanan |
|-----------|------------|
|halo |dunia |

#### LPAD dan RPAD
- Padukan string dengan panjang tertentu dengan karakter tertentu.

```sql
SELECT LPAD('SQL', 5, '*') AS lpad, RPAD('SQL', 5, '*') AS rpad;
```
**Hasil:**

|lpad |rpad |
|-------|-------|
|**SQL |SQL** |

#### MUNDUR
- Membalikkan urutan karakter dalam sebuah string.

```sql
SELECT REVERSE('SQL') AS reversed;
```
**Hasil:**

|terbalik |
|----------|
|LQS |

### Contoh Praktis 🌐

#### Contoh 1: Membersihkan Data

Misalkan Anda memiliki tabel `users`:

|identitas |nama pengguna |
|----|--------------|
|1 |Alice123 |
|2 |Bob456 |

Untuk membersihkan spasi dan mengubah nama pengguna menjadi huruf kecil:

```sql
SELECT id, TRIM(LOWER(username)) AS cleaned_username
FROM users;
```
**Hasil:**

|identitas |dibersihkan_nama pengguna |
|----|------------------|
|1 |alice123 |
|2 |bob456 |

#### Contoh 2: Mengekstrak Domain dari Email

Diberikan tabel `contacts`:

|identitas |email |
|----|----------------------|
|1 |alice@example.com |
|2 |bob@sqlchallenge.com |

Untuk mengekstrak domain:

```sql
SELECT id, SUBSTRING(email, INSTR(email, '@') + 1) AS domain
FROM contacts;
```
**Hasil:**

|identitas |domain |
|----|---------------------|
|1 |contoh.com |
|2 |sqlchallenge.com |

### Latihan Latihan 🏆

1. Tulis query untuk mengubah semua nama dalam tabel `customers` menjadi huruf besar.
2. Ekstrak 3 karakter pertama kolom `product_code` dari tabel `products`.
3. Tulis query untuk mengganti semua spasi pada kolom `address` dengan garis bawah.
4. Carilah posisi kemunculan pertama '@' pada kolom `email`.
5. Balikkan teks pada kolom `comments`.

### Ringkasan 🌟

Hari ini, kami membahas:

- Fungsi string umum dan lanjutan seperti `UPPER`, `TRIM`, `SUBSTRING`, dan `REVERSE`.
- Aplikasi praktis untuk membersihkan dan memanipulasi data tekstual.
- Contoh dan latihan untuk memantapkan pemahaman Anda.

Besok, kita akan beralih ke **Fungsi Tanggal dan Waktu**!Pantau terus!🚀