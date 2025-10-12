# Implementasi Modul Audit Trail pada SIMRS Ngoerahsun WAC Bali

## 🎯 Latar Belakang Masalah & Celah Penelitian (Problem & Research Gap)

Pengembangan sistem Audit Trail yang efektif merupakan tantangan krusial dalam keamanan sistem informasi kesehatan. Untuk memetakan kontribusi penelitian ini, dilakukan analisis mendalam terhadap berbagai literatur ilmiah terkini, baik dari jurnal internasional bereputasi maupun jurnal nasional terakreditasi.

### Tinjauan Penelitian Terdahulu (State-of-the-Art Review)

Tabel berikut merangkum penelitian-penelitian utama yang menjadi landasan dan pembanding dalam riset ini.

| No | Peneliti & Tahun | Judul Penelitian | Metode / Teknologi | Hasil Utama | Keterbatasan / Gap | Link Sumber |
|:---|:---|:---|:---|:---|:---|:---|
| 1 | Chen, J., et al. (2025) | Electronic Health Record Activity Changes Around New Decision Support Implementation | EHR Audit Logs, Topic Modeling | Audit log digunakan untuk memantau aktivitas pengguna pasca implementasi sistem baru. | Fokus pada analisis log, belum pada integrasi audit trail di sistem rumah sakit. | [JAMIA Open](https://doi.org/10.1093/jamiaopen/ooae073) |
| 2 | Kannampallil, T., et al. (2022) | Using Electronic Health Record Audit Log Data for Research | Data Analisis EHR Logs | Audit log dimanfaatkan untuk riset perilaku pengguna EHR. | Belum fokus pada sistem audit trail yang real-time dan terintegrasi. | [PMC](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8043694/) |
| 3 | Ullah, F., et al. (2024) | Blockchain-enabled EHR Access Auditing: Enhancing Data Security with Immutable Audit Trails | Blockchain, Smart Contract | Audit Trail berbasis blockchain meningkatkan keamanan dan transparansi. | Kompleksitas tinggi dan sulit diimplementasikan di SIMRS eksisting. | [Heliyon (Elsevier)](https://doi.org/10.1016/j.heliyon.2024.e25530) |
| 4 | Al-Khasawneh, M. A., et al. (2024) | A Secure Blockchain Framework for Healthcare Records Management Systems | Blockchain Framework | Menjamin keamanan data rekam medis melalui blockchain audit. | Tidak membahas integrasi dengan aplikasi SIMRS modern. | [PeerJ Comp. Sci.](https://doi.org/10.7717/peerj-cs.1793) |
| 5 | Li, H., et al. (2025) | Imputation of Missing Aggregate EHR Audit Log Data Across Organizations | Machine Learning, Data Quality | Meningkatkan kualitas audit log data lintas organisasi. | Fokus pada kelengkapan data, bukan pada audit trail di sistem lokal. | [J. Biomedical Informatics](https://doi.org/10.1016/j.jbi.2024.104683) |
| 6 | Tahir, N. U. A., et al. (2024) | Blockchain-Based Healthcare Records Management: A Framework for Adoption | Blockchain, MDPI Framework | Audit trail blockchain untuk adopsi keamanan data EHR. | Kompleksitas integrasi tinggi pada sistem non-blockchain. | [MDPI Technologies](https://doi.org/10.3390/technologies12030029) |
| 7 | Saputra, C. H. (2024) | Integrasi Audit Trail dan Teknik Clustering untuk Segmentasi dan Kategorisasi Aktivitas Log | Laravel, PHP, Clustering | Menerapkan audit trail dan analisis log dengan clustering untuk segmentasi aktivitas. | Belum diterapkan pada sistem rumah sakit atau regulasi kesehatan. | [JTIIK (SINTA 2)](https://doi.org/10.25126/jtiik.2024117621) |
| 8 | Rahmawati, N. (2023) | Desain Audit Trail Berbasis Blockchain untuk Keamanan Rekam Medis | Blockchain | Audit trail sulit dimanipulasi dan transparan. | Kompleksitas tinggi dan belum diujikan pada SIMRS lokal. | Local Research Archive |

### Analisis Kesenjangan (Gap Analysis)
Berdasarkan tinjauan di atas, ditemukan beberapa kesenjangan signifikan yang mendorong penelitian ini:

* **Kesenjangan Regulasi**: Sebagian besar penelitian global tidak mempertimbangkan konteks regulasi spesifik di Indonesia, yaitu **Permenkes No. 24 Tahun 2022**.
* **Kurangnya Integrasi**: Banyak solusi audit trail bersifat *standalone* atau berbasis teknologi kompleks (Blockchain), sehingga sulit diintegrasikan ke dalam SIMRS konvensional yang sudah berjalan.
* **Pencatatan yang Kurang Detail**: Implementasi yang ada seringkali hanya mencatat aktivitas dasar, tanpa merekam detail krusial seperti **nilai data sebelum dan sesudah perubahan** (`before-after values`).
* **Fokus Implementasi**: Riset di Indonesia masih terbatas pada level konseptual, bukan pada lingkungan rumah sakit regional yang aktif seperti di Bali.

---

## 💡 Solusi & Posisi Penelitian (Our Solution & Positioning)

Penelitian ini secara strategis mengisi celah tersebut dengan menawarkan solusi yang:

* ✅ **Terintegrasi Penuh**: Mengembangkan modul yang menjadi bagian inheren dari SIMRS eksisting (berbasis Laravel & PostgreSQL), memastikan implementasi yang mulus dan *real-time*.
* ✅ **Kepatuhan Regulasi**: Dirancang secara eksplisit untuk memenuhi mandat keamanan dalam **Permenkes No. 24/2022** serta mendukung standar global seperti **ISO 27001** dan **COBIT 5**.
* ✅ **Pencatatan Komprehensif**: Merekam jejak audit secara detail, mencakup **nilai sebelum-sesudah**, alamat IP, *user agent*, dan *timestamp* untuk setiap aktivitas CRUD dan login.
* ✅ **Implementasi Nyata**: Proyek ini bukan sekadar prototipe, melainkan implementasi langsung pada studi kasus **SIMRS Ngoerahsun WAC Bali**.

---

## 🗺️ Peta Konsep Penelitian (Research Mind Map)

-- 


## 🏆 Kontribusi Utama Penelitian (Key Contributions)

1.  **Pengembangan Modul Audit Trail Terintegrasi**: Menyediakan modul yang siap pakai untuk SIMRS berbasis Laravel dan PostgreSQL.
2.  **Peningkatan Keamanan Data Medis**: Mengimplementasikan pencatatan detail (`before-after value`, IP, perangkat) untuk meningkatkan akuntabilitas dan kemampuan audit.
3.  **Model Kepatuhan Regulasi**: Menjadi rujukan implementasi teknis untuk memenuhi kewajiban Permenkes No. 24/2022 bagi fasilitas kesehatan di Indonesia.

--- 

## 🛠️ Teknologi yang Digunakan (Tech Stack)

* **Framework**: Laravel (PHP 8.3)
* **Database**: PostgreSQL
* **Bahasa Pemrograman**: PHP