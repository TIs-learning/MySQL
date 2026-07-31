# 📘 30 Hari SQL: Hari ke-23 - Trigger dan Event

Selamat datang di **Hari ke-23** dari tantangan **30 Hari SQL**! 🎉 Hari ini, kita akan menjelajahi **Trigger dan Event** dalam SQL, alat yang ampuh untuk mengotomatiskan tindakan dan menjaga integritas data dalam basis data Anda.

## 🔍 Gambaran Umum

**Trigger** adalah objek basis data yang dieksekusi secara otomatis sebagai respons terhadap peristiwa tertentu, seperti operasi `INSERT`, `UPDATE`, atau `DELETE` pada sebuah tabel. Trigger membantu menegakkan aturan bisnis, menjaga jejak audit, dan mengotomatiskan proses.

**Event** dalam SQL adalah tindakan terjadwal yang dieksekusi oleh server basis data pada waktu atau interval tertentu. Event berguna untuk mengotomatiskan tugas rutin seperti pencadangan, pengarsipan, atau operasi pembersihan.

---

## 📘 Apa itu Trigger?

### 1. Jenis Trigger

| **Tipe Pemicu** | **Deskripsi** |

|-------------------------|---------------------------------------------------------|

| Pemicu `BEFORE` | Dieksekusi sebelum operasi SQL pemicu. |

| Pemicu `AFTER` | Dieksekusi setelah operasi SQL pemicu. |

| Pemicu `INSTEAD OF` | Menggantikan operasi SQL pemicu (digunakan dalam tampilan). |

### 2. Sintaks Pemicu

**Sintaks Umum**:

```sql
CREATE TRIGGER trigger_name
{ BEFORE | AFTER | INSTEAD OF } { INSERT | UPDATE | DELETE }
ON table_name
[FOR EACH ROW]
BEGIN
    -- Trigger logic
END;
```

**Contoh**: Catat setiap karyawan baru yang ditambahkan ke tabel `employees`.

```sql
CREATE TRIGGER log_new_employee
AFTER INSERT
ON employees
FOR EACH ROW
BEGIN
    INSERT INTO employee_logs (employee_id, action, timestamp)
    VALUES (NEW.id, 'INSERT', CURRENT_TIMESTAMP);
END;
```

---

## ⚡ Event dalam SQL

### 1. Apa itu Event?

Event memungkinkan Anda untuk menjalankan tindakan yang telah ditentukan sebelumnya pada interval atau waktu tertentu. Event sering digunakan untuk tugas pemeliharaan.

### 2. Membuat dan Mengelola Event

**Sintaks Umum**:

```sql
CREATE EVENT event_name
ON SCHEDULE { AT timestamp | EVERY interval }
DO
BEGIN
    -- Event logic
END;
```

**Contoh**: Bersihkan data lama dari tabel `logs` setiap hari.

```sql
CREATE EVENT daily_log_cleanup
ON SCHEDULE EVERY 1 DAY
DO
BEGIN
    DELETE FROM logs WHERE log_date < NOW() - INTERVAL 30 DAY;
END;
```

---

## 💡 Contoh Praktis

### Contoh 1: Jejak Audit dengan Pemicu

Catat setiap penghapusan dari tabel `orders`.

```sql
CREATE TRIGGER log_order_deletion
AFTER DELETE
ON orders
FOR EACH ROW
BEGIN
    INSERT INTO order_logs (order_id, action, timestamp)
    VALUES (OLD.id, 'DELETE', CURRENT_TIMESTAMP);
END;
```

### Contoh 2: Pencadangan Otomatis dengan Peristiwa

Buat cadangan tabel `customers` setiap minggu.

```sql
CREATE EVENT weekly_customer_backup
ON SCHEDULE EVERY 1 WEEK
DO
BEGIN
    CREATE TABLE customers_backup AS SELECT * FROM customers;
END;
```

---

## 🔧 Praktik Terbaik

1. **Jaga Logika Trigger Tetap Sederhana**: Hindari logika yang kompleks untuk meminimalkan beban kinerja.

2. **Gunakan Event dengan Hemat**: Penggunaan event yang berlebihan dapat menyebabkan perebutan sumber daya.

3. **Pantau dan Uji**: Uji trigger dan event secara teratur untuk memastikan fungsinya sesuai harapan.

4. **Dokumentasikan Trigger dan Event Anda**: Buat dokumentasi yang jelas untuk pemeliharaan yang lebih baik.

---

## 🎯 Tantangan Praktik Langsung

1. Buat trigger untuk mencatat pembaruan pada tabel `products`.

2. Jadwalkan event untuk mengarsipkan data dari tabel `sales` setiap bulan.

3. Tulis trigger untuk mencegah penghapusan baris penting di tabel `users`.

---

## 💻 Latihan - Hari ke-23

### ✅ Latihan: Level 1

1. Tulis trigger `BEFORE INSERT` untuk memvalidasi data sebelum dimasukkan ke dalam tabel `orders`.

2. Buat event untuk menghapus record yang lebih lama dari 60 hari dari tabel `sessions`.

### 🚀 Latihan: Level 2

1. Tulis trigger `AFTER UPDATE` untuk melacak perubahan pada tabel `inventory`.

2. Jadwalkan event untuk mengoptimalkan semua tabel dalam database setiap minggu.

---

## 📝 Ringkasan Hari ke-23

Hari ini, Anda telah mempelajari tentang **Trigger** dan **Event** dalam SQL, dua mekanisme ampuh untuk mengotomatiskan tindakan dan menjaga integritas data. Alat-alat ini sangat penting untuk mengoptimalkan operasi database dan mengimplementasikan logika bisnis langsung di tingkat database.

Nantikan **Hari ke-24**, di mana kita akan membahas **Impor dan Ekspor Data**! 🚀
