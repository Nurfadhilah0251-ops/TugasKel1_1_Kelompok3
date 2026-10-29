
# A3. Batasan Sistem

<!-- Penanggung jawab: [Nur Afifah] -->

Berikut adalah batasan-batasan sistem pada Layanan Assignment & Assessment di SPADA UMI-Kalam FIKOM UMI yang dikelompokkan ke dalam tiga kategori utama (teknologi, bisnis, dan operasional), beserta analisis dampaknya terhadap perancangan arsitektur perangkat lunak:

## 1. Batasan Teknologi (Technology Constraints)
* **Keterlibatan Infrastruktur Basis Data SPADA**: Sistem layanan tugas wajib terintegrasi dengan pangkalan data pusat SPADA UMI-Kalam yang sudah ada tanpa melakukan perombakan skema tabel inti yang dikelola oleh universitas.
* **Kapasitas Unggah Berkas Tugas**: Batasan ukuran maksimum untuk unggah berkas tugas mahasiswa (seperti laporan praktikum, dokumen kode .zip, atau laporan format PDF) dibatasi hingga 25 MB per dokumen guna mengoptimalkan kapasitas penyimpanan server dan kelancaran jaringan di lingkungan kampus.

### Dampak pada Arsitektur:
Arsitektur perangkat lunak harus mengimplementasikan lapisan API Gateway atau layanan wrapper khusus agar dapat melakukan sinkronisasi data pengumpulan tugas dengan basis data pusat secara aman tanpa melanggar batasan skema lama. Selain itu, diperlukan pemisahan modul penyimpanan (Object Storage) khusus untuk berkas tugas berukuran besar agar tidak membebani performa basis data relasional.

## 2. Batasan Bisnis (Business Constraints)
* **Kepatuhan Kalender Akademik Universitas**: Siklus pembuatan tugas, tenggat waktu (deadline), hingga penutupan pengisian nilai mutlak harus selaras dengan kalender akademik resmi Universitas Muslim Indonesia.
* **Standar Integritas Akademik**: Layanan wajib menerapkan sistem pemeriksaan kemiripan (similarity check) untuk mendeteksi plagiarisme antar-tugas mahasiswa sesuai dengan kode etik akademik di lingkungan FIKOM UMI.
### Dampak pada Arsitektur:
Sistem memerlukan modul penjadwalan otomatis (cron job / scheduler) yang terikat ketat dengan waktu server lokal universitas. Perancangan modul penilaian juga harus menyediakan fitur log audit (audit trail) untuk mencatat setiap perubahan nilai oleh dosen demi menjaga transparansi bisnis akademik.

## 3. Batasan Operasional (Operational Constraints)
* **Keterbatasan Bandwidth dan Lonjakan Akses (Peak Load)**: Sistem sering mengalami lonjakan trafik yang tinggi secara bersamaan ketika mendekati batas waktu (deadline) pengumpulan tugas akhir malam oleh mahasiswa.
* **Hak Akses Pengguna (Role-Based Access Control)**: Operasional sistem harus membatasi ketat hak akses antara mahasiswa (hanya bisa mengunggah dan melihat nilai sendiri), dosen (mengelola tugas dan memberi nilai), hingga administrator.
### Dampak Pada Arsitektur:
Penerapan load balancing dan mekanisme antrean unggahan (queue system) sangat diperlukan pada arsitektur server untuk mengantisipasi kegagalan sistem saat terjadi lonjakan akses bersamaan. Hak akses harus dikelola menggunakan token otentikasi yang aman (seperti JWT) untuk mencegah kebocoran data tugas mahasiswa lain.
