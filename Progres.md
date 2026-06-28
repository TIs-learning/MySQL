Day 1
----------
*syntax penting
> Melihat Semua Database: show databases;
> Membuat Database: create database nama_database;
> Menghapus database: drop database nama_database;
> Memilih database: use nama_database;
> melihat semua table di database: show tables;

*konsep penting
> setiap kolom memiliki 1 tipe data, tidak bisa berganti ganti
> yang membedakan jenis int adalah byte yang ditampung di memori
> Number: Int, float, decimal, attribute.
> String: Char, Varchar, perbedaannya adalah cara menyimpannya

Day 2
----------
*syntax penting
> Engine Mengolah data: show engines;
> membuat table: CREATE TABLE belajar_konsep
    -> (
    ->          id      INT,
    ->          nama    VARCHAR(100) NOT NULL,
    ->          harga   INT,
    ->          jumlah  INT
    -> ) ENGINE = InnoDB;
> Melihat Struktur Table: DESCRIBE nama_table; DESC nama_tabel; SHOW CREATE TABLE nama_tabel;
> Mengubah Table: ALTER TABLE namatable
	ADD COLUMN nama_column TEXT,
	DROP COLUMN nama,
	RENAME COLUMN nama TO nama_baru,
	MODIFY nama VARCHAR(100) AFTER jumlah,
	MODIFY nama VARCHAR(100) FIRST; bisa diganti NOT NULL; bisa ditumpuk juga DEAFULT 0;
> tidak boleh kosong: NOT NULL;
> set nilai default: DEFAULT 0; atau CURRENT_TIMESTAMP;
> Menghapus semua table dan membuat ulang table: TRUNCATE nama_table;
> Menghapus Table secara permanen: DROP TABLE nama_table;

*konsep penting
> Tipe data Date dan Time, Boolean, dan berbagai tipe data lainnya

Day 3
--------
*syntax 
> Memasukkan data > INSERT INTO;
INSERT INTO jadwal(id, Hari, name, description, quantity)
    -> VALUES ('1', 'Selasa', 'Louis', 'Python', '30'); (bisa ditumpuk juga
> Mengambil data: SELECT id, name, price, a, b from jadwal; (*  = semuanya)
CREATE TABLE Jadwal (
    id INT UNSIGNED NOT NULL AUTO_INCREMENT,
    Hari VARCHAR(10) NOT NULL,
    name VARCHAR(100) NOT NULL,
    description TEXT,
    quantity INT UNSIGNED NOT NULL DEFAULT 0,
    created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY (id)
) ENGINE = InnoDB;
> ADD PRIMARY KEY (id);

*konsep
> Primary Key = representasi id
> bisa multiple column
> set primary key = tidak bisa set nilai unik key yang sama

Day 4
--------
Xampp dan MySQL workbench
