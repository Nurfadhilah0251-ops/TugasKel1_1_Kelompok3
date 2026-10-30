# B1. Identifikasi dan Klasifikasi Karakteristik

<!-- Penanggung jawab: [ST. Nabila Azira Zamzani A] -->

Berikut adalah daftar kandidat karakteristik arsitektur untuk Layanan Tugas Akhir pada subsistem *Assignment & Assessment*, diklasifikasikan berdasarkan kategori, sifat, serta penentuan 3 karakteristik pendorong utama:

## 1. Daftar Kandidat Karakteristik Arsitektur

| No | Karakteristik Arsitektur | Kategori | Sifat | Alasan Pemilihan |
| :--- | :--- | :--- | :--- | :--- |
| 1 | **Performance Efficiency** | Operasional | Eksplisit |Mengatasi lonjakan akses mahasiswa dan dosen saat pengumpulan tugas akhir mata kuliah atau menjelang batas waktu (deadline) agar sistem tidak mengalami kelambatan (*latency*). |
| 2 | **Security** | Lintas Sektor | Eksplisit | Melindungi dokumen draf tugas, laporan praktikum, serta kerahasiaan nilai tugas mahasiswa dari akses pihak yang tidak berwenang. |
| 3 | **Integrity & Auditability** | Lintas Sektor | Eksplisit | Menjamin jejak digital pengunggahan tugas, riwayat pengubahan nilai oleh dosen, dan laporan hasil pemeriksaan kemiripan (similarity check) valid serta tidak dapat dimanipulasi. |
| 4 | **Availability** | Operasional | Implisit | Menjaga layanan SPADA UMI-Kalam tetap dapat diakses secara andal selama masa krusial pengumpulan tugas dan ujian akhir semester. |
| 5 | **Maintainability** | Struktural | Implisit | Memudahkan penyesuaian logika bisnis, rubrik penilaian, dan integrasi modul baru jika terjadi perubahan regulasi akademik di lingkungan FIKOM UMI.|
| 6 | **Scalability** | Operasional | Implisit |Mampu menangani peningkatan volume penyimpanan berkas digital tugas mahasiswa yang terus bertambah di setiap akhir semester perkuliahan. |
| 7 | **Usability** | Lintas Sektor | Eksplisit |Memberikan kenyamanan antarmuka bagi mahasiswa dan dosen dalam proses pengunggahan berkas, pemantauan status, serta pemberian umpan balik (*feedback*). |
| 8 | **Reliability** | Operasional | Implisit | Menjamin transaksi penyimpanan berkas dan penginputan nilai tugas berhasil terekam secara konsisten tanpa adanya data yang hilang di basis data pusat. |

---

## 2. Tiga Karakteristik Pendorong Utama (Driving Characteristics)

Berdasarkan pengujian terhadap tiga ciri karakteristik arsitektur (berdampak pada struktur desain, tidak bergantung pada domain fungsional tunggal, serta sangat penting bagi keberhasilan sistem):

1. **Performance Efficiency (Operasional):**
   * *Alasan:* Kegagalan menangani beban puncak saat batas waktu (*deadline*) pengumpulan tugas akhir mata kuliah secara serentak dapat melumpuhkan alur akademik dan mengganggu proses rekapitulasi nilai mahasiswa. Karakteristik ini memaksa perancangan arsitektur menggunakan antrean pesan (*message queue*) dan caching untuk menjaga kestabilan respons server SPADA UMI-Kalam FIKOM UMI
2. **Security & Integrity (Lintas Sektor):**
   * *Alasan:* Dokumen tugas, laporan praktikum, serta nilai ujian mahasiswa merupakan produk hukum akademik yang harus terbebas dari pemalsuan, kebocoran data, serta akses tanpa otorisasi yang sah. Hal ini menuntut lapisan autentikasi berbasis token yang aman dan kontrol akses berlapis (*Role-Based Access Control*).
3. **Maintainability (Struktural):**
   * *Alasan:* Regulasi operasional dan rubrik penilaian tugas di lingkungan program studi sering kali mengalami penyesuaian aturan dari universitas atau fakultas. Oleh karena itu, struktur kode modul Assignment & Assessment harus mudah dimodifikasi (*low coupling*) tanpa merusak fungsi modul pembelajaran lainnya di dalam sistem SPADA UMI-Kalam.

