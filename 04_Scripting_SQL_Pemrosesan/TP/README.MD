# 🎬 Modul 4 – SQL JOIN

## Studi Kasus: Menampilkan Data Teater dan Kursi

---

## 📌 Deskripsi Kasus

Pada sistem bioskop, pegawai ingin melihat **seluruh data teater beserta seluruh kursi yang ada pada masing-masing teater**.

Informasi yang ingin ditampilkan:

* **Nomor Teater**
* **Nomor Kursi**

Karena setiap teater memiliki semua kursi yang sama, maka setiap teater harus dipasangkan dengan seluruh kursi yang tersedia.

Metode yang digunakan dalam SQL adalah **CROSS JOIN**.

---

# 🗂 Struktur Database

## 1️⃣ Tabel TEATER

Tabel ini menyimpan daftar teater yang tersedia.

| Kolom        | Tipe Data   | Keterangan          |
| ------------ | ----------- | ------------------- |
| nomor_teater | VARCHAR(20) | Nama / nomor teater |

### SQL: Membuat Tabel

```sql
CREATE TABLE TEATER (
    nomor_teater VARCHAR(20)
);
```

### SQL: Mengisi Data

```sql
INSERT INTO TEATER VALUES ('Teater 1');
INSERT INTO TEATER VALUES ('Teater 2');
INSERT INTO TEATER VALUES ('Teater 3');
INSERT INTO TEATER VALUES ('Teater 4');
INSERT INTO TEATER VALUES ('Teater 5');
```

---

## 2️⃣ Tabel KURSI

Tabel ini menyimpan daftar nomor kursi dalam satu teater.

| Kolom | Tipe Data  | Keterangan  |
| ----- | ---------- | ----------- |
| no_k  | VARCHAR(3) | Nomor kursi |

### SQL: Membuat Tabel

```sql
CREATE TABLE KURSI (
    no_k VARCHAR(3)
);
```

### SQL: Mengisi Data Kursi

Kursi terdiri dari baris **A sampai E**, masing-masing memiliki **8 kursi**.

```sql
INSERT INTO KURSI VALUES ('A1');
INSERT INTO KURSI VALUES ('A2');
INSERT INTO KURSI VALUES ('A3');
INSERT INTO KURSI VALUES ('A4');
INSERT INTO KURSI VALUES ('A5');
INSERT INTO KURSI VALUES ('A6');
INSERT INTO KURSI VALUES ('A7');
INSERT INTO KURSI VALUES ('A8');

INSERT INTO KURSI VALUES ('B1');
INSERT INTO KURSI VALUES ('B2');
INSERT INTO KURSI VALUES ('B3');
INSERT INTO KURSI VALUES ('B4');
INSERT INTO KURSI VALUES ('B5');
INSERT INTO KURSI VALUES ('B6');
INSERT INTO KURSI VALUES ('B7');
INSERT INTO KURSI VALUES ('B8');

INSERT INTO KURSI VALUES ('C1');
INSERT INTO KURSI VALUES ('C2');
INSERT INTO KURSI VALUES ('C3');
INSERT INTO KURSI VALUES ('C4');
INSERT INTO KURSI VALUES ('C5');
INSERT INTO KURSI VALUES ('C6');
INSERT INTO KURSI VALUES ('C7');
INSERT INTO KURSI VALUES ('C8');

INSERT INTO KURSI VALUES ('D1');
INSERT INTO KURSI VALUES ('D2');
INSERT INTO KURSI VALUES ('D3');
INSERT INTO KURSI VALUES ('D4');
INSERT INTO KURSI VALUES ('D5');
INSERT INTO KURSI VALUES ('D6');
INSERT INTO KURSI VALUES ('D7');
INSERT INTO KURSI VALUES ('D8');

INSERT INTO KURSI VALUES ('E1');
INSERT INTO KURSI VALUES ('E2');
INSERT INTO KURSI VALUES ('E3');
INSERT INTO KURSI VALUES ('E4');
INSERT INTO KURSI VALUES ('E5');
INSERT INTO KURSI VALUES ('E6');
INSERT INTO KURSI VALUES ('E7');
INSERT INTO KURSI VALUES ('E8');
```

Jumlah kursi total: **40 kursi**

---

# 🔗 Query JOIN

Untuk menampilkan semua teater dengan seluruh kursinya digunakan **CROSS JOIN**.

### SQL Query

```sql
SELECT t.nomor_teater, k.no_k
FROM TEATER t
CROSS JOIN KURSI k
ORDER BY t.nomor_teater, k.no_k;
```

---

# ⚙️ Cara Kerja Query

| Bagian Query     | Penjelasan                                           |
| ---------------- | ---------------------------------------------------- |
| SELECT           | Menentukan kolom yang akan ditampilkan               |
| FROM TEATER      | Menjadikan tabel TEATER sebagai tabel utama          |
| CROSS JOIN KURSI | Menggabungkan semua data teater dengan semua kursi   |
| ORDER BY         | Mengurutkan hasil berdasarkan teater dan nomor kursi |

---

# 📊 Hasil Query

Jumlah data:

* Jumlah teater = **5**
* Jumlah kursi = **40**

Total hasil:

```
5 × 40 = 200 rows
```

Contoh hasil:

```
NOMOR_TEATER   NO_K
Teater 1       A1
Teater 1       A2
Teater 1       A3
Teater 1       A4
...
Teater 5       E7
Teater 5       E8

200 rows selected
```

---

# 📚 Kesimpulan

* Query menggunakan **CROSS JOIN** karena setiap teater harus dipasangkan dengan seluruh kursi yang tersedia.
* CROSS JOIN menghasilkan **kombinasi semua baris dari dua tabel**.
* Jika terdapat **5 teater** dan **40 kursi**, maka hasil query menjadi **200 baris data**.

---

# 👨‍💻 Author

**Nama:** *AHMAD SHOFI*
**NIM:** *103122400024*
**Mata Kuliah:** Basis Data
**Modul:** Modul 4 – JOIN
**Topik:** CROSS JOIN pada SQL
