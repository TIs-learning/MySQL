# MySQL
Documenting Learning Database SQL

# Roadmap
Belajar MySQL dari nol adalah langkah yang sangat taktis, terutama untuk memperkuat fondasi pengolahan data sebelum masuk ke tahap analitik atau pemodelan. Memahami cara kerja database relasional akan mengubah cara Anda menstrukturkan informasi.

Berikut adalah roadmap komprehensif untuk menguasai MySQL, dirancang agar Anda bisa langsung mengaplikasikannya ke dalam alur kerja data yang nyata.

### Fase 1: Fondasi Pengambilan Data (Data Query Language)

Fokus pertama adalah mengambil dan menyaring data yang sudah ada. Menguasai tahap ini memungkinkan Anda melakukan filterisasi awal di level database, sehingga proses analisis selanjutnya menjadi lebih ringan.

* **Sintaks Dasar:** Memahami struktur `SELECT`, `FROM`, dan `WHERE`.
* **Filter & Logika:** Menggunakan operator seperti `AND`, `OR`, `IN`, `BETWEEN`, dan `LIKE`.
* **Penanganan Nilai Kosong:** Mengidentifikasi data yang hilang menggunakan `IS NULL` dan `IS NOT NULL` (konsep ini merupakan garda terdepan sebelum Anda melakukan operasi seperti pembersihan kolom pada tahap analisis lanjutan).
* **Agregasi & Pengelompokan:** Menggunakan fungsi agregat (`COUNT`, `SUM`, `AVG`, `MAX`, `MIN`) dan mengelompokkan data dengan `GROUP BY` serta `HAVING`.

### Fase 2: Relasi dan Penggabungan Data (Joins)

Database relasional memecah data ke dalam banyak tabel untuk efisiensi. Fase ini krusial untuk menyatukan kembali informasi tersebut.

* **Kunci Relasional:** Memahami konsep *Primary Key* (identitas unik sebuah baris) dan *Foreign Key* (referensi ke tabel lain).
* **Tipe Penggabungan:** Menguasai `INNER JOIN`, `LEFT JOIN`, `RIGHT JOIN`, dan `FULL OUTER JOIN`. Logika struktural di sini sangat identik dengan operasi *merge* saat Anda menggabungkan berbagai dataset.

### Fase 3: Pembuatan dan Manipulasi Data (DDL & DML)

Setelah bisa mengambil data, Anda perlu tahu cara membuat wadahnya dan mengubah isinya.

* **Data Definition Language (DDL):** Membuat dan memodifikasi struktur tabel menggunakan `CREATE TABLE`, `ALTER TABLE`, dan `DROP TABLE`. Memahami tipe data dasar di MySQL (seperti `INT`, `VARCHAR`, `DATE`, `FLOAT`).
* **Data Manipulation Language (DML):** Menambah, mengubah, dan menghapus isi data menggunakan `INSERT INTO`, `UPDATE`, dan `DELETE`.

### Fase 4: Teknik Analisis Lanjutan

Fase ini memisahkan pengguna dasar dari mereka yang bisa melakukan manipulasi data tingkat lanjut langsung di dalam mesin database.

* **Subqueries:** Menulis *query* di dalam *query* untuk logika bertingkat.
* **Common Table Expressions (CTE):** Menggunakan klausa `WITH` untuk membuat tabel sementara yang membuat *query* kompleks menjadi lebih mudah dibaca dan di-debug.
* **Window Functions:** Menggunakan `ROW_NUMBER()`, `RANK()`, dan `OVER()` untuk melakukan kalkulasi pada sekumpulan baris yang saling berhubungan tanpa menggabungkannya ke dalam satu baris (sangat berguna untuk data deret waktu atau peringkat).

### Fase 5: Integrasi dengan Ekosistem Python

Database jarang berdiri sendiri. Nilai aslinya muncul saat dihubungkan dengan bahasa pemrograman.

* **Konektor Database:** Menggunakan *library* seperti `mysql-connector-python` atau `SQLAlchemy` untuk membangun jembatan komunikasi antara MySQL dan Python.
* **Ekstraksi ke DataFrame:** Menjalankan *query* SQL dari Python dan menyimpan hasilnya langsung ke dalam struktur tabel. Dari titik ini, data yang sudah bersih dan terelasi siap didorong ke dalam *pipeline* algoritma klasifikasi atau regresi (seperti Random Forest atau Gradient Boosting) menggunakan *library* standar seperti Scikit-learn.

---

### Saran Ekskusi Pembelajaran

* **Gunakan Dummy Data:** Mulailah dengan membuat tabel berisi *dummy data* sederhana, misalnya skema "Toko Online" dengan tabel Pelanggan, Produk, dan Transaksi. Jangan langsung berlatih menggunakan dataset produksi yang masif agar Anda bisa fokus pada pemahaman mekanika logika *query* tanpa merasa kewalahan.
* **Eksplorasi Referensi Lokal:** *Channel* YouTube pendidikan seperti Indonesia Belajar memiliki seri video yang sangat terstruktur mengenai logika dasar database dan integrasinya, yang bisa menjadi pelengkap visual yang bagus selain membaca dokumentasi resmi atau buku teks.

Bagian mana dari roadmap ini yang ingin kita bahas lebih dalam pertama kali, atau apakah Anda ingin saya buatkan *script* SQL untuk membangun struktur database dan *dummy data* pertama Anda?
