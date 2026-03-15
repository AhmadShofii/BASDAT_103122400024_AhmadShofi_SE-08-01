# Database Bioskop - Tugas SQL

## Identitas
- **Nama:** AHMAD SHOOFI
- **NIM:** 103122400024
- **Mata Kuliah:** Basis Data
- **Topik:** Implementasi DDL, DML, dan Query SQL pada Database Bioskop

---

# 1. Menjalankan Query DDL dan DML

Database bioskop dibuat menggunakan script SQL yang berisi:

- **DDL (Data Definition Language)**  
  Digunakan untuk membuat struktur tabel.

- **DML (Data Manipulation Language)**  
  Digunakan untuk mengisi data ke dalam tabel.

Format nama tabel menggunakan **NIM**, yaitu:

FILM_103122400024
INVENTORI_103122400024
JADWAL_103122400024
MEMBER_103122400024
THEATER_103122400024
TRANSAKSI_103122400024


## Contoh struktur tabel

### Tabel FILM

```sql
CREATE TABLE FILM_103122400024 (
ID_FILM CHAR(5) NOT NULL,
JUDUL VARCHAR2(100),
SINOPSIS VARCHAR2(1000),
TAHUN NUMBER,
DURASI NUMBER
);

### Isi Tabel

SELECT * FROM FILM_103122400024;

### Query Diskon Harga Teater 15%

SELECT 
ID_THEATER,
KELAS,
HARGA AS HARGA_AWAL,
HARGA - (HARGA * 15/100) AS HARGA_SETELAH_DISKON
FROM THEATER_103122400024;

### Query Total Pemasukan Setiap Teater :

SELECT 
    t.ID_THEATER,
    t.KELAS,
    COUNT(tr.KODE_PEMESANAN) AS JUMLAH_TRANSAKSI,
    COUNT(tr.KODE_PEMESANAN) * t.HARGA AS TOTAL_PEMASUKAN
FROM THEATER_103122400024 t
LEFT JOIN JADWAL_103122400024 j
    ON t.ID_THEATER = j.ID_THEATER
LEFT JOIN TRANSAKSI_103122400024 tr
    ON j.ID_JADWAL = tr.ID_JADWAL
GROUP BY t.ID_THEATER, t.KELAS, t.HARGA
ORDER BY t.ID_THEATER;

### Kesimpulan

Dari implementasi database bioskop ini dapat disimpulkan bahwa:

DDL digunakan untuk membuat struktur tabel.

DML digunakan untuk memasukkan data ke tabel.

Query SQL dapat digunakan untuk melakukan analisis data seperti:

menghitung diskon harga

menghitung total pemasukan teater.

Database ini terdiri dari 6 tabel utama yang saling terhubung menggunakan Primary Key dan Foreign Key.