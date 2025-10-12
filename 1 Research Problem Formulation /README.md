# **BAB I – PERUMUSAN MASALAH PENELITIAN**

## **1.1 Latar Belakang**

Perkembangan teknologi informasi dalam bidang kesehatan telah mendorong transformasi sistem pelayanan rumah sakit menuju digitalisasi, salah satunya melalui penerapan **Sistem Informasi Manajemen Rumah Sakit (SIMRS)**. SIMRS berperan penting dalam mengelola data pasien, rekam medis elektronik, administrasi, hingga laporan manajemen secara terintegrasi. Namun, seiring meningkatnya kompleksitas dan jumlah pengguna, muncul tantangan terkait **keamanan data, akuntabilitas pengguna, serta kepatuhan terhadap regulasi kesehatan**.

Salah satu aspek krusial dalam menjamin keamanan dan keandalan sistem informasi rumah sakit adalah penerapan **Audit Trail** — mekanisme pencatatan otomatis terhadap seluruh aktivitas pengguna dalam sistem. Audit Trail memungkinkan pihak manajemen untuk melacak siapa yang melakukan tindakan tertentu, kapan dilakukan, serta perubahan apa yang terjadi pada data. Hal ini penting untuk mencegah penyalahgunaan akses, manipulasi data medis, serta memastikan setiap aktivitas terekam secara transparan dan dapat diaudit.

Penerapan Audit Trail juga mendukung kepatuhan terhadap regulasi **Permenkes No. 24 Tahun 2022 tentang Rekam Medis Elektronik**, yang mewajibkan fasilitas pelayanan kesehatan untuk menjaga integritas, keamanan, dan kerahasiaan data rekam medis. Dengan adanya modul Audit Trail, SIMRS dapat memperkuat sistem pengawasan internal serta meningkatkan kepercayaan terhadap sistem digital yang digunakan.

Berdasarkan permasalahan tersebut, penelitian ini dilakukan di **SIMRS Ngoerahsun WAC Bali**, dengan tujuan untuk merancang dan mengimplementasikan **sistem Audit Trail aktivitas pengguna** yang terintegrasi dengan modul SIMRS yang telah ada, menggunakan **framework Laravel (PHP 8.3)** dan **PostgreSQL**, serta dikembangkan dengan pendekatan **Agile-Scrum** guna memastikan fleksibilitas, kolaborasi tim, dan peningkatan berkelanjutan terhadap fitur keamanan sistem.

---

## **1.2 Rumusan Masalah**

Berdasarkan latar belakang di atas, maka rumusan masalah dalam penelitian ini adalah sebagai berikut:

1. Bagaimana merancang dan mengimplementasikan sistem Audit Trail yang mampu mencatat seluruh aktivitas pengguna pada SIMRS Ngoerahsun WAC Bali?
2. Bagaimana penerapan Audit Trail dapat meningkatkan keamanan data serta akuntabilitas pengguna dalam lingkungan SIMRS?
3. Bagaimana pendekatan **Agile-Scrum** dapat mendukung efektivitas pengembangan sistem Audit Trail berbasis Laravel?

---

## **1.3 Tujuan Penelitian**

Tujuan dari penelitian ini adalah:

1. Merancang dan mengimplementasikan sistem Audit Trail aktivitas pengguna pada SIMRS Ngoerahsun WAC Bali menggunakan **Laravel (PHP 8.3)** dan **PostgreSQL**.
2. Meningkatkan transparansi, akuntabilitas, dan keamanan data melalui pencatatan serta pelacakan aktivitas pengguna secara otomatis di level aplikasi Laravel.
3. Mengevaluasi efektivitas penerapan Audit Trail terhadap peningkatan keamanan data dan kepatuhan regulasi rumah sakit.

---

## **1.4 Manfaat Penelitian**

Adapun manfaat yang diharapkan dari penelitian ini adalah sebagai berikut:

### 1. **Manfaat Akademik**

Sebagai referensi dan pengembangan ilmu pengetahuan di bidang **Sistem Informasi Kesehatan**, khususnya penerapan **Audit Trail berbasis framework Laravel dan PostgreSQL** dengan pendekatan pengembangan **Agile-Scrum**.

### 2. **Manfaat Praktis**

Sebagai acuan bagi pihak **RS Ngoerahsun WAC Bali** dalam meningkatkan keamanan dan akuntabilitas sistem informasi melalui penerapan modul Audit Trail yang terintegrasi langsung ke dalam kode sumber SIMRS.

### 3. **Manfaat Regulatif dan Keamanan Data**

Mendukung kepatuhan terhadap regulasi **Permenkes No. 24 Tahun 2022** terkait pengelolaan rekam medis elektronik, serta memperkuat prinsip **integritas, kerahasiaan, dan keaslian data** melalui pencatatan otomatis aktivitas pengguna.

---

## **1.5 Ruang Lingkup Penelitian**

Penelitian ini dibatasi pada implementasi modul Audit Trail dalam lingkup **SIMRS Ngoerahsun WAC Bali**, dengan ruang lingkup sebagai berikut:

* Integrasi modul Audit Trail langsung ke dalam sistem SIMRS berbasis Laravel.
* Pencatatan aktivitas pengguna meliputi login, create, update, delete, dan view data.
* Penyimpanan informasi tambahan seperti **alamat IP, user agent, dan timestamp** setiap aktivitas.
* Monitoring perubahan data secara detail (nilai sebelum dan sesudah).
* Implementasi dilakukan langsung melalui kode Laravel tanpa menggunakan framework keamanan tambahan seperti COBIT atau ISO framework.
* Pengembangan sistem dilakukan menggunakan pendekatan **Agile-Scrum**.

---

## **1.6 Metodologi Penelitian (Gambaran Umum)**

Penelitian ini menggunakan pendekatan **Agile-Scrum**, yaitu metode pengembangan sistem yang berorientasi pada kolaborasi tim, fleksibilitas terhadap perubahan, dan peningkatan berkelanjutan melalui iterasi yang disebut **Sprint**.

Adapun tahapan metodologi dalam penelitian ini meliputi:

1. **Product Backlog Creation**
   Menentukan daftar kebutuhan sistem (fitur Audit Trail, struktur data, dan kebutuhan keamanan) berdasarkan analisis terhadap modul SIMRS dan kebutuhan rumah sakit.

2. **Sprint Planning**
   Menentukan prioritas fitur yang akan dikembangkan dalam tiap sprint serta mendefinisikan target hasil pada setiap iterasi pengembangan.

3. **Sprint Implementation**
   Melakukan pengembangan sistem menggunakan **Laravel (PHP 8.3)** dan **PostgreSQL**, meliputi pembuatan model, middleware, event listener, serta logging aktivitas pengguna.

4. **Daily Scrum**
   Melakukan komunikasi dan pembaruan harian untuk membahas progres, hambatan teknis, dan rencana tindak lanjut dalam pengembangan modul Audit Trail.

5. **Sprint Review & Testing**
   Melakukan pengujian terhadap hasil sprint, termasuk pengujian fungsionalitas pencatatan aktivitas dan validasi integrasi dengan sistem SIMRS.

6. **Sprint Retrospective**
   Mengevaluasi hasil sprint yang telah diselesaikan, mengidentifikasi area perbaikan, dan menyusun rencana peningkatan fitur untuk sprint berikutnya.

Pendekatan **Agile-Scrum** memungkinkan penelitian ini menghasilkan sistem Audit Trail yang adaptif, efisien, dan terintegrasi langsung dengan SIMRS tanpa memerlukan framework tambahan di luar Laravel, sehingga mendukung keamanan data serta akuntabilitas pengguna secara optimal.

---