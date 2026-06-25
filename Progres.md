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

Dat 2
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
