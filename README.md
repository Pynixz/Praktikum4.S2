# Praktikum4.S2
## Mata Kuliah

Sebagai tugas praktikum: [4] Basis Data | Universitas Pelita Bangsa.

## Laporan Praktikum

### Membuat Tabel 1 (Pegawai) dan Tabel 2 (Hewan)

- Bagian 1:

  > Membuat Tabel 1 khusus untuk pertanyaan Pegawai.

```sql
CREATE TABLE IF NOT EXISTS pegawai (
    idpegawai VARCHAR(5),
    nama_depan VARCHAR(50),
    nama_belakang VARCHAR(50),
    email VARCHAR(100),
    telepon VARCHAR(15),
    tgl_kontrak DATE,
    id_job VARCHAR(5),
    gaji INT,
    tunjangan INT,
    PRIMARY KEY (idpegawai)
);

INSERT INTO pegawai (idpegawai, nama_depan, nama_belakang, email, telepon, tgl_kontrak, id_job, gaji, tunjangan)
VALUES 
('E001', 'Ferry', 'Gustiawan', 'ferry@yahoo.com', '07117059004', '2005-09-01', 'L0001', 2000000, 500000),
('E002', 'Aris', 'Ganiardi', 'aris@yahoo.com', '081312345678', '2006-09-01', 'L0002', 2000000, 200000),
('E003', 'Faiz', 'Ahnad', 'faiz@gmail.com', '081367384322', '2006-10-01', 'L0003', 1500000, NULL),
('E004', 'Emna', 'Bunton', 'enna@gmail.com', '081363484342', '2006-10-01', 'L0004', 1500000, 9),
('E005', 'Mike', 'Scoff', 'mike@plasa.com', '08163454555', '2007-09-01', 'L0005', 1250000, 9),
('E006', 'Lincoln', 'Burrows', 'linc@yahoo.com', '08527388432', '2008-09-01', 'L0006', 1750000, NULL);```
```

- Bagian 2:

  > Membuat Tabel 1 khusus untuk pertanyaan Hewan.

```sql
CREATE TABLE IF NOT EXISTS hewan (
    id VARCHAR(2),
    name VARCHAR(50),
    owner VARCHAR(50),
    species VARCHAR(50),
    sex CHAR(1),
    PRIMARY KEY (id)
);

INSERT INTO hewan (id, name, owner, species, sex)
VALUES 
('p1', 'Puffball', 'Diane', 'hamster', 'f'),
('p2', 'Claws', 'Gwen', 'cat', 'm'),
('p3', 'Fluffy', 'Haro 1d', 'cat', 'f'),
('p4', 'Buffy', 'Haro 1d', 'dog', 'f'),
('p5', 'Fang', 'Benny', 'dog', 'm'),
('p6', 'Bowser', 'Diane', 'dog', 'm'),
('p7', 'Chirpy', 'Gwen', 'bird', 'f'),
('p8', 'Whistler', 'Gwen', 'bird', NULL),
('p9', 'Slim', 'Benny', 'snake', 'm');
```

### Pertanyaan Tabel 1 (Pegawai)

1. Tampilkan pegawai yang gajinya bukan 2.000.000 dan 1.250.000:
```sql
SELECT * FROM pegawai WHERE gaji NOT IN (2000000, 1250000);
```

2. Tampilkan pegawai yang tunjangannya NULL:
```sql
SELECT * FROM pegawai WHERE tunjangan IS NULL;
```

3. Tampilkan pegawai yang tunjangannya tidak NULL:
```sql
SELECT * FROM pegawai WHERE tunjangan IS NOT NULL;
```

4. Tampilkan/hitung jumlah baris/record tabel pegawai:
```sql
SELECT COUNT(*) AS jumlah_pegawai FROM pegawai;
```

5. Tampilkan/hitung jumlah total gaji di tabel pegawai:
```sql
SELECT SUM(gaji) AS total_gaji FROM pegawai;
```

6. Tampilkan/hitung rata-rata gaji pegawai:
```sql
SELECT AVG(gaji) AS rata_rata_gaji FROM pegawai;
```

7. Tampilkan gaji terkecil:
```sql
SELECT MIN(gaji) AS gaji_terkecil FROM pegawai;
```

8. Tampilkan gaji terbesar:
```sql
SELECT MAX(gaji) AS gaji_terbesar FROM pegawai;
```

### Pertanyaan Tabel 2 (Hewan)

1. Tampilkan jumlah hewan yang dimiliki setiap owner:
```sql
SELECT id, COUNT(*) AS jumlah_hewan FROM hewan GROUP BY id;
```

2. Tampilkan jumlah hewan berdasarkan spesies:
```sql
SELECT species, COUNT(*) AS jumlah_hewan FROM hewan GROUP BY species;
```

3. Tampilkan jumlah hewan berdasarkan jenis kelamin:
```sql
SELECT sex, COUNT(*) AS jumlah_hewan FROM hewan GROUP BY sex;
```

4. Tampilkan jumlah hewan berdasarkan spesies dan jenis kelamin:
```sql
SELECT species, sex, COUNT(*) AS jumlah_hewan FROM hewan GROUP BY species, sex;
```

5. Tampilkan jumlah hewan berdasarkan spesies (cat dan dog saja) dan jenis kelamin:
```sql
SELECT species, sex, COUNT(*) AS jumlah_hewan 
FROM hewan 
WHERE species IN ('cat', 'dog') 
GROUP BY species, sex;
```

6. Tampilkan jumlah hewan berdasarkan jenis kelamin yang diketahui saja:
```sql
SELECT sex, COUNT(*) AS jumlah_hewan 
FROM hewan 
WHERE sex IS NOT NULL 
GROUP BY sex;
```
  
### Berikan Kesimpulan Anda:

Terdapat beberapa **Query Filter** yang ditemukan pada tugas praktikum 4 :

- Operator `IN` digunakan untuk memfilter data yang terdapat pada list IN
- Operator `NOT IN` digunakan untuk memfilter data yang tidak terdapat pada list IN
- Operator `IS NULL` digunakan untuk menampilkan data dengan nilai data NULL
- Operator `IS NOT NULL` digunakan untuk menampilkan data dengan nilai data tidak NULL
- `COUNT` adalah perintah yang digunakan untuk menghitung jumlah baris suatu kolom pada tabel.
- `SUM` adalah perintah yang digunakan untuk menghitung jumlah nilai suatu kolom pada tabel.
- `AVG` adalah perintah yang digunakan untuk menghitung rata-rata dari nilai suatu kolom pada tabel.
- `MIN` adalah perintah yang digunakan untuk menampilkan nilai terkecil dari suatu kolom pada tabel.
- `MAX` adalah perintah yang digunakan untuk menampilkan nilai terbesar dari suatu kolom pada tabel.
- Klausa `GROUP BY` berfungsi untuk mengelompokkan data berdasarkan field tertentu.

## Documentation

All associated resources. are licensed under the [MIT License](https://mit-license.org/).
