# ADR-[001]: Penggunaan Cloud Object Storage untuk Pengelolaan Berkas Tugas dan Penilaian

<!-- Salin berkas ini menjadi ADR-001-judul-singkat.md, ADR-002-... dan seterusnya. -->

- **Status:** Diusulkan / Diterima / Digantikan oleh ADR-[nomor]
- **Tanggal:** [30-10-2026]
- **Pengambil keputusan:** [Tim Pengembang SPADA UMI-Kalam (FIKOM UMI)]

## Context
Lonjakan pengunduhan dan pengunggahan berkas tugas mahasiswa (seperti laporan praktikum, dokumen tugas besar, hingga lembar pengesahan berukuran besar hingga 25 MB) secara bersamaan menjelang batas waktu (deadline) berpotensi menyebabkan bottleneck pada server lokal dan memberatkan basis data relasional pusat. Hal ini berkaitan langsung dengan karakteristik ASR 1 (Performance Efficiency) dan ASR 6 (Scalability) untuk memastikan kestabilan sistem bagi 500 pengguna simultan di lingkungan FIKOM UMI.

## Decision
Kami akan menggunakan layanan Cloud Object Storage terpusat yang terisolasi khusus untuk menampung seluruh berkas digital tugas dan penilaian mahasiswa, serta diintegrasikan dengan sistem backend SPADA melalui Secure Signed URLs.

## Consequences
**Dampak Positif (Untung):** Kapasitas penyimpanan server utama menjadi jauh lebih aman dan skalabel, tidak mudah penuh, serta performa basis data relasional tetap terjaga tanpa mengalami kelambatan (latency) saat masa pengumpulan tugas massal.

**Dampak Negatif (Rugi / Trade-off):** Memerlukan konfigurasi tambahan yang aman pada jaringan, manajemen token akses yang ketat, serta pemantauan biaya layanan penyimpanan awan secara berkala.

## Compliance
Keputusan ini dipastikan dipatuhi melalui peninjauan kode pada modul unggah berkas, pengujian fungsionalitas pengunduhan aman, serta uji beban (*load testing*) secara berkala sebelum masa pengumpulan tugas akhir semester dimulai.

