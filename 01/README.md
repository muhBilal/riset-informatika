# Implementasi Sistem Audit Trail Aktivitas Pengguna pada SIMRS di Ngoerahsun WAC Bali

## 📌 Deskripsi
Proyek ini merupakan implementasi sistem **Audit Trail** pada **Sistem Informasi Manajemen Rumah Sakit (SIMRS) Ngoerahsun WAC Bali**.  
Audit Trail berfungsi untuk mencatat dan melacak seluruh aktivitas pengguna dalam sistem, guna meningkatkan **keamanan data, akuntabilitas pengguna, serta kepatuhan terhadap regulasi kesehatan** seperti **Permenkes No. 24 Tahun 2022** tentang rekam medis elektronik.

---

## 🎯 Tujuan Penelitian
1. Merancang dan mengimplementasikan sistem audit trail aktivitas pengguna pada SIMRS di Ngoerahsun WAC Bali.  
2. Meningkatkan transparansi, akuntabilitas, dan keamanan data melalui pencatatan aktivitas pengguna.  
3. Mengevaluasi efektivitas modul audit trail dalam mendukung kepatuhan regulasi dan standar keamanan informasi rumah sakit.  

---

## ❓ Rumusan Masalah
1. Bagaimana merancang modul audit trail yang dapat mencatat seluruh aktivitas pengguna pada SIMRS?  
2. Bagaimana audit trail dapat membantu meningkatkan keamanan data dan akuntabilitas pengguna dalam SIMRS?  
3. Apa dampak implementasi audit trail terhadap kepatuhan regulasi dan standar keamanan informasi?  

---

## 🧭 Metodologi
Metode pengembangan sistem yang digunakan adalah **Waterfall**, yang meliputi:  
1. **Analisis Kebutuhan** – Identifikasi kebutuhan pengguna dan regulasi terkait.  
2. **Desain Sistem** – Perancangan modul audit trail (skema database, flow aktivitas, dan integrasi dengan SIMRS).  
3. **Implementasi** – Pengembangan menggunakan **Laravel (PHP 8.2/8.3)** dengan basis data **PostgreSQL 14/17**.  
4. **Pengujian** – Uji fungsionalitas pencatatan log aktivitas.  
5. **Pemeliharaan** – Evaluasi efektivitas serta perbaikan berkelanjutan.  

---

## 📊 Ruang Lingkup
- Integrasi modul audit trail dengan SIMRS.  
- Pencatatan log aktivitas pengguna (login, insert, update, delete, view).  
- Monitoring perubahan data secara detail (*before & after value*).  
- Penyimpanan informasi tambahan (IP address, user agent, timestamp).  
- Analisis kepatuhan terhadap standar keamanan informasi (ISO 27001/COBIT 5).  

---

## 🛠️ Teknologi yang Digunakan
- **Backend**: Laravel 12.x (PHP 8.2/8.3)  
- **Database**: PostgreSQL 14/17  
- **Frontend**: Blade + Tailwind CSS  
- **DevOps**: Docker (PHP-Apache, Postgres)  
- **Mobile Integration**: Flutter (NgoerahSun WAC Mobile)  

---

## 📂 Struktur Penelitian
```bash
.
├── docs/                  # Dokumentasi penelitian (bab, jurnal, regulasi)
├── src/                   # Source code implementasi
│   ├── app/               # Core Laravel application
│   ├── database/          # Migrasi & seeders
│   ├── resources/         # Blade templates & assets
│   └── tests/             # Unit & feature testing
├── README.md              # Dokumentasi utama
└── LICENSE                # Lisensi proyek
