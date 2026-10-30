# B5. Analisis Trade-off

<!-- Penanggung jawab: [Fera Julia  Halim] -->

Berikut adalah analisis dua pasang karakteristik arsitektur yang saling memengaruhi pada Layanan pengumpulan tugas (subsistem *Assignment & Assessment*), beserta keputusan prioritas dan alasannya:

## 1. Pasang Trade-off 1: Keamanan (Security) vs Kinerja (Performance Efficiency)
* **Dampak Saling Memengaruhi:**
  Penerapan autentikasi JWT berlapis, verifikasi tanda tangan digital atau pengecekan plagiarisme (similarity check) pada dokumen tugas, serta enkripsi data nilai mahasiswa meningkatkan tingkat keamanan sistem secara signifikan. Namun, proses pemindaian berkas dan pemeriksaan token akses secara terus-menerus akan menambah beban komputasi server dan memperlambat waktu respons sistem (*latency*).
* **Keputusan Prioritas & Alasan:**
  * **Keputusan:** Aspek Security didahulukan untuk modul yang menangani data nilai akhir dan penyimpanan berkas tugas, sedangkan Performance Efficiency didahulukan untuk modul antarmuka pengunggahan berkas harian mahasiswa.
  * *Alasan:* Pemalsuan nilai atau kebocoran dokumen tugas berisiko melanggar integritas akademik di lingkungan FIKOM UMI, sehingga keamanan data mutlak diutamakan. Sebaliknya, proses pengunggahan tugas harian membutuhkan respons yang cepat dan ringan agar kenyamanan mahasiswa tetap terjaga terutama saat mendekati batas waktu (*deadline*).
---

## 2. Pasang Trade-off 2: Fleksibilitas (Flexibility) vs Kemudahan Perawatan (Maintainability)
* **Dampak Saling Memengaruhi:**
 Penggunaan layanan penyimpanan terpusat (*Cloud Object Storage*) untuk menampung file tugas berukuran besar memberikan skalabilitas yang sangat baik agar server utama tidak cepat penuh. Namun, hal ini meningkatkan kompleksitas pemeliharaan karena tim pengembang harus mengelola integrasi API tambahan dan manajemen izin akses file (*signed URLs*).
* **Keputusan Prioritas & Alasan:**
  * **Keputusan:** Aspek Scalability diprioritaskan melalui pemisahan penyimpanan berkas, sementara struktur kode dibuat tetap modular untuk menjaga Maintainability.
  * *Alasan:* Lonjakan pengumpulan tugas di akhir semester pasti akan terus meningkat setiap tahunnya di SPADA UMI-Kalam, sehingga kapasitas penyimpanan harus fleksibel. Penggunaan arsitektur modular membantu tim IT mengelola kode dengan lebih rapi tanpa takut rusak saat ada pembaruan sistem.
