Siap, Bilal 👍
Berikut versi **revisi penuh BAB III – Metodologi Penelitian** yang sudah **disesuaikan dengan metode Agile-Scrum** (bukan Waterfall), **berbasis implementasi langsung di Laravel + PostgreSQL**, dan tetap **mengacu pada konteks nyata di SIMRS Ngoerahsun WAC Bali**.
Seluruh bagian sudah diubah agar konsisten dengan pendekatan iteratif Agile-Scrum tanpa kehilangan struktur ilmiah.

---

# **BAB III – METODOLOGI PENELITIAN**

## **3.1 Pendekatan Penelitian**

Penelitian ini menggunakan pendekatan **penelitian terapan (applied research)** yang bertujuan menghasilkan solusi konkret terhadap permasalahan keamanan data dan akuntabilitas pengguna pada **Sistem Informasi Manajemen Rumah Sakit (SIMRS)** di **Ngoerahsun WAC Bali**.
Hasil penelitian diharapkan dapat langsung diimplementasikan dan memberikan dampak nyata terhadap peningkatan kualitas serta keamanan sistem informasi rumah sakit.

Metode pengembangan sistem yang digunakan adalah **metode Agile-Scrum**, karena pendekatan ini bersifat **iteratif, kolaboratif, dan adaptif** terhadap perubahan kebutuhan selama proses pengembangan. Dengan Scrum, setiap fungsi sistem dikembangkan dalam siklus singkat yang disebut **Sprint**, sehingga tim dapat melakukan evaluasi dan peningkatan berkelanjutan pada modul **Audit Trail** yang terintegrasi dengan SIMRS.

---

## **3.2 Metode Pengembangan Sistem**

Tahapan pengembangan sistem dengan pendekatan **Agile-Scrum** meliputi beberapa aktivitas utama berikut:

1. **Product Backlog Creation**
2. **Sprint Planning**
3. **Sprint Execution (Implementation & Testing)**
4. **Daily Scrum Meeting**
5. **Sprint Review & Retrospective**

---

### **3.2.1 Product Backlog Creation**

Tahap awal ini dilakukan untuk mengidentifikasi kebutuhan sistem dan menyusunnya dalam daftar prioritas fitur yang disebut **product backlog**.
Backlog disusun berdasarkan hasil **observasi sistem SIMRS**, **wawancara dengan staf IT**, dan **analisis regulasi Permenkes No. 24 Tahun 2022**.

#### **Kebutuhan Fungsional**

1. Sistem mencatat aktivitas pengguna seperti **login, create, update, delete, dan view data**.
2. Setiap log aktivitas menyimpan: **user_id, nama pengguna, peran (role), modul, jenis aktivitas, timestamp, alamat IP, dan user agent**.
3. Perubahan data dicatat secara rinci dengan perbandingan nilai lama dan baru (*before–after*).
4. Data log dapat difilter berdasarkan **tanggal, pengguna, atau jenis aktivitas** serta diekspor ke PDF.
5. Log disimpan secara permanen dan tidak dapat dihapus tanpa hak administratif.

#### **Kebutuhan Non-Fungsional**

1. Sistem dikembangkan dengan **Laravel (PHP 8.3)** dan **PostgreSQL 17**.
2. Mekanisme logging dibuat **langsung di kode aplikasi** (middleware / controller), tanpa library eksternal.
3. Audit Trail terintegrasi dengan modul SIMRS yang sudah ada tanpa mengubah struktur utamanya.
4. Autentikasi dan otorisasi berbasis peran diterapkan untuk membatasi akses.
5. Pengelolaan data log mengikuti prinsip keamanan informasi pada **Permenkes No. 24 Tahun 2022** dan praktik dasar **ISO 27001**.

---

### **3.2.2 Sprint Planning**

Setelah backlog disusun, tahap berikutnya adalah merencanakan pekerjaan dalam **Sprint** berdurasi ± 2 minggu per iterasi.
Pada tahap ini ditentukan:

* **Tujuan Sprint** (fitur yang akan diselesaikan, misalnya modul pencatatan login atau tampilan dashboard audit).
* **Tugas tim pengembang** (developer, tester, dan product owner).
* **Kriteria penerimaan (acceptance criteria)** untuk tiap fitur.

---

### **3.2.3 Sprint Execution (Implementation & Testing)**

Tahap ini meliputi kegiatan pengembangan dan pengujian pada setiap sprint.

#### **a. Implementasi Sistem**

1. **Middleware Logging** — mendeteksi setiap request HTTP dan mencatat aktivitas pengguna.
2. **Controller Hooks** — menyimpan log tambahan untuk operasi CRUD pada modul seperti EMR, Admission, dan MCU.
3. **Penyimpanan Data Log** — data disimpan di tabel `audit_logs` (PostgreSQL) dalam format JSONB.
4. **Dashboard Audit** — menampilkan hasil pencatatan secara kronologis dan dapat difilter.

Integrasi dilakukan sebagai **modul tambahan (plug-in)** di dalam SIMRS, tanpa memodifikasi struktur utama.

#### **b. Desain Basis Data**

| Kolom      | Tipe Data    | Keterangan                  |
| ---------- | ------------ | --------------------------- |
| id         | BIGSERIAL    | Primary key                 |
| user_id    | INTEGER      | ID pengguna                 |
| role       | VARCHAR(50)  | Peran pengguna              |
| module     | VARCHAR(100) | Modul SIMRS                 |
| action     | VARCHAR(50)  | Jenis aktivitas             |
| old_values | JSONB        | Nilai sebelum perubahan     |
| new_values | JSONB        | Nilai sesudah perubahan     |
| ip_address | INET         | Alamat IP                   |
| user_agent | TEXT         | Informasi perangkat/browser |
| created_at | TIMESTAMP    | Waktu aktivitas             |

#### **c. Desain Antarmuka**

Fitur utama antarmuka:

* Tabel aktivitas pengguna (urut kronologis).
* Filter tanggal / user / jenis aksi.
* Tampilan detail before–after.
* Laporan PDF berkala untuk audit.

---

### **3.2.4 Daily Scrum Meeting**

Selama sprint berlangsung, dilakukan pertemuan singkat setiap hari (maks. 15 menit) untuk:

* Melaporkan progres pengembangan.
* Mengidentifikasi hambatan teknis.
* Menentukan langkah berikutnya agar sprint tetap sesuai rencana.

---

### **3.2.5 Sprint Review dan Retrospective**

Setiap akhir sprint dilakukan dua kegiatan:

1. **Sprint Review** – menampilkan hasil pengembangan kepada *product owner* (atau tim IT RS) untuk memperoleh umpan balik.
2. **Sprint Retrospective** – mengevaluasi proses kerja sprint sebelumnya untuk peningkatan efektivitas sprint selanjutnya.

---

### **3.2.6 Pengujian Sistem**

Pengujian menggunakan **Black Box Testing**, fokus pada fungsi sistem tanpa meninjau kode sumber.

|  No | Skenario Uji       | Kondisi Awal  | Hasil Diharapkan                       | Status |
| :-: | ------------------ | ------------- | -------------------------------------- | :----: |
|  1  | Login pengguna     | User valid    | Aktivitas login tersimpan              |    ✔   |
|  2  | Tambah data pasien | Form baru     | Log `create` menyimpan data baru       |    ✔   |
|  3  | Ubah data pasien   | Data tersedia | Log `update` menyimpan before–after    |    ✔   |
|  4  | Hapus data         | Data tersedia | Log `delete` menyimpan data terhapus   |    ✔   |
|  5  | Lihat data         | Menu pasien   | Log `view` menyimpan IP dan user agent |    ✔   |

---

### **3.2.7 Pemeliharaan Sistem**

Kegiatan pemeliharaan meliputi:

1. **Backup dan arsip log** setiap periode tertentu.
2. **Monitoring kinerja database** untuk mencegah penumpukan data.
3. **Peningkatan fitur** berdasarkan hasil retrospektif sprint.
4. **Audit internal rutin** untuk memastikan integritas data log.

---

## **3.3 Lokasi dan Waktu Penelitian**

Penelitian dilakukan di **RS Ngoerahsun WAC Bali**, dengan objek sistem **SIMRS internal** yang digunakan tenaga medis dan staf administrasi.
Durasi penelitian berlangsung selama **18 minggu**, mencakup tahap analisis, pengembangan iteratif (beberapa sprint), pengujian, dan pelaporan akhir.

---

## **3.4 Sumber Data Penelitian**

**Data Primer :**
Hasil observasi langsung terhadap aktivitas pengguna SIMRS serta wawancara dengan staf IT dan manajemen RS.

**Data Sekunder :**
Dokumen kebijakan internal, log aktivitas sebelumnya, literatur terkait Audit Trail, serta peraturan pemerintah seperti **Permenkes No. 24 Tahun 2022**.

---

## **3.5 Analisis Data**

* **Analisis Kualitatif :** menilai persepsi pengguna terhadap kemudahan dan manfaat modul Audit Trail melalui wawancara dan observasi.
* **Analisis Kuantitatif :** mengukur jumlah log tercatat, tingkat keberhasilan pencatatan, dan performa sistem sebelum–sesudah implementasi.

---

## **3.6 Indikator Keberhasilan**

Sistem Audit Trail dinilai berhasil apabila:

1. Seluruh aktivitas pengguna tercatat otomatis dan lengkap.
2. Data log tidak dapat diubah atau dihapus tanpa otorisasi.
3. Performa SIMRS tidak menurun signifikan.
4. Laporan audit dapat dihasilkan secara berkala.
5. Tim pengembang mampu melakukan iterasi peningkatan melalui setiap sprint.

---

Apakah kamu mau aku bantu lanjutkan **BAB IV – Hasil dan Implementasi Agile-Scrum** biar nyambung dari struktur ini (misalnya dengan tabel backlog, pembagian sprint, dan hasil pengujian tiap sprint)?
