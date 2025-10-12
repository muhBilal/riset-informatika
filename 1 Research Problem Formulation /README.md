# **BAB I – PERUMUSAN MASALAH PENELITIAN**

## **1.1 Latar Belakang**

Perkembangan teknologi informasi dalam bidang kesehatan telah mendorong transformasi sistem pelayanan rumah sakit menuju digitalisasi, salah satunya melalui penerapan **Sistem Informasi Manajemen Rumah Sakit (SIMRS)**. SIMRS berperan penting dalam mengelola data pasien, rekam medis elektronik, administrasi, hingga laporan manajemen secara terintegrasi. Namun, seiring meningkatnya kompleksitas dan jumlah pengguna, muncul tantangan terkait **keamanan data, akuntabilitas pengguna, serta kepatuhan terhadap regulasi kesehatan**.

Salah satu aspek krusial dalam menjamin keamanan dan keandalan sistem informasi rumah sakit adalah penerapan **Audit Trail** — mekanisme pencatatan otomatis terhadap seluruh aktivitas pengguna dalam sistem. Audit Trail memungkinkan pihak manajemen untuk melacak siapa yang melakukan tindakan tertentu, kapan dilakukan, serta perubahan apa yang terjadi pada data. Hal ini penting untuk mencegah penyalahgunaan akses, manipulasi data medis, serta memastikan setiap aktivitas terekam secara transparan dan dapat diaudit.

Penerapan Audit Trail juga mendukung kepatuhan terhadap regulasi **Permenkes No. 24 Tahun 2022 tentang Rekam Medis Elektronik**, yang mewajibkan fasilitas pelayanan kesehatan untuk menjaga integritas, keamanan, dan kerahasiaan data rekam medis. Dengan adanya modul Audit Trail, SIMRS dapat memperkuat sistem pengawasan internal serta meningkatkan kepercayaan terhadap sistem digital yang digunakan.

Berdasarkan permasalahan tersebut, penelitian ini dilakukan di **SIMRS Ngoerahsun WAC Bali**, dengan tujuan untuk merancang dan mengimplementasikan **sistem Audit Trail aktivitas pengguna** yang terintegrasi dengan modul SIMRS yang telah ada, menggunakan **framework Laravel (PHP 8.3)** dan basis data **PostgreSQL**, guna meningkatkan keamanan, akuntabilitas, serta kepatuhan terhadap regulasi yang berlaku.

---

## **1.2 Rumusan Masalah**

Berdasarkan latar belakang di atas, maka rumusan masalah dalam penelitian ini adalah sebagai berikut:

1. Bagaimana merancang dan mengimplementasikan sistem Audit Trail yang mampu mencatat seluruh aktivitas pengguna pada SIMRS Ngoerahsun WAC Bali?
2. Bagaimana penerapan Audit Trail dapat meningkatkan keamanan data serta akuntabilitas pengguna dalam lingkungan SIMRS?
3. Bagaimana dampak implementasi sistem Audit Trail terhadap kepatuhan SIMRS terhadap regulasi dan standar keamanan informasi yang berlaku?

---

## **1.3 Tujuan Penelitian**

Tujuan dari penelitian ini adalah:

1. Merancang dan mengimplementasikan sistem Audit Trail aktivitas pengguna pada SIMRS Ngoerahsun WAC Bali.
2. Meningkatkan transparansi, akuntabilitas, dan keamanan data melalui pencatatan serta pelacakan aktivitas pengguna.
3. Mengevaluasi efektivitas modul Audit Trail dalam mendukung kepatuhan terhadap regulasi dan standar keamanan informasi rumah sakit.

---

## **1.4 Manfaat Penelitian**

Adapun manfaat yang diharapkan dari penelitian ini adalah sebagai berikut:

### 1. **Manfaat Akademik**

Sebagai referensi dan pengembangan ilmu pengetahuan di bidang **Sistem Informasi Kesehatan**, khususnya mengenai penerapan Audit Trail dalam sistem manajemen rumah sakit berbasis Laravel dan PostgreSQL.

### 2. **Manfaat Praktis**

Sebagai acuan bagi pihak **RS Ngoerahsun WAC Bali** dalam meningkatkan keamanan dan akuntabilitas sistem informasi melalui penerapan modul Audit Trail yang terintegrasi dengan SIMRS.

### 3. **Manfaat Regulatif dan Keamanan Data**

Mendukung kepatuhan terhadap regulasi **Permenkes No. 24 Tahun 2022** serta penerapan prinsip-prinsip keamanan informasi berdasarkan **ISO 27001** dan **COBIT 5**.

---

## **1.5 Ruang Lingkup Penelitian**

Penelitian ini dibatasi pada implementasi modul Audit Trail dalam lingkup **SIMRS Ngoerahsun WAC Bali**, dengan ruang lingkup sebagai berikut:

* Integrasi modul Audit Trail dengan sistem SIMRS berbasis Laravel.
* Pencatatan aktivitas pengguna meliputi login, create, update, delete, dan view data.
* Penyimpanan informasi tambahan seperti **alamat IP, user agent, dan timestamp** setiap aktivitas.
* Monitoring perubahan data secara detail (nilai sebelum dan sesudah).
* Analisis efektivitas sistem Audit Trail terhadap standar keamanan informasi dan kepatuhan regulasi.

---

## **1.6 Metodologi Penelitian (Gambaran Umum)**

Penelitian ini menggunakan metode pengembangan sistem **Waterfall**, dengan tahapan sebagai berikut:

1. **Analisis Kebutuhan** – Mengidentifikasi kebutuhan pengguna, regulasi, serta aspek keamanan data.
2. **Desain Sistem** – Merancang struktur database, flow aktivitas, dan integrasi modul Audit Trail dengan SIMRS.
3. **Implementasi** – Mengembangkan sistem menggunakan Laravel (PHP 8.3) dan PostgreSQL.
4. **Pengujian** – Melakukan pengujian fungsionalitas untuk memastikan seluruh aktivitas pengguna terekam dengan benar.
5. **Pemeliharaan dan Evaluasi** – Menilai efektivitas modul Audit Trail serta melakukan perbaikan berkelanjutan berdasarkan hasil pengujian.

--- 