# 📘 30 Hari SQL: Hari ke-27 - Keamanan SQL

Hari ini, kita akan menjelajahi topik penting **Keamanan SQL**, dengan fokus pada teknik dan praktik terbaik untuk mengamankan basis data Anda dari akses tidak sah dan potensi ancaman.

## 🔍 Gambaran Umum

Mengamankan basis data Anda sangat penting untuk menjaga integritas, kerahasiaan, dan ketersediaan data Anda. Keamanan SQL mencakup berbagai praktik, mulai dari otentikasi pengguna hingga enkripsi data sensitif. Dengan menerapkan langkah-langkah ini, Anda dapat melindungi basis data Anda dari akses tidak sah dan serangan berbahaya.

---

## 🔑 Otentikasi dan Otorisasi

### 1. Akun dan Peran Pengguna

Akun dan peran pengguna membentuk dasar keamanan basis data:

- **Akun Pengguna**: Pengidentifikasi unik untuk individu atau aplikasi yang mengakses basis data.

- **Peran**: Kelompok izin yang diberikan kepada pengguna untuk menyederhanakan manajemen.

**Contoh** (Membuat pengguna dan menetapkan peran):
```sql
-- Create a user
CREATE USER 'report_user'@'localhost' IDENTIFIED BY 'secure_password';

-- Create a role and grant it permissions
CREATE ROLE data_analyst;
GRANT SELECT, INSERT ON database_name.* TO data_analyst;

-- Assign the role to the user
GRANT data_analyst TO 'report_user'@'localhost';
```

---

### 2. Memberikan dan Mencabut Izin

Gunakan pernyataan `GRANT` dan `REVOKE` untuk mengontrol akses pengguna:

**Grant Permissions**:
```sql
GRANT SELECT, UPDATE ON employees TO 'report_user'@'localhost';
```

**Revoke Permissions**:
```sql
REVOKE UPDATE ON employees FROM 'report_user'@'localhost';
```

---

## 🔒 Mengamankan Data

### 1. Enkripsi

Enkripsi memastikan data sensitif disimpan dan ditransmisikan dengan aman:

- **Saat Diam**: Enkripsi data yang tersimpan dalam tabel.

- **Saat Ditransmisikan**: Gunakan SSL/TLS untuk komunikasi yang aman antara basis data dan klien.

**Example** (MySQL enabling SSL):
```bash
# In the MySQL configuration file (my.cnf):
[mysqld]
ssl-ca=/path/to/ca.pem
ssl-cert=/path/to/server-cert.pem
ssl-key=/path/to/server-key.pem
```

---

### 2. Menyamarkan Data Sensitif

Penyamaran data menyembunyikan informasi sensitif, seperti nomor kartu kredit, dari pengguna yang tidak berwenang:

**Example**:
```sql
-- Partial masking
SELECT CONCAT(SUBSTRING(phone_number, 1, 3), '****', SUBSTRING(phone_number, 7)) AS masked_number
FROM users;
```

---

### 3. Audit dan Pencatatan Log

Audit melacak aktivitas basis data untuk tujuan kepatuhan dan pemecahan masalah:
**Enable Auditing**:
```sql
-- MySQL Audit Plugin
INSTALL PLUGIN audit_log SONAME 'audit_log.so';
SET GLOBAL audit_log_policy = 'ALL';
```

---

## 🛡️ Melindungi dari SQL Injection

SQL injection adalah serangan umum di mana kode SQL berbahaya disuntikkan ke dalam kueri. Langkah-langkah pencegahan meliputi:

1. **Kueri Berparameter**:
```sql
-- Example in Python
cursor.execute("SELECT * FROM users WHERE username = %s", (username,))
```

2. **Memvalidasi Input**:

- Membersihkan input pengguna.

- Menolak karakter yang tidak terduga.

3. **Membatasi Hak Akses**:

- Memastikan aplikasi hanya memiliki izin yang diperlukan.

---

## 💡 Praktik Terbaik

1. Gunakan kata sandi yang kuat dan unik untuk semua akun basis data.

2. Lakukan audit dan tinjau izin pengguna secara berkala.

3. Aktifkan otentikasi multi-faktor (MFA) jika memungkinkan.

4. Lakukan patch dan pembaruan sistem basis data secara berkala.

5. Pantau aktivitas mencurigakan menggunakan alat pencatatan dan peringatan.

---

## 🎯 Tantangan Praktik Langsung

1. **Buat Pengguna yang Aman**: Buat akun pengguna dengan izin terbatas untuk alat pelaporan.

2. **Aktifkan Pencatatan**: Konfigurasikan audit dan pencatatan basis data.

3. **Uji Injeksi**: Coba serangan injeksi SQL pada basis data uji dan amankan menggunakan kueri berparameter.

---

## 💻 Latihan - Hari ke-27

### ✅ Latihan: Level 1

1. Buat pengguna dengan izin `SELECT` pada tabel tertentu.

2. Aktifkan SSL/TLS untuk basis data MySQL atau PostgreSQL.

3. Gunakan `GRANT` dan `REVOKE` untuk mengelola izin pengguna.

### 🚀 Latihan: Level 2

1. Terapkan masking data untuk kolom sensitif dalam tabel contoh.

2. Aktifkan dan konfigurasikan audit untuk melacak login dan perubahan basis data.

3. Tulis kueri yang aman untuk mencegah serangan injeksi SQL.

---

## 📝 Ringkasan Hari ke-27

Hari ini, kita telah membahas topik-topik penting dalam **Keamanan SQL**, termasuk otentikasi, otorisasi, enkripsi, dan perlindungan terhadap injeksi SQL. Praktik-praktik ini memastikan integritas dan keamanan basis data Anda. Besok, kita akan menyelesaikan tantangan ini dengan **Membangun Proyek Dunia Nyata**! 🎉
