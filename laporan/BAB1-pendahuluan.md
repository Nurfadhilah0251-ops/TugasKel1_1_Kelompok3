# BAB I. Pendahuluan

## 1.1 Gambaran layanan inti
Layanan tugas pada platform SPADA UMI-Kalam di lingkungan Fakultas Ilmu Komputer Universitas Muslim Indonesia (FIKOM UMI) merupakan salah satu layanan inti di bawah subsistem *Assignment & Assessment*. Layanan ini dirancang untuk mendigitalkan dan mengoptimalkan seluruh siklus pengelolaan penugasan akademik secara daring. Ruang lingkup fungsional utama dari layanan ini mencakup:
* **Pemberian Tugas:** Fasilitas bagi dosen pengampu untuk membuat, mempublikasikan, dan menetapkan spesifikasi penugasan atau laporan praktikum kepada mahasiswa.
* **Pengumpulan Tugas:** Wadah bagi mahasiswa untuk mengunggah berkas hasil pengerjaan tugas (seperti dokumen laporan format PDF, tautan proyek, atau arsip kode `.zip`) ke dalam sistem.
* **Pengelolaan Tenggat Waktu (Deadline):** Mekanisme otomatisasi pencatatan waktu buka dan tutup pengumpulan tugas agar selaras dengan aturan akademik.
* **Pemeriksaan Kemiripan (Similarity Check):** Fitur pemindaian otomatis untuk mendeteksi tingkat plagiarisme atau kesesuaian konten antar-tugas mahasiswa guna menjaga integritas akademik.

## 1.2 Ruang lingkup (3-5 kasus penggunaan)
Untuk memperjelas batasan operasional sistem, berikut adalah 4 skenario utama (*use cases*) yang dicakup dalam perancangan arsitektur layanan tugas ini:
1. **Pembuatan dan Pengaturan Penugasan oleh Dosen:** Dosen memasukkan detail informasi tugas, bobot nilai, instruksi pengerjaan, serta menetapkan batas waktu (*deadline*) pengumpulan secara spesifik per kelas mata kuliah.
2. **Pengunggahan Berkas Tugas oleh Mahasiswa:** Mahasiswa mengakses modul penugasan, melampirkan berkas dokumen digital (dengan batasan ukuran file hingga 25 MB), dan mengirimkannya sebelum tenggat waktu berakhir.
3. **Pemindaian Kemiripan Dokumen (Similarity Check):** Sistem secara asinkron menjalankan proses pemindaian berkas yang diunggah untuk memeriksa indikasi kemiripan teks atau plagiarisme antar-mahasiswa.
4. **Penilaian dan Pemberian Umpan Balik (Feedback):** Dosen mengunduh atau memeriksa berkas tugas mahasiswa yang terkumpul, memasukkan nilai akhir beserta catatan ulasan, dan menyimpannya ke dalam sistem rekapitulasi nilai SPADA.

## 1.3 Sumber Data
Penyusunan analisis dan perancangan arsitektur perangkat lunak untuk layanan ini didasarkan pada integrasi beberapa sumber data yang valid dan sesuai dengan ketentuan akademik:
* **Pengalaman Pengguna (User Experience):** Eksplorasi langsung terhadap antarmuka platform SPADA UMI-Kalam oleh anggota kelompok selaku mahasiswa aktif untuk mencatat alur transaksi, kendala teknis harian, serta respons waktu muat sistem.
* **Informasi Publik:** Panduan resmi perguruan tinggi, regulasi akademik, serta dokumentasi teknis dari situs resmi Universitas Muslim Indonesia (`umi.ac.id`).
* **Wawancara / Survei Singkat:** Diskusi dan pengumpulan tanggapan dari minimal 5 responden (terdiri atas mahasiswa FIKOM UMI sebagai pengguna akhir serta staf/pengelola unit terkait) untuk mengetahui ekspektasi kualitas layanan.
* **Pengamatan Langsung:** Observasi kondisi operasional jaringan dan kebiasaan akses civitas akademika di lingkungan kampus UMI terutama pada masa-masa menjelang batas akhir pengumpulan tugas.
