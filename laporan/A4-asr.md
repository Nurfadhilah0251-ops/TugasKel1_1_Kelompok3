# A4. Kebutuhan Signifikan (ASR)

<!-- Penanggung jawab: [Nur Afifah] -->

Berikut adalah draf untuk bagian ASR (Architecturally Significant Requirements di lingkungan FIKOM UMI:

## 1. ASR 1: Kinerja dan Penanganan Lonjakan Beban (Performance Efficiency)
* **Pernyataan Kebutuhan:** Pada periode pengumpulan tugas akhir mata kuliah atau menjelang batas waktu (deadline) pengiriman berkas, sistem harus mampu menangani hingga 500 mahasiswa dan dosen yang mengakses secara bersamaan, dengan waktu muat halaman web rata-rata kurang dari 3 detik.
* **Alasan Pengaruh pada Arsitektur:** Kebutuhan ini sangat memengaruhi desain arsitektur karena lonjakan akses secara simultan berpotensi menyebabkan bottleneck pada server web dan basis data relasional pusat SPADA UMI-Kalam. Oleh karena itu, arsitektur sistem harus mengadopsi mekanisme penanganan beban seperti caching data referensi dan antrean proses (message queue) untuk menjaga stabilitas respons sistem.

## 2. ASR 2: Integritas Data dan Rekam Jejak Audit (Integrity & Auditability)
* **Pernyataan Kebutuhan:** Setiap aktivitas penting—seperti pengunggahan tugas oleh mahasiswa, penetapan tenggat waktu oleh dosen, hasil pemeriksaan kemiripan (similarity check), hingga penginputan nilai akhir—wajib terekam secara permanen, aman, dan tidak dapat dimanipulasi (tamper-proof audit trail).
* **Alasan Pengaruh pada Arsitektur:** Aspek integritas akademik di lingkungan FIKOM UMI menuntut tingkat keandalan data yang tinggi. Hal ini memaksa perancang arsitektur untuk menetapkan batasan transaksi basis data (ACID transactions) yang ketat serta memisahkan lapisan pencatatan log aktivitas (audit logging service) dari logika bisnis utama agar setiap perubahan status penilaian memiliki jejak digital yang jelas.

## 3. ASR 3: Keamanan dan Otorisasi Akses Berkas Sensitif (Security & Confidentiality)
* **Pernyataan Kebutuhan:** Berkas tugas, laporan praktikum, serta hasil penilaian mahasiswa bersifat rahasia dan hanya dapat diakses oleh mahasiswa bersangkutan serta dosen pengampu mata kuliah terkait.
* **Alasan Pengaruh pada Arsitektur:** Kebutuhan kerahasiaan data menuntut implementasi protokol otentikasi yang aman berbasis JSON Web Token (JWT) serta sistem kontrol akses berbasis peran (Role-Based Access Control / RBAC). Arsitektur penyimpanan file (Object Storage) juga harus dilindungi dengan tautan terenkripsi (secure signed URLs) guna mencegah akses unduh tanpa izin dari pihak luar.
