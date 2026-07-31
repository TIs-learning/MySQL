📘 30 Hari SQL: Hari ke-19 - Transaksi dan Kontrol Konkurensi

Hari ini, kita akan menjelajahi transaksi dan kontrol konkurensi, dua konsep penting untuk memastikan integritas dan konsistensi data dalam lingkungan basis data multi-pengguna.

### 🔍 Gambaran Umum

Transaksi adalah urutan satu atau lebih operasi SQL yang dieksekusi sebagai satu unit kerja logis. Kontrol konkurensi memastikan bahwa banyak pengguna dapat mengakses basis data secara bersamaan tanpa konflik atau inkonsistensi data. Bersama-sama, konsep-konsep ini membentuk dasar untuk operasi basis data yang andal.

---

### 📘 Transaksi

#### 1. Properti Transaksi (ACID)

Transaksi mematuhi properti berikut:

- **Atomisitas**: Semua operasi dalam transaksi berhasil atau gagal sebagai satu kesatuan.
- **Konsistensi**: Transaksi membawa basis data dari satu keadaan valid ke keadaan valid lainnya.
- **Isolasi**: Transaksi bersifat independen satu sama lain.
- **Ketahanan**: Setelah transaksi dikomit, perubahannya tetap ada meskipun terjadi kegagalan sistem.

#### 2. Perintah Transaksi

- **`BEGIN`**: Memulai transaksi.
- **`COMMIT`**: Menyimpan semua perubahan yang dilakukan dalam transaksi.
- **`ROLLBACK`**: Membatalkan semua perubahan yang dilakukan dalam transaksi.
- **`SAVEPOINT`**: Membuat titik dalam transaksi tempat Anda dapat melakukan rollback.

**Contoh**:

```sql
BEGIN;

UPDATE accounts
SET balance = balance - 500
WHERE account_id = 1;

UPDATE accounts
SET balance = balance + 500
WHERE account_id = 2;

COMMIT;
```

---

### 💡 Kontrol Konkurensi

#### 1. Tingkat Isolasi

SQL mendefinisikan empat tingkat isolasi untuk mengontrol visibilitas perubahan antar transaksi:

- **Read Uncommitted**: Transaksi dapat melihat perubahan yang belum di-commit dari transaksi lain.
- **Read Committed**: Transaksi hanya melihat perubahan yang telah di-commit dari transaksi lain.
- **Repeatable Read**: Memastikan pembacaan yang konsisten selama transaksi.
- **Serializable**: Memberikan tingkat isolasi tertinggi dengan mengunci data sepenuhnya.

**Pengaturan Tingkat Isolasi**:

```sql
SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;
BEGIN;
-- Transaction code here
COMMIT;
```

#### 2. Mekanisme Penguncian

- **Shared Lock**: Memungkinkan beberapa transaksi untuk membaca suatu sumber daya tetapi tidak dapat memodifikasinya.

- **Exclusive Lock**: Memungkinkan satu transaksi untuk memodifikasi suatu sumber daya sambil mencegah transaksi lain mengaksesnya.

- **Deadlock**: Terjadi ketika dua atau lebih transaksi saling memblokir.

---

### 🔧 Praktik Terbaik

- **Minimalkan Waktu Penguncian**: Jaga agar transaksi tetap singkat untuk menghindari penguncian sumber daya dalam jangka waktu yang lama.

- **Gunakan Tingkat Isolasi yang Tepat**: Pilih tingkat isolasi berdasarkan kebutuhan aplikasi.

- **Hindari Deadlock**: Pastikan transaksi mengakses sumber daya dalam urutan yang konsisten.

- **Uji Secara Menyeluruh**: Simulasikan transaksi konkuren untuk mendeteksi potensi konflik.

---

### 🎯 Tantangan Praktik

1. Tulis transaksi untuk mentransfer dana antar rekening dengan penanganan kesalahan yang tepat.

2. Uji berbagai tingkat isolasi dan amati dampaknya pada transaksi konkuren.

3. Buat skenario di mana terjadi deadlock dan selesaikan.

4. Implementasikan transaksi dengan beberapa savepoint dan rollback.

---

### 💻 Latihan - Hari ke-19

#### ✅ Latihan: Level 1

1. Tulis transaksi untuk memperbarui level stok dan melakukan commit perubahan.

2. Buat savepoint selama transaksi dan lakukan rollback ke savepoint tersebut.

3. Demonstrasikan penggunaan perintah `ROLLBACK` jika terjadi kesalahan.

#### 🚀 Latihan: Level 2

1. Simulasikan transaksi konkuren yang mengakses sumber daya yang sama dengan tingkat isolasi yang berbeda.

2. Tulis query untuk mendeteksi dan menyelesaikan skenario deadlock.

3. Implementasikan serangkaian transaksi untuk mempertahankan keadaan yang konsisten dalam database penjualan.

---

### 📝 Ringkasan Hari ke-19

Hari ini, kita membahas transaksi dan kontrol konkurensi, mengeksplorasi perannya dalam menjaga integritas basis data dan menangani lingkungan multi-pengguna. Dengan pengetahuan ini, Anda dapat membuat aplikasi SQL yang tangguh dan tahan terhadap kesalahan.

Nantikan Hari ke-20, di mana kita akan membahas Latihan dan Kuis SQL Tingkat Lanjut! 🚀