# Sistem Audit Trail SIMRS Ngoerahsun WAC Bali

## Daftar Isi
- [3.1 Pendekatan Penelitian](#31-pendekatan-penelitian)
- [3.2 Metode Pengembangan Sistem](#32-metode-pengembangan-sistem)
- [3.3 Lokasi dan Waktu Penelitian](#33-lokasi-dan-waktu-penelitian)
- [3.4 Sumber Data Penelitian](#34-sumber-data-penelitian)
- [3.5 Analisis Data](#35-analisis-data)
- [3.6 Indikator Keberhasilan](#36-indikator-keberhasilan)

---

## 3.1 Pendekatan Penelitian

Penelitian ini menggunakan pendekatan **penelitian terapan (applied research)** yang bertujuan untuk menghasilkan solusi konkret terhadap permasalahan keamanan data dan akuntabilitas pengguna pada **Sistem Informasi Manajemen Rumah Sakit (SIMRS)** di **Ngoerahsun WAC Bali**.
Hasil penelitian diharapkan dapat langsung diimplementasikan dan memberikan dampak nyata terhadap peningkatan kualitas sistem informasi rumah sakit.

Metode pengembangan yang digunakan adalah **metode Waterfall**, karena setiap tahap dalam proses pengembangan sistem dilakukan secara berurutan dan sistematis, mulai dari analisis kebutuhan hingga pemeliharaan sistem.

---

## 3.2 Metode Pengembangan Sistem

Tahapan pengembangan sistem dengan model **Waterfall** terdiri dari lima fase utama, yaitu:

1. **Analisis Kebutuhan (Requirement Analysis)**
2. **Perancangan Sistem (System Design)**
3. **Implementasi (Implementation)**
4. **Pengujian (Testing)**
5. **Pemeliharaan (Maintenance)**

---

### 3.2.1 Analisis Kebutuhan

Tahap ini dilakukan untuk mengidentifikasi kebutuhan sistem Audit Trail serta menentukan ruang lingkup fungsional dan non-fungsional.
Analisis dilakukan melalui **observasi langsung** terhadap sistem SIMRS yang berjalan dan **wawancara dengan staf IT rumah sakit**.

#### Kebutuhan Fungsional

1. Sistem mampu mencatat aktivitas pengguna seperti **login, tambah data, ubah data, hapus data, dan akses tampilan data**.
2. Setiap aktivitas harus mencatat atribut: **user_id, nama pengguna, peran (role), modul sistem, jenis aktivitas, waktu (timestamp), alamat IP, dan user agent**.
3. Perubahan data dicatat secara detail melalui perbandingan nilai lama dan baru (*before–after*).
4. Data log dapat ditampilkan dalam bentuk tabel dan laporan yang dapat difilter berdasarkan tanggal, pengguna, atau jenis aktivitas.
5. Log aktivitas disimpan secara permanen dan tidak dapat dihapus tanpa izin administratif.

#### Kebutuhan Non-Fungsional

1. Sistem dikembangkan dengan **Laravel (PHP 8.3)** dan **PostgreSQL 17** sebagai basis data.
2. Mekanisme pencatatan log dilakukan secara **manual melalui middleware atau controller**, bukan melalui model otomatis.
3. Audit Trail diintegrasikan dengan modul SIMRS tanpa mengubah struktur utama sistem.
4. Keamanan akses diterapkan melalui autentikasi pengguna dan pembatasan hak akses berdasarkan peran.
5. Sistem harus sesuai dengan ketentuan keamanan data dalam **Permenkes No. 24 Tahun 2022** dan prinsip **ISO 27001**.

---

### 3.2.2 Perancangan Sistem

Perancangan sistem meliputi desain arsitektur, struktur basis data, dan rancangan antarmuka pengguna.

#### a. Arsitektur Sistem

Arsitektur sistem dirancang agar modul Audit Trail dapat menerima input log dari berbagai modul SIMRS yang sudah ada (seperti Admission, EMR, MCU, dan lainnya).
Setiap aktivitas pengguna pada modul tersebut akan dikirim ke **tabel audit_logs** melalui fungsi pencatatan di middleware atau controller utama.

```
+---------------------------+
|         Pengguna          |
+-------------+-------------+
              |
              v
+---------------------------+
|     Modul SIMRS (EMR,     |
|   Admission, MCU, dll)    |
+-------------+-------------+
              |
              v
+---------------------------+
|  Middleware / Controller  |
|     Pencatatan Log        |
+-------------+-------------+
              |
              v
+---------------------------+
|     Database Audit Log    |
|       (PostgreSQL)        |
+-------------+-------------+
              |
              v
+---------------------------+
|  Dashboard Audit & Report |
+---------------------------+
```

#### b. Perancangan Basis Data

Struktur basis data berfokus pada satu tabel utama bernama **`audit_logs`**, yang menyimpan seluruh aktivitas pengguna.
Adapun atribut utamanya antara lain:

| Nama Kolom | Tipe Data | Keterangan |
| ---------- | --------- | ---------- |
| id | BIGSERIAL | Primary key |
| user_id | INTEGER | ID pengguna yang melakukan aktivitas |
| role | VARCHAR(50) | Peran pengguna (admin, dokter, perawat, pasien) |
| module | VARCHAR(100) | Modul sistem yang diakses |
| action | VARCHAR(50) | Jenis aktivitas (login, insert, update, delete, view) |
| old_values | JSONB | Nilai sebelum perubahan (jika ada) |
| new_values | JSONB | Nilai sesudah perubahan (jika ada) |
| ip_address | INET | Alamat IP pengguna |
| user_agent | TEXT | Informasi perangkat/browser |
| created_at | TIMESTAMP | Waktu aktivitas tercatat |

#### c. Perancangan Antarmuka Pengguna

Antarmuka pengguna dirancang agar mudah digunakan oleh administrator dan auditor internal.
Tampilan utama sistem audit trail meliputi:

- Daftar aktivitas pengguna secara kronologis.
- Filter berdasarkan **tanggal, pengguna, dan jenis aksi**.
- Tampilan detail aktivitas (menampilkan perbandingan data sebelum dan sesudah).
- Laporan yang dapat diunduh dalam format **PDF** untuk audit berkala.

---

### 3.2.3 Implementasi

Tahapan implementasi dilakukan dengan mengintegrasikan sistem Audit Trail ke dalam **lingkungan kerja SIMRS Ngoerahsun WAC Bali**.
Proses pencatatan dilakukan melalui middleware yang secara otomatis menyimpan log aktivitas ke dalam tabel `audit_logs` setiap kali pengguna melakukan aksi pada sistem.

#### Mekanisme Utama Implementasi

1. **Middleware Logging** → memantau setiap request HTTP yang dikirim pengguna, mencatat informasi terkait aktivitas.
2. **Controller Hooks** → menyimpan log tambahan untuk aktivitas penting seperti perubahan data pasien, tindakan medis, atau akses rekam medis.
3. **Penyimpanan Data Log** → semua informasi dikirim ke database PostgreSQL dan disimpan dalam format JSONB.
4. **Dashboard Audit** → menampilkan data log yang sudah tersimpan untuk keperluan analisis dan audit.

Integrasi dilakukan tanpa mengubah struktur dasar modul SIMRS, sehingga sistem audit trail dapat berfungsi sebagai **komponen tambahan (plug-in module)** yang ringan dan mudah dipelihara.

---

### 3.2.4 Pengujian Sistem

Pengujian dilakukan dengan metode **Black Box Testing**, yaitu menguji fungsi-fungsi sistem tanpa melihat kode sumber.
Tujuan pengujian adalah memastikan bahwa sistem audit trail mampu mencatat seluruh aktivitas pengguna secara benar dan konsisten.

| No | Skenario Uji | Kondisi Awal | Hasil yang Diharapkan | Status |
| :---: | :--- | :--- | :--- | :--- |
| 1 | Pengguna login ke sistem | User valid | Log aktivitas login tersimpan di tabel audit | ✔ |
| 2 | Pengguna menambah data pasien | Form input pasien baru | Aktivitas `create` terekam dengan data baru | ✔ |
| 3 | Pengguna mengubah data pasien | Data pasien tersedia | Log `update` menyimpan before-after value | ✔ |
| 4 | Pengguna menghapus data | Data tersedia | Log `delete` menyimpan data yang dihapus | ✔ |
| 5 | Pengguna melihat data | Akses menu pasien | Aktivitas `view` tercatat dengan IP dan user agent | ✔ |

Hasil pengujian menunjukkan bahwa seluruh fungsi utama pencatatan log berjalan sesuai harapan dan tidak menyebabkan gangguan pada performa sistem utama SIMRS.

---

### 3.2.5 Pemeliharaan Sistem

Tahap pemeliharaan dilakukan untuk memastikan sistem Audit Trail tetap berfungsi optimal dan aman.
Kegiatan meliputi:

1. **Pembersihan dan pengarsipan log** berdasarkan periode tertentu (misalnya 6 bulan sekali).
2. **Backup rutin** database audit ke server cadangan.
3. **Pemantauan performa sistem** untuk menghindari overload penyimpanan log.
4. **Evaluasi periodik** efektivitas audit trail dan kepatuhan terhadap kebijakan rumah sakit.

---

## 3.3 Lokasi dan Waktu Penelitian

Penelitian dilaksanakan di **RS Ngoerahsun WAC Bali**, dengan objek penelitian berupa sistem **SIMRS internal** yang digunakan oleh tenaga medis dan staf administrasi.
Waktu pelaksanaan penelitian berlangsung selama **18 minggu**, mulai dari tahap analisis, pengembangan, implementasi, pengujian, hingga pelaporan akhir.

---

## 3.4 Sumber Data Penelitian

**Data Primer:**
Hasil observasi langsung terhadap aktivitas pengguna sistem dan wawancara dengan staf IT serta manajemen rumah sakit.

**Data Sekunder:**
Dokumen kebijakan internal, laporan penggunaan SIMRS, literatur terkait audit trail, serta peraturan pemerintah seperti **Permenkes No. 24 Tahun 2022**.

---

## 3.5 Analisis Data

Analisis dilakukan dengan dua pendekatan:

**Analisis Kualitatif:**
Menilai pemahaman dan persepsi pengguna terhadap sistem audit trail melalui wawancara dan observasi.

**Analisis Kuantitatif:**
Mengukur jumlah log yang tercatat, frekuensi aktivitas per pengguna, serta tingkat keberhasilan pencatatan aktivitas berdasarkan hasil pengujian sistem.

Hasil analisis digunakan untuk mengevaluasi efektivitas sistem audit trail dalam mendukung keamanan dan akuntabilitas SIMRS.

---

## 3.6 Indikator Keberhasilan

Sistem Audit Trail dianggap berhasil apabila memenuhi indikator berikut:

1. Semua aktivitas pengguna terekam secara otomatis dan lengkap.
2. Data log tidak dapat dihapus atau dimodifikasi tanpa otorisasi.
3. Sistem tidak memengaruhi kinerja SIMRS secara signifikan.
4. Laporan audit dapat dihasilkan secara berkala dan digunakan untuk keperluan evaluasi keamanan.

---